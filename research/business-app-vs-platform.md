# The Business app is not the platform

## The problem

"WhatsApp Business" is three products, and only one of them can take a webhook. The free app is what people already know. The scraper we have reads an account in one direction and cannot answer. The later bot has to answer. If the app cannot call our system, it does not matter that it is free.

## What we'd do

Use the **WhatsApp Business Platform** (Cloud API), either direct or through a provider that is only a skin on that API. Do not use the WhatsApp Business app. Do not use Meta Business Agent for the conversation. Prompts stay in our process, which reads the webhook and decides the next line.

## How this is better, and worse

Better: a URL we register receives the citizen's message, and a send API answers it. The same webhook carries a stable sender id (`wa_id` / `from`) and a message id, so continuity is a row we store, not a feature we buy. Photos arrive as a media id. We pull the file when the webhook lands.

Worse: the app is free and the platform is not. Business verification and a display name are ours, or a provider's. The marketing site still describes the old conversation pricing, so anyone quoting from the FAQ will quote the wrong model. The rate card is the one to use. See [send-vs-receive-pricing.md](send-vs-receive-pricing.md).

## Compared with the app, and with Meta's assistant

Meta's own FAQ: the app is one phone, free to download, limited customisation, limited connection to other tools. The platform is programmatic access, media, buttons, and a bill. There is no place on the app to register a webhook URL. That is why a scraper exists, and why a scraper cannot become the bot.

The FAQ also still says businesses pay per conversation, with the first 1,000 conversations a month free. Meta's developer pricing page, read the same day, bills per delivered message, and the 1,000-free allowance is service messages. When those two disagree, the pricing page wins.

Meta Business Agent is a fifth category on the rate card, billed in tokens, not at the India message rates. It would run the chat on Meta's side. That is the product already rejected: harder to shape, smaller context than a model we run ourselves. A provider's "AI agent" add-on is the same decision again. It is not in this comparison.

## Cost

The app is ₹0 and cannot do the job. The platform's India rates, and what a complaint costs, are in [send-vs-receive-pricing.md](send-vs-receive-pricing.md). Meta Business Agent's token price is irrelevant once we are not using it.

## What the later bot changes

Nothing about this split. The bot needs the webhook whether the question is "what is your name" or "send a photo of the drain". The app still will not call us. Continuity is still our record of `wa_id`, which the platform already puts on every inbound message.

## Sources (accessed 2026-10-23)

- Differences between the WhatsApp Business Platform and the app — https://www.facebook.com/business/help/338665938087159
- WhatsApp for Business FAQ (app vs platform; this page still describes per-conversation pricing) — https://business.whatsapp.com/resources/faq
- Webhooks setup (received messages vs status) — https://developers.facebook.com/docs/whatsapp/cloud-api/guides/set-up-webhooks/
- Webhooks overview — https://developers.facebook.com/documentation/business-messaging/whatsapp/webhooks/overview
- Incoming text payload, including `from`, `id`, `wa_id` — https://developers.facebook.com/docs/whatsapp/cloud-api/webhooks/payload-examples/
- Media: webhook media ids last 7 days, download URL about 5 minutes — https://developers.facebook.com/docs/whatsapp/cloud-api/reference/media/
- Location as a message type (send API, latitude and longitude; docs updated 21 May 2026) — https://developers.facebook.com/docs/whatsapp/cloud-api/messages/location-messages/
- Pricing page, for the contradiction with the FAQ — https://developers.facebook.com/docs/whatsapp/pricing/

**Unknown:** I read the send API for location, and the text webhook. I did not get an incoming location example to load. One live pin against a test number, later, before anyone promises the bot can take a map pin. It does not change the provider choice. Every API option here is a skin on this webhook.
