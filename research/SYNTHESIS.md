# Synthesis — WhatsApp two-way providers for a later complaint bot

*Backed by the notes in this folder. Prices are public list prices, India, accessed 2026-10-23. Dollar and euro conversions are named in [providers.md](providers.md) and are not invoice rates.*

## The problem

Illias asked for a provider that can **receive on a webhook and send a reply**, compared on price, on whether send and receive cost the same, and against the WhatsApp Business app. The complaint bot comes after. It will ask for a photo, a location and a name, ask different follow-ups for waste, a broken pipeline or a dead animal, and create the complaint at the end. Prompts stay in-house. Meta's assistant was already rejected. The scraper we have only reads one way, so it is not a candidate.

## The verdict

Use the **Cloud API direct**. Receive is free. Send, for the mix used in this pack, is Meta's India rate of **₹0.115** for a service reply and for a utility template. One number, no subscription:

| Complaints / month | Meta only |
|---|---|
| 1,000 | **₹345** |
| 5,000 | **₹2,185** |
| 10,000 | **₹4,485** |

That is 4 sends per complaint (2 replies, 2 utility templates), minus the first 1,000 free service messages on the number. The citizen's messages, including a photo or a pin, are not in it. Full arithmetic in [send-vs-receive-pricing.md](send-vs-receive-pricing.md).

If we do not want to hold Meta verification ourselves, **360dialog Regular at €49 per number per month**, Meta's fees passed through, no receive fee found. At 1,000 complaints that license is the bill, not the messages.

Do not use the WhatsApp Business app. It cannot call a webhook. Do not use Twilio unless we are already paying them: they charge **$0.005 on the receive as well as the send**. Do not use Wati's Growth plan: no webhooks. Leave AiSensy and Interakt unless someone specifically wants their inbox. They cost a subscription plus a higher send rate, and their AI add-ons are the design we turned down. Gupshup's utility fee is **unknown** on a public page.

## The questions, in one line each

1. **App or platform?** The app is free and one device. The platform is the webhook. Only the platform. → [business-app-vs-platform.md](business-app-vs-platform.md)
2. **What is 0.115?** Meta's India list rate, in rupees, for utility, authentication and service, effective 1 October 2026. Marketing is ₹0.8631. The ₹1,000 guess for 1,000 complaints does not come out of this mix. It is high. → [send-vs-receive-pricing.md](send-vs-receive-pricing.md)
3. **Send versus receive?** Meta bills the send only. The receive is free. Twilio bills both. The inbox products bill a subscription and a marked-up send, and say the receive is free. → [providers.md](providers.md)
4. **Can the pipe hold the later bot?** Text, a photo and a sender id, yes, on the Cloud API. Continuity is our record of that sender id, not a provider feature. Location as an inbound pin still wants one live test. Hindi transcription is not a WhatsApp charge. → [what-the-pipe-must-carry.md](what-the-pipe-must-carry.md)
5. **Who runs the prompts?** We do. Meta Business Agent, and the providers' agents, are out.

## What would change the choice

Template category, not the vendor. Two marketing templates instead of two utility templates takes 1,000 complaints from ₹345 to about **₹1,841**, and 10,000 from ₹4,485 to about **₹19,400**. Write the status texts so they stay utility, and submit one early enough to see how Meta classifies it.

The other change is operational, not a rate. If nobody here should own the Business Manager, pay 360dialog's €49 and keep the same message rates. That is a license, not a cheaper message.

## What this pass did not do

No Meta app was created, no message sent, no webhook server stood up, no prompt written. Still open before a number goes into a proposal: GST, Gupshup's fee if anyone still wants a quote, Wati's unpublished rate card, whether Interakt really does not charge service messages, one real inbound location pin, and whose name is the second admin on the Business Manager.

## Sources

Repeated at the bottom of each file. The rate card is https://developers.facebook.com/docs/whatsapp/pricing/. The app-versus-platform split is https://business.whatsapp.com/resources/faq and https://www.facebook.com/business/help/338665938087159. Provider pages are listed in [providers.md](providers.md).
