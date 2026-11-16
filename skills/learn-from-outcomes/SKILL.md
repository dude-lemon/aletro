---
name: learn-from-outcomes
description: Record won and lost deals in Aletro and turn them into lessons that shape the next search. Use when the user reports a win, a loss, a meeting or a dead end, or asks what is working, which leads convert, or how to improve targeting.
---

# Learn from outcomes

## Record what happened

When the user reports an outcome, call `set_company_status` with the new status (`meeting`, `won`, `lost` or `dismissed`) and a note on why, in their words. The reason is what makes a lesson possible later.

## Turn outcomes into lessons

1. `get_learnings` for the product. It returns the rules the user wrote, the lessons saved so far, the companies marked won or lost with how they scored, and the lead quality feedback the user gave on each company (good fit, wrong industry, too large and so on).
2. With at least a few outcomes or feedback, compare won with lost and good fit with bad: industry, size, region, the kind of buying signal, how recent it was, who you reached, and the reasons in the notes.
3. Write one to five lessons that would change a search, each one sentence and specific, for example:
   - "Clinics with a single site rarely buy; target groups with two or more."
   - "Job posts for a practice manager convert better than funding news."
   Leave out anything a single case suggests; say it needs more data instead.
4. Save each lesson with `save_learning`, with a short `title` and a `category`: targeting, exclusions, signals, buyers, messaging, pricing or general. The `find-buyers` skill reads them at the start of every run.
5. If a lesson shows the ideal customer itself is off (a new exclusion, a size band), suggest the change and, if the user agrees, update it with `save_product`.

## Tell the user

Give the lessons in plain words, how many outcomes they rest on, and what the next search will do differently.
