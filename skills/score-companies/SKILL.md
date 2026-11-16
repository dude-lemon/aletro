---
name: score-companies
description: How Aletro scores a company's fit and buying intent. Use whenever you give a company a fit_score or intent_score for save_company, or when the user asks why a company scored as it did or wants companies re-scored.
---

# Scoring a company

Every company saved with `save_company` gets two scores from you, each 0 to 100. Aletro shows 60% fit plus 40% intent, then holds the result down in code when the proof is thin or the company looks off target. Score honestly: a padded score gets capped anyway and makes the list worse.

## Fit score: how well it matches the ideal customer

Check the saved product (`list_products`) and add points for each match you can show from a source:

| Fit | Meaning |
| --- | --- |
| 85 to 100 | Matches the industry, size and region, and the deciding role clearly exists there |
| 65 to 84 | Matches on industry and size; region or buyer role less certain |
| 40 to 64 | Partly matches; one important part (size, region, industry) is off or unknown |
| 0 to 39 | Weak match; include only if the buying signal is unusually strong |

Lower the fit when the company would struggle to buy at the product's deal size, or when it sells the same thing the product does.

## Intent score: how strong and recent the buying signals are

| Intent | Meaning |
| --- | --- |
| 80 to 100 | Two or more of the product's buying signals, at least one in the last 90 days, from the company's own pages or reputable news |
| 60 to 79 | One clear buying signal from the last six months |
| 40 to 59 | A signal older than six months, or one that is indirect |
| 0 to 39 | No real signal, only fit |

Add up to 10 when you found a named decision maker, since the company can actually be reached.

## Evidence for save_company

Each claim is one item with:

- `kind`: `signal` shows buying now, `fit` shows the match, `risk` argues against (include risks; they help the user decide)
- `claim`: one factual sentence, in your words
- `source_url`: the page you actually opened that says it. Never a search results page, never a guessed URL
- `source_date`: when the source was published, if the page shows it
- `confidence`: `high` when the company's own page or a reputable outlet states it directly; `medium` when it is stated but secondhand or slightly dated; `low` when it is inferred

## What Aletro does after you save

- Refuses a company with no claim that has a usable source link, a subdomain instead of the company's own domain, or a blog or jobs site as the company.
- Caps the score when there is no buying signal, no strong one, or the newest signal is over a year old.
- Pushes down news and media outlets, competitors, software vendors (for service products), very large companies (for small deals) and anything matching the product's exclusions.
- Tells you why in `flag_reason`. Pass that on to the user rather than arguing with it; if the rule is wrong for this product, suggest changing the product's settings with `save_product`.
