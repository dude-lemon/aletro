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

## Searching

Work signal first: look for the product's buying signals, then check whether the company behind each one fits. Searching by industry alone finds companies that fit but are not buying.

- Turn each buying signal into a few concrete searches for the region, for example job posts naming the role, news of a new site or funding, a new regulation's deadline, tenders, or reviews complaining about the problem.
- Prefer primary sources: the company's own site, its careers page, official registries and tender portals, and reputable local or trade news.
- Open the pages you cite. A claim goes into Aletro only if a page you read says it.
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
- Add the decision makers you can see on public pages (team page, press releases, conference speaker pages): name, title exactly as published, the page you found it on, and a public profile link if there is one. Never look for or record personal email addresses or phone numbers.

## Saving

- Call `save_company` once per company, as you go, so nothing is lost if the run stops.
- If Aletro refuses a company, read why, fix what you can (usually the domain or a source link) and try once more; otherwise move on.
- If it saves with a `flag_reason`, keep it and tell the user why it ranks lower.

## Finishing

1. Call `get_pipeline` so the list shows in the chat.
2. Give a short summary: how many you checked, how many you saved, the three strongest with one line each on why now, and any pattern worth knowing.
3. Offer next steps: research the top companies in depth (`research-company`) or draft outreach (`draft-outreach`).

## Keep in mind

- Quality over count. Ten well-sourced companies beat thirty thin ones.
- Each run uses the user's own Claude usage. For a large request, work in batches of 10 to 20 and check in between.
- Never present a guess as a fact. When something is uncertain, say so in the claim and mark it `low` confidence.
