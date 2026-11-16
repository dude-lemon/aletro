---
name: find-buyers
description: Find companies that are likely to buy what the user sells, with the sourced buying signals behind each, and save them to the Aletro pipeline. Use when the user asks for leads, prospects, target accounts, companies to contact, "who should I sell to", or "find buyers".
---

# Find companies ready to buy

You research the open web, check each company against the product's ideal customer, score it, and save it to Aletro. The user's pipeline then shows them in Claude (`get_pipeline`) and on aletro.dudelemon.cloud.

## Before searching

1. `list_products`. With no product saved, run the `setup` skill first. With several, ask which one, unless the user named it.
2. `get_learnings` for that product. Apply every lesson to this run, and mention the ones that changed what you looked for.
3. `list_known_domains`. Skip companies already saved unless the user asked to refresh them.
4. Agree the scope in one line: region, how many companies (default 15), and any focus the user gave.
5. `start_run` with that scope as the brief, and keep the `run_id` for every `save_company` in this search.

## Searching

Work signal first: look for the product's buying signals, then check whether the company behind each one fits. Searching by industry alone finds companies that fit but are not buying.

- Turn each buying signal into a few concrete searches for the region, for example job posts naming the role, news of a new site or funding, a new regulation's deadline, tenders, or reviews complaining about the problem.
- Prefer primary sources: the company's own site, its careers page, official registries and tender portals, and reputable local or trade news.
- Open the pages you cite. A claim goes into Aletro only if a page you read says it, and then it is saved with `verified: true`. A claim you only saw in a search snippet is `verified: false`.
- Give every signal a `signal_type`: hiring, expansion, funding, leadership, launch, tech_change, partnership, event, regulation, complaint or other.
- When a source is a news site or a directory, the company is the one the article is about, never the publisher.

## Checking each company

Keep a company only when all of these hold:

- It is a real company with its own website. Use its root domain (acme.com, not blog.acme.com or a jobs board).
- It matches the ideal customer closely enough to score 40 or more on fit.
- It does not match the product's exclusions, and it is not a competitor.
- You have at least one buying signal with a source link, ideally from the last six months.

Note risks you find (a recent contract with a competitor, layoffs, a hiring freeze) as `risk` evidence instead of leaving them out.

## Scoring and people

- Score fit and intent with the `score-companies` guide.
- Add the decision makers you can see on public pages (team page, press releases, conference speaker pages): name, title exactly as published, the page you found it on, and a public profile link if there is one. Give each a `persona`: economic_buyer, department_owner, user or technical_evaluator. Never look for or record personal email addresses or phone numbers.
- Write the `brief`: a one-line `headline`, the `likely_pain`, the `outreach_angle`, the `best_buyer`, the `approach`, three to five `talking_points`, and `what_could_be_wrong` (the honest case against it).
- Add `platform` and `tech` when the site or job posts show the tools they use.

## Saving

- Call `save_company` once per company, as you go, so nothing is lost if the run stops.
- If Aletro refuses a company, read why, fix what you can (usually the domain or a source link) and try once more; otherwise move on.
- If it saves with a `flag_reason`, keep it and tell the user why it ranks lower.

## Finishing

1. `finish_run` with how many companies you looked at, how many you saved, and why you turned the rest down, as reasons with counts (for example "No buying signal with a source", 12).
2. Call `get_pipeline` so the list shows in the chat.
3. Give a short summary: how many you checked, how many you saved, the three strongest with one line each on why now, and any pattern worth knowing.
4. Offer next steps: research the top companies in depth (`research-company`) or draft outreach (`draft-outreach`).

## Keep in mind

- Quality over count. Ten well-sourced companies beat thirty thin ones.
- Each run uses the user's own Claude usage. For a large request, work in batches of 10 to 20 and check in between.
- Never present a guess as a fact. When something is uncertain, say so in the claim and mark it `low` confidence.
