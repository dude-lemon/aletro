# Aletro

Aletro is free B2B prospecting that works inside Claude. Claude finds companies showing real buying signals for what you sell, checks each one against your ideal customer, maps who decides there, and drafts outreach. Aletro keeps it all in a pipeline you can open in Claude or at [aletro.dudelemon.cloud](https://aletro.dudelemon.cloud). Every claim carries its source, date and confidence, so you can see why a company made the list.

## How it works

- **Claude does the research** on your own Claude plan, using its web search. Aletro runs no AI of its own and never asks you for API keys.
- **Aletro checks and keeps the results.** When Claude saves a company, Aletro refuses it without a sourced claim or a real company domain, holds the score down when the proof is thin or old, and pushes down media outlets, competitors and companies far too large for your deal size.
- **You stay in control.** Aletro never sends email or messages. Outreach is saved as drafts that you send yourself.

## Get started

1. Install the plugin. In Claude Code, run `/plugin marketplace add dude-lemon/aletro`, then `/plugin install aletro@aletro`. It connects Claude to the Aletro connector at `https://aletro.dudelemon.cloud/mcp`.
2. When Claude asks you to connect, sign in with your email and the code we send you, then click Allow. A free account is created the first time.
3. Ask Claude: "Set up Aletro for my product", then "Find companies that are ready to buy".

Without the plugin, you can add the connector yourself in Claude under Settings, Connectors, Add custom connector, with the address above.

## What is inside

Skills:

| Skill | What it does |
| --- | --- |
| `setup` | Saves what you sell, who buys it, the signals that show a company may buy now, and what to exclude |
| `find-buyers` | Searches for companies showing those signals, checks and scores them, and saves them |
| `score-companies` | The scoring guide for fit and buying intent, and what Aletro does with the scores |
| `research-company` | Builds an in-depth brief on one company and maps who decides there |
| `draft-outreach` | Writes a short outreach sequence grounded in the saved evidence |
| `learn-from-outcomes` | Records wins and losses and turns them into lessons for the next search |

Connector tools (on `aletro.dudelemon.cloud`): `list_products`, `save_product`, `list_known_domains`, `start_run`, `save_company`, `finish_run`, `get_pipeline` (also shows the pipeline inside Claude), `get_company`, `set_company_status`, `add_note`, `save_draft`, `get_learnings`, `save_learning`.

## What is sent to Aletro

The plugin contains only instructions and the connector address; it runs no code on your computer. Through the connector, Claude sends Aletro what you ask it to keep: your product settings, the searches it ran, the companies it researched with their evidence and source links, people's names, job titles and public profile links, outreach drafts, notes and lessons. Your sign-in email is used to create your account and send sign-in codes. Nothing else from your conversations is sent.

## Privacy policy

Aletro is a Dude Lemon product and is covered by the [Dude Lemon privacy policy](https://dudelemon.com/privacy). In short:

- **What we collect**: your email address, and the data Claude saves to your Aletro account as listed above.
- **How we use it**: only to run your Aletro account: to show your pipeline and to let Claude read and update it. We do not sell it or use it for advertising.
- **Where it is stored**: in Aletro's own database on our servers.
- **Sharing**: only with the service providers that run Aletro (hosting on AWS and email delivery for sign-in codes).
- **How long we keep it**: until you delete it. Delete your account from Settings at aletro.dudelemon.cloud and everything in it is removed, and Claude's access ends.
- **Contact**: [dudelemon.com/contact](https://dudelemon.com/contact).

## Support

Questions or problems: [dudelemon.com/contact](https://dudelemon.com/contact).

## License

MIT. See [LICENSE](LICENSE).
