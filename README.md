# WhatsApp two-way providers for a later complaint bot

This repository is a research pack for evaluating WhatsApp provider options for a future citizen-complaint bot in India. The core question is not the bot itself; it is the communication pipe:

- Can the provider receive a citizen's WhatsApp message on a webhook?
- Can it send a reply back?
- What does each direction cost?
- Is the free WhatsApp Business app enough, or is a platform/API required?

The work in this repo compares provider capabilities, pricing, and operational trade-offs before any bot or workflow is built.

## Why this repo exists

The project is focused on the plumbing required for a two-way WhatsApp channel for a complaint workflow:

- inbound messages from citizens
- outbound replies and status updates
- message categorization and template rules
- webhook-driven integration with an internal system

The research assumes a later complaint bot will need to handle photos, location data, continuity across chat turns, and back-office integration, not just a simple broadcast.

## Repository layout

- `NOTES.md` — working notes and pricing calculations used during the research
- `research/README.md` — reading guide and project assumptions
- `research/SYNTHESIS.md` — concise decision summary and verdict
- `research/business-app-vs-platform.md` — comparison of WhatsApp Business app vs platform/API
- `research/send-vs-receive-pricing.md` — send-vs-receive pricing analysis under Meta's India rate card
- `research/providers.md` — comparison of Cloud API direct, 360dialog, Twilio, Gupshup, AiSensy, Wati, and Interakt
- `research/what-the-pipe-must-carry.md` — what the communication layer must support for the later bot

## Key findings

The research concludes that the strongest option for this use case is the WhatsApp Cloud API direct, rather than the Business app or a managed inbox platform, unless there is a specific operational reason to use a partner.

Main conclusions from the research:

- The WhatsApp Business app is not sufficient for a webhook-driven bot.
- Meta bills outbound sends, while inbound customer messages are free.
- In India, Meta's list price for utility and service messaging is approximately ₹0.115 per message (effective from the 1 October 2026 rate card in the research notes).
- Meta's own rate card includes a free tier for service messages on a number, which changes the effective cost for certain message mixes.
- A provider that charges on the receive as well as the send adds cost without necessarily improving the bot capability.

## Recommended reading order

If you want the short path, start here:

1. `research/README.md`
2. `research/SYNTHESIS.md`
3. `research/send-vs-receive-pricing.md`
4. `research/providers.md`

## Scope and assumptions

This repository focuses on the communication layer, not the complaint application itself.

Assumptions documented in the research:

- Scope is the WhatsApp pipe, not the bot logic or complaint workflow.
- Two-way communication is required: receive on a webhook and send replies.
- AI and prompts remain under our control rather than Meta Business Agent or vendor-owned chatbots.
- Rates are modeled for India and compare public list pricing as of the research date.
- One number and a practical city-scale message volume are assumed for cost comparisons.

## Notes on data and sources

The research is based on public pricing pages and documented rate cards from Meta and several WhatsApp providers, with the source references recorded in the research files.

This repo intentionally does not claim to be a production implementation; it is a decision-support pack and a pricing analysis.

## License

This repository does not currently include a license file. If you plan to reuse the content, confirm the ownership and licensing terms before publication or redistribution.

## Summary

This repo answers a single question early and deliberately: what WhatsApp channel can we actually use to receive citizen messages and send back replies, without locking the future bot into the wrong platform? The answer in the research is to prefer the direct Cloud API path unless a platform-specific operational constraint makes a provider partner necessary.