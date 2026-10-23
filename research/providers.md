# Who can do two-way, and what they add to Meta's price

## The problem

Meta's card is the floor. [send-vs-receive-pricing.md](send-vs-receive-pricing.md) puts a complaint at ₹345–₹4,485 a month depending on volume, receive included at zero. Providers sell access to that same pipe. Some charge a subscription, some add a per-message fee, and one of them charges for the receive, which Meta does not. A provider that cannot hand us a webhook has already failed, however cheap the send looks.

## What we'd do

Call the Cloud API ourselves, and pay Meta only. Use a provider only if we do not want to hold business verification. The test for that provider is: inbound webhook (including a photo), send from our process, Meta's rates passed through, no fee on the receive.

Rupee conversions below are not invoice rates. Dollar figures use 94.78, The Hindu, early trade 23 October 2026. Euro uses the RBI reference archived for 21 October, 106.2839.

## Cloud API, direct

Receive: webhook, no Meta fee. Send: the card in the pricing note. No monthly rent on that card.

This is the pipe. Advantage is that nothing sits on top of ₹0.115, and the webhook is not a plan feature we can accidentally not buy. Disadvantage is that verification, the display name, and the Business Manager are ours. More than one admin, or the number leaves with one person.

## 360dialog

Receive: they forward Meta's webhooks. No per-receive fee found. Send: Meta's card, passed through. Marketing on the ordinary messages endpoint instead of the marketing API picks up 7%. This bot should not send marketing, so that 7% should not apply.

The price is the license. Regular is **€49 per number per month**, about ₹5,200 before a complaint. Premium is €99, and it is the plan that claims verification in 48 hours. That sentence is theirs, not Meta's.

An older partner page still says session messages are free. The current client pricing page bills service messages. Budget Meta's service rate, not the old sentence.

Advantage: an API, not an inbox, if we want them to hold the Meta relationship. Disadvantage: at 1,000 complaints the license is an order of magnitude above Meta's message bill (₹5,200 against ₹345).

## Twilio

Their fee is **$0.005 per message, inbound and outbound**, on top of Meta, page dated September 2026. A failed message is another $0.001. They are the provider who charges for the receive.

$0.005 is about ₹0.47. At 1,000 complaints, counting two inbound as well as our four outbound: 6,000 × $0.005 = $30, about ₹2,840, plus Meta's ₹345. At 10,000 complaints, about ₹28,400 plus Meta's ₹4,485.

The top of their page agrees utility inside the window is now charged. An example further down still shows it free. The example is stale. The $0.005 is the number I believe.

Advantage: a real webhook and a real send API. Disadvantage: we pay them, in dollars, for citizen messages Meta would carry free. I would not, unless we are already on Twilio for something else.

## Gupshup

An API with webhooks. The fee article that quotes $0.001, on both session and template messages, is stamped **not updated**, last touched June 2024, and the WhatsApp half of the example is an old rate. I am not using it.

What they have published since: from 1 January 2026, marketing that does not go through Marketing Messages Lite costs an extra 6% of Meta's marketing fee. Partner docs say service messages became chargeable on 1 October 2026 and point at a pricing document that is not a public rate card. No public India utility or service fee.

Advantage: it is an API, not an inbox. Disadvantage: **unknown** on the messages this bot sends. A quote, or leave them out of the costing.

## AiSensy

An inbox that also has APIs. Their pricing page: incoming messages free. Sends to Indian numbers, marketing ₹1.09, utility, authentication and service **₹0.145**. They do state the 1,000 free service messages, and that utility inside the window is now charged. So they understood October. Their send price is Meta's ₹0.115 plus about 3 paise. A blog line says you only pay what Meta mandates. The page is higher. The page wins.

Same four sends at ₹0.145: (4N − 1,000) × 0.145.

| Complaints | Messages | Plus the platform |
|---|---|---|
| 1,000 | ₹435 | Basic ₹1,500, or Pro ₹3,200, GST on top |
| 5,000 | ₹2,755 | same |
| 10,000 | ₹5,655 | same |

Project APIs are listed on Pro, not Basic. I would not assume Basic can feed our process. The chatbot builder (₹2,500) and the AI agent are separate products, and they are the prompts we are not buying.

Advantage: rupee prices, on the site, aligned with the October change. Disadvantage: a subscription and a markup for an inbox the bot will not sit in.

## Wati

Growth is $59 a month billed annually, and the plan says **no webhooks**. That fails the brief. Pro is $119, limited webhooks, about ₹11,300 at 94.78 before messages. An extra number is $29 a month. The per-message card is behind a button. Not copied from anyone else's blog. **Unknown.**

Automation triggers are capped (1,000 included on Growth). A citizen chat would burn those, or a person would answer in their screen.

Advantage: a shared inbox, if a team were going to live there. They are not.

## Interakt

Growth is $55 a month plus tax, about ₹5,200. Utility on the page is ₹0.150 (Advanced ₹0.140). Service is printed **FREE**. Incoming-message webhooks are on the paid WhatsApp plans.

Service free, three weeks after Meta started charging for service, cannot go into a costing as written. Either they absorb it and have not said so, or the page is stale. **Unknown** which. Receive is not listed as a charge.

Advantage: a public send API and incoming webhooks on the plan you would buy. Disadvantage: a sales inbox, a dollar subscription, and a service price I will not repeat as fact.

## Side by side

| | Webhook in | Send, this bot | Receive | Before any message |
|---|---|---|---|---|
| Cloud API | Yes | Meta, ₹0.115 | None | None |
| 360dialog | Yes | Meta, passed through | None found | €49 / number |
| Twilio | Yes | Meta + $0.005 | $0.005 | None |
| Gupshup | Yes | Not published | Stale article only | Not published |
| AiSensy | Pro, not clearly Basic | ₹0.145 | None on the page | ₹1,500 or ₹3,200 |
| Wati | Not on Growth. Limited on Pro | Not on the page | Not stated | $59 or $119 |
| Interakt | Paid WhatsApp plans | Utility ₹0.140–0.150. Service printed free | Not stated | $55 or $69 |
| Business app | No | Not the API | n/a | Free, and useless here |

## How this is better, and worse

Better, on the Cloud API: the bill is the rate card, receive stays free, and we are not renting an inbox to throw away. Worse: we operate verification ourselves. 360dialog is the honest alternative when that is the part we do not want, and its cost is a license, not a cheaper message.

Every inbox option is worse on price at these volumes and worse on shape. The bot's prompts are ours. Paying AiSensy or Wati or Interakt to host an AI we will not use is the decision already made, bought back by accident.

## What the later bot changes

More inbound media. Providers who charge per receive (Twilio, and maybe Gupshup) get more expensive as the citizen sends photos. Providers who charge only for the send do not. That pushes further away from Twilio, not towards it. It does not make an inbox product any more able to take a webhook it does not offer.

## Sources (accessed 2026-10-23)

- Twilio WhatsApp pricing — https://www.twilio.com/en-us/whatsapp/pricing
- 360dialog pricing — https://360dialog.com/pricing
- 360dialog client pricing (Meta pass-through, 7% on the wrong marketing endpoint, service billed) — https://docs.360dialog.com/docs/get-started/pricing
- Gupshup fee article, marked by them as not updated — https://support.gupshup.io/hc/en-us/articles/360012075779-Whats-is-Gupshup-s-pricing-model-What-is-Gupshup-fee-and-WhatsApp-fee-in-pricing
- Gupshup, 6% on non-Lite marketing from 1 January 2026 — https://support.gupshup.io/hc/en-us/articles/53700207494169-Gupshup-fee-changes-to-Cloud-API-marketing-w-e-f-1st-Jan-2026
- Gupshup partner pricing note — https://partner-docs.gupshup.io/docs/pricing
- AiSensy pricing — https://aisensy.com/pricing
- Wati pricing — https://www.wati.io/pricing/
- Interakt pricing — https://www.interakt.shop/pricing/
- The Hindu, rupee at 94.78, early trade 23 October 2026 — https://www.thehindu.com/business/markets/rupee-rises-against-us-dollar-on-october-23-2026/article71614598.ece
- MSEI archive of the RBI reference rate, EURINR 106.2839 on 21 October 2026 — https://www.msei.in/markets/Currency/Historical-Data/RBIReferenceRateArchives

**Unknown:** Gupshup's current utility and service fee. Wati's rate card. Whether Interakt's "service free" is a real absorption or a stale page. GST on top of the rupee plans.
