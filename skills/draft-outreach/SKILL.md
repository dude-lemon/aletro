---
name: draft-outreach
description: Draft a short outreach sequence for a saved company or person, grounded in the evidence Aletro holds, and save the drafts to Aletro. Use when the user asks to write an email, LinkedIn message, follow-ups, or a call opener for a prospect.
---

# Draft outreach

Aletro never sends anything. You write the drafts, save them with `save_draft`, and the user sends them from their own mailbox or account.

## Steps

1. `get_company` to read the evidence, people and any notes. Pick the person to write to (the champion first, unless the user says otherwise). If no one is saved, write to the role and say so.
2. Ask, only if you cannot tell: the user's name and sign-off, and anything the offer must or must not say.
3. Write a three step sequence unless the user wants something else:
   - **Step 1**: open with the specific signal (the new site, the job post, the deadline), link it to the problem the product solves, and make one small ask.
   - **Step 2**, about four days later: a short follow-up adding one useful point, such as a relevant result or an idea for their situation.
   - **Step 3**, about a week later: a brief, polite close that leaves the door open.
4. Save each step with `save_draft` (company, person, step, channel, subject, a few words on the `angle`, and the body). Use the company's brief (outreach angle, talking points, best buyer) when it has one.
5. Show the drafts to the user. They can copy them from the chat or from the company's page in Aletro.

## Writing rules

- Use only facts from the saved evidence. Never invent results, mutual contacts or familiarity.
- Short: under 120 words for an email, under 60 for a LinkedIn message.
- One ask per message. Plain language, no hype, no false urgency.
- Match the recipient's language and local tone.
- If the user has an email connector and asks for it, you may also create the drafts there for them to review. Never send on their behalf.

## After sending

When the user says a message went out or got a reply, record it with `set_company_status` (contacted, meeting) and a note, so the pipeline stays true.
