# WhatsApp two-way providers, for a later complaint bot

Illias asked Mohammed Shafi A to compare providers that can **send and receive** on WhatsApp, before anyone builds the complaint bot. The bot itself is later: it will chat, ask for a photo, a location and a name, categorise (waste, a broken pipeline, a dead animal), and only then create the complaint. Prompts stay in-house. Meta's own assistant was already turned down.

This pack answers the question that has to be settled first:

**Which pipe can receive a citizen's message on a webhook and send a reply, what does each direction cost, and is the free WhatsApp Business app enough?**

Each file is written as: **the problem → what we'd do → how it's better (and worse) → comparison → cost → what the later bot changes → sources**.

## Reading order

| File | Question it answers |
|---|---|
| [business-app-vs-platform.md](business-app-vs-platform.md) | The Business app, the Platform, and Meta's assistant. Which of those can actually call us? |
| [send-vs-receive-pricing.md](send-vs-receive-pricing.md) | Meta's India card after 1 October 2026. What a send costs, what a receive costs, and the monthly bill |
| [providers.md](providers.md) | Cloud API, 360dialog, Twilio, Gupshup, AiSensy, Wati, Interakt. Webhook or not, and who charges for the receive |
| [what-the-pipe-must-carry.md](what-the-pipe-must-carry.md) | Photos, location, a name, and chat continuity. Not the bot. Just whether the pipe can hold them |
| [SYNTHESIS.md](SYNTHESIS.md) | The whole story on one page. Read this first if you read only one |

The scratch from the pages is [NOTES.md](../NOTES.md), one level up. It is not a second copy of these files.

## Assumptions

- **Scope is the pipe.** No bot, no prompts, no webhook service, no complaint workflow.
- **Two-way is the requirement.** Receive via webhook, send a reply. The existing scraper only reads one way, so it is out.
- **AI stays ours.** Meta Business Agent, and the providers' own chatbots, are not candidates for the prompts.
- **Country is India.** Rates are Meta's INR list effective 1 October 2026. Where a provider bills in dollars or euros, the conversion is named and dated. It is not a rate they will invoice at.
- **One number, one city.** Moradabad-scale volumes used for the sums: 1,000, 5,000 and 10,000 complaints a month.

## Sources and calculations

- Every material claim carries a source (title + URL, accessed 2026-10-23). Meta's own docs and each provider's own pricing page first. A news write-up is labeled as that. Anything not on a page we opened is **unknown**, not guessed.
- Prices are public list prices. No account was opened, no message was sent.
- The complaint mix used everywhere is the same: **4 messages we send** (2 ordinary replies, 2 utility templates) and the citizen's messages on top, which Meta does not bill. The arithmetic sits next to the number.
- One figure in the pack is a conversion, not a list price: $ and € turned into rupees at 94.78 (The Hindu, early trade 23 October) and 106.2839 (RBI reference archived for 21 October). Flagged wherever it appears.
