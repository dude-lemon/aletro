---
name: research-company
description: Research one saved company in depth: confirm its buying signals, add evidence and risks, and map the people who decide, then save it all to Aletro. Use when the user asks to dig into a company, build a dossier or account brief, or find who to contact there.
---

# Research a company in depth

## Steps

1. Find the company: `get_pipeline` (search by name) or `get_company` if you have its id. Read what is already saved so you add to it instead of repeating it.
2. Confirm the buying signals already saved still hold. Look for newer ones, and for risks.
3. Fill in what the company is: what it sells, size, locations, recent news, the tools or suppliers it uses that matter to the product.
4. Map the buying committee from public pages only:
   - **Decides**: the person who signs off (owner, director, head of the function).
   - **Champions**: the person who feels the problem day to day.
   - **Influences or blocks**: finance, IT or procurement, when the purchase touches them.
   For each person: name, title exactly as published, where you found it, a public profile link if there is one, and one line on why they matter. Never look for or record personal email addresses or phone numbers.
5. Re-score with the `score-companies` guide, then call `save_company` with the same domain. It adds the new evidence and people to what is there and keeps the company's status.
6. Write a short brief and save it with `add_note`: why now, who to approach first and why, the angle that fits their situation, and the main risk.
7. If the company is clearly worth pursuing, ask the user whether to move it to `qualified` with `set_company_status`.

## Then

Show the user the brief, and offer to draft outreach (`draft-outreach`).
