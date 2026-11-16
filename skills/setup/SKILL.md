---
name: setup
description: Set up Aletro for something the user sells, or change it. Use when the user wants to start prospecting, says what they sell, asks Aletro to "set up" or "update my ideal customer", or when another Aletro skill finds no saved product.
---

# Set up a product in Aletro

Aletro keeps, for each product the user sells, who buys it and what shows a company may buy now. Every search and score reads this, so a few good answers here make every later run better.

## Steps

1. Call `list_products`. If the product is already saved, show what is saved and ask what to change. Otherwise continue.
2. If the user gives a website, read it first and draft the answers yourself, then ask the user to correct them. Ask only for what you could not work out.
3. Settle these, in plain words:
   - **What it is**: two or three sentences on what it does and the problem it solves.
   - **Typical deal size** in US dollars, roughly. It keeps giant companies from crowding a small-ticket list.
   - **Is it a service** (consulting, an agency, a managed service)? If so, other firms that sell the same service are competitors, not buyers.
   - **Who buys**: industries, company sizes, countries or regions.
   - **Who decides**: the job titles that sign off or champion it.
   - **Buying signals**: events that show a company may buy soon. Suggest some that fit the product and let the user pick. Good signals are specific and visible on the open web, for example:
     - hiring for a role the product replaces or supports
     - opening a new site, branch or market
     - a funding round, acquisition or new leadership in the buying team
     - a new rule or deadline that forces a change
     - public complaints or reviews about the problem the product solves
     - a tender or request for proposals
     - switching or outgrowing a tool the product replaces
   - **Exclusions**: kinds of company never to include, such as existing customers, competitors, or segments that never buy.
4. Call `save_product` with the answers (pass `product_id` when updating).
5. Read back a short summary and offer the next step: finding companies (the `find-buyers` skill).

## Notes

- Keep lists short and concrete. Five sharp buying signals beat twenty vague ones.
- A user can have several products. Each has its own pipeline.
