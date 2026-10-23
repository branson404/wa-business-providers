23 Oct 2026. Looking up WhatsApp pricing for the Moradabad grievance bot. The number going around is 0.115, and someone guessed about ₹1,000 a month for 1,000 complaints at 5–6 messages each. Neither of those is sourced. Pages below are what I actually opened today.

Meta's own pricing page says the rate card in force is the one effective 1 October 2026, by the messaging account's timezone. https://developers.facebook.com/docs/whatsapp/pricing/ (same text on the documentation URL). The INR workbook is the "INR list rates" link on that page. The file is titled "Cost per message in INR on the WhatsApp Business Platform, effective October 1, 2026". India row, INR:

- Marketing 0.8631
- Utility 0.115
- Authentication 0.115
- Authentication-international 2.4971
- Service 0.115

So 0.115 is a real published rate. It is the India list rate for utility, for authentication, and for service. It is not the marketing rate. It is rupees, not dollars. Read 23 Oct 2026.

Same card, volume tiers workbook ("INR volume tiers" on the same page). India utility stays on the list rate of 0.115 until 25,000,000 messages in a month, then 0.1081. India authentication stays at 0.115 until 750,000 a month. Service has no tier. We will not get near either threshold at 10,000 complaints.

What changed on 1 October, from that same Meta page, not from a blog. Two things that were free are now charged.

Service messages (the free-form replies inside the 24-hour window: text, images, audio, the usual) were free from 1 Nov 2024. From 1 Oct 2026 each business phone number gets 1,000 delivered service messages free per month. They do not roll over. From the 1,001st, Meta charges the service rate. India, that is ₹0.115. No volume discount on those.

Utility templates sent inside an open customer service window were free from 1 July 2025. The 1 Oct 2026 section is headed "Charging for messages that were previously free" and says the pricing type on those utility messages changes from `free_customer_service` to `regular`. The "when we do not charge" section now only lists the free-entry-point window (click-to-WhatsApp ad, up to 7 days) and the 1,000 service messages. Utility-inside-the-window is not in that list anymore. Mint wrote the same thing on 1 Oct 2026, citing Meta's docs: utility in India is ₹0.115 even while the window is open. https://www.livemint.com/technology/whatsapp-business-platform-gets-costlier-from-today-what-indian-businesses-need-to-know-about-new-messaging-charges-11790836512655.html I am treating Mint as a write-up of the docs, not as the rate card.

User messages are still free. Meta does not charge for a citizen writing or sending a voice note to us.

Older cards, so I don't mix them up. Gupshup hosts Meta's October 2025 INR pdf: India marketing ₹0.7846, utility ₹0.1150, authentication ₹0.1150, authentication-international ₹2.3000, service "n/a". https://www.gupshup.ai/resources/wp-content/uploads/2025/10/INR_Oct2025.pdf Their January 2026 pdf (marked on the pdf itself as a future card, not the then-current one) already has India marketing at ₹0.8631 and utility still ₹0.1150, service still n/a, auth-international ₹2.3000. https://www.gupshup.ai/resources/wp-content/uploads/2025/12/INR_Jan2026.pdf So the 0.115 utility/auth figure is at least a year old. What is new since 1 Oct 2026 is that service is also ₹0.115, and utility inside the window is no longer free. Marketing for India did not move on 1 Oct 2026. India is not in Meta's list of markets whose rates changed that day. Auth-international did move, from 2.3000 on the January card to 2.4971 now. We should not hit that if the account is Indian and the citizen numbers are +91. If Meta decides an OTP is "authentication-international", that one message is ₹2.50 instead of ₹0.12. Not putting OTPs in the base sum.

A complaint, the way I think it actually goes. Citizen messages are not in the bill.

1. Citizen sends a voice note or a Hinglish text. Free.
2. Bot asks a clarifying question, ordinary text, inside the window. Service.
3. Citizen answers. Free. Window resets.
4. Bot sends the complaint id. If that is ordinary text, service. If someone makes it a utility template, utility, and that is now charged even inside the window.
5. Next day, "we're on it" or "it's closed". Window is shut, so this has to be a template. A plain status update should be utility at ₹0.115. If Meta's review calls the wording marketing, it is ₹0.8631 instead. That is the whole costing risk.
6. A second status, closure. Same thing.

I am counting 4 messages from us: 2 service, 2 utility. The 5–6 in the guess includes the citizen. Voice note in is an audio message. WhatsApp will deliver the file. Nobody on these pricing pages transcribes Hindi. That is a separate piece of work, not a line on Meta's card.

Scratch, Meta only, one number, list rate ₹0.115, first 1,000 service messages free.

Billable messages = 4×N − 1,000, once N is at least 500 so the free tier is used up. Both categories are the same rate, so swapping the acknowledgement from service to utility does not change the total as long as we still send at least 1,000 service messages in the month.

- 1,000 complaints: 3,000 × 0.115 = ₹345
- 5,000: 19,000 × 0.115 = ₹2,185
- 10,000: 39,000 × 0.115 = ₹4,485

₹1,000 for 1,000 complaints does not fall out of this. 5.5 × 1,000 × 0.115 = ₹632.50, and that wrongly charges the citizen's own messages. The guess is high for a utility/service bot, not low. It is a round number. I would not put it in a costing.

If both outbound templates get classed as marketing (₹0.8631) and the two replies stay service:

- 1,000 complaints: 2,000 × 0.8631 + 1,000 × 0.115 = ₹1,726.20 + ₹115 = ₹1,841.20
- 10,000: 20,000 × 0.8631 + 19,000 × 0.115 = ₹17,262 + ₹2,185 = ₹19,447

That is the case where the ₹1,000 guess is too low. Template wording matters more than which BSP we pick.

GST is not on Meta's rate card. I am not adding 18%.

Cloud API direct. No monthly fee on the rate card. We pay Meta the rates above and we host the webhook ourselves. Business verification, display name, and a phone number that isn't already a consumer WhatsApp account. I did not find an official "verification takes N days" from Meta. More than one admin on the Business Manager, or the login walks out with one person. Hindi and English are template languages plus ordinary Unicode text, not a paid feature. Interactive buttons and lists exist. Several numbers can sit on one account. Meta is not charging a per-number rent on this card. Inbound voice notes arrive as media. We still have to understand them.

Twilio, https://www.twilio.com/en-us/whatsapp/pricing, page says pricing current as of September 2026. Their fee is $0.005 per message, inbound or outbound, on top of Meta, which they say they pass through. A failed message is another $0.001. The same page says, near the top, that during the customer service window Meta charges for utility templates and for non-template service messages. Further down an example still shows utility at $0.0034 outside the window and no Meta charge inside it. I am ignoring that example. It looks like the pre-October sentence left on the page. Meta's card wins.

$0.005 hurts because they charge it on the citizen's message too, including the voice note. The Hindu, early trade 23 Oct 2026, rupee at 94.78 to the dollar. Not the RBI fix, and not a rate Twilio will bill at. 0.005 × 94.78 = ₹0.4739 per message, about four times Meta's ₹0.115.

Six messages a complaint if I count two from the citizen: 6 × $0.005.

- 1,000 complaints: $30, about ₹2,843, plus Meta's ₹345, about ₹3,190
- 10,000: $300, about ₹28,434, plus Meta's ₹4,485, about ₹32,900

Twilio is a real API, webhooks, we build the bot. We would be paying them mostly for carrying messages Meta already prices. I don't see a reason to, unless we are already on Twilio for something else.

360dialog. Pricing page https://360dialog.com/pricing, read today. WhatsApp API Regular is €49 per number per month, Premium €99, Scale €500, all plus Meta's fees. Premium is the one that claims business verification in 48 hours. That is their sentence, not Meta's. Client docs https://docs.360dialog.com/docs/get-started/pricing say usage follows Meta's rate cards, and they bill in INR as well as EUR and USD. Marketing sent through the ordinary messages endpoint instead of the marketing API picks up a 7% surcharge. We should not be sending marketing, so that 7% should not apply. An older partner page still says session messages are free and unlimited and talks about "conversations". That page has not been brought up to 1 Oct 2026. The client pricing page has. I am using the client page.

Their docs also describe service messages as billed, and the only free case they mention is the free-entry-point window. They do not mention Meta's 1,000 free service messages. Meta's own page does. If we buy through them I would still expect the 1,000, because it is Meta's rule, but I have not seen them write it down.

€49. Last RBI reference I could see archived is 21 Oct 2026, EURINR 106.2839, on the MSEI RBI reference-rate archive. Not the 23rd. 49 × 106.28 ≈ ₹5,208 a month before Meta's messages. At 1,000 complaints the license is the bill. At 10,000, license plus Meta is roughly ₹5,200 + ₹4,500.

They are an API, not an inbox we have to live in. We still build the bot. The partner pricing page says zero markup for people reselling them. The direct API plan is the €49 one.

Gupshup. The help article that explains "Gupshup fee + WhatsApp fee" is stamped "THIS ARTICLE IS NOT UPDATED", last updated 14 June 2024, and the example is $0.001 plus a WhatsApp fee of $0.0042. I am not using those numbers. https://support.gupshup.io/hc/en-us/articles/360012075779-Whats-is-Gupshup-s-pricing-model-What-is-Gupshup-fee-and-WhatsApp-fee-in-pricing

What they have published since then: from 1 Jan 2026, marketing sent on Cloud API and not on Marketing Messages Lite gets an extra 6% of the WhatsApp marketing fee. https://support.gupshup.io/hc/en-us/articles/53700207494169-Gupshup-fee-changes-to-Cloud-API-marketing-w-e-f-1st-Jan-2026 Partner docs say the pricing document is elsewhere and, as of a note updated about three weeks ago, that Meta starts charging for service messages on 1 Oct 2026. https://partner-docs.gupshup.io/docs/pricing No public utility or service fee for India. If someone wants Gupshup, it is a sales quote. They are an API. Not an inbox.

AiSensy, https://aisensy.com/pricing, read today. For Indian users they charge marketing ₹1.09, and utility, authentication and service ₹0.145. They do say the first 1,000 service messages a month are free, and that utility inside the window is now chargeable. Incoming messages free. That part matches Meta. The rate does not. Meta is ₹0.115 and ₹0.8631. Their blog still says you only pay what Meta mandates. The pricing page is 3 paise higher on utility and about 23 paise higher on marketing. I am using the pricing page.

Same 4-message mix at ₹0.145, free tier still 1,000 service messages: (4N − 1,000) × 0.145.

- 1,000 complaints: ₹435 of messages
- 5,000: ₹2,755
- 10,000: ₹5,655

Plus the platform. Their tutorial says Basic is ₹1,500 a month and Pro is ₹3,200, GST on top, and Project APIs are a Pro feature. Basic lists template message APIs. I did not open the API reference to see whether Basic can give us an inbound webhook. I would not assume it. Chatbot builder is another ₹2,500 a month. AI agent is ₹1,215 a month billed annually for 1,000 AI messages, and I did not see Hindi speech-to-text in that price. This is an inbox with a broadcast product. The bot would be living in their builder unless Pro's API is actually enough.

Wati, https://www.wati.io/pricing/, read today. Growth is $59 a month billed annually, 3 users, and the usage line says 10k API calls a month, no webhooks. Pro is $119 a month billed annually, 5 users, limited webhooks, 200k API calls. Business is custom, extensive webhooks, multiple numbers. An extra WhatsApp number is $29 a month. The per-message rate card is behind "View Rate Card". It is not printed on the page. I am not copying a number from someone else's comparison. At ₹94.78, Growth is about ₹5,590 a month and still cannot take a webhook. Pro is about ₹11,280 before whatever their rate card says. Wrong shape for this bot. It is a shared inbox and a campaign tool. Automation triggers are capped (1,000 free on Growth). A complaint bot would burn those or make an agent answer by hand.

Interakt, https://www.interakt.shop/pricing/, read today. Growth is $55 a month plus taxes, Advanced $69 plus taxes. Indian message prices printed on the page: Growth marketing ₹0.958, authentication ₹0.128, utility ₹0.150, service FREE. Advanced utility ₹0.140, service still FREE. Enterprise says no markup. Public APIs show up from Growth. Incoming-message webhooks show up on the columns after the first one. At $55 and ₹94.78 the subscription alone is about ₹5,210 a month.

Service FREE on 23 Oct, three weeks after Meta started charging for service, is the problem. Either they are absorbing it and have not said so, or the page is stale. I am not putting "service free" into a number we hand to costing. Utility at ₹0.150 against Meta's ₹0.115 is a markup of about 3.5 paise, if the page is current. Their older resource-centre article still talks about per-conversation prices. Ignore that one.

Filing, because it decides whether an inbox product is even relevant. I am not designing the complaint flow.

NagarNet create is a logged-in POST to complaints/v1/complaints/. JWT, multipart. It wants a description, a type, a subtype, and a ward and a zone, or coordinates so ward detection can fill those in. The complaint is owned by that user, and the city comes off the user's profile. An anonymous citizen cannot file. A webhook can call this, but the caller has to be some service user we create, in the right city.

GreenAssist create is POST /api/v2/complaints, staff JWT, and the body is tied to an existing customer id. Status texts today go out as SMS, not WhatsApp. Same point: the provider's webhook can hit it, the provider does not know what a customer id is. We do.

Any of the API providers can do that webhook. Wati's cheap plan cannot. An inbox BSP can also do it only if we are allowed to subscribe to incoming messages. The identity gap is ours on both systems, whoever carries the WhatsApp traffic.

Open, still. Gupshup's actual fee. Whether Interakt will really not charge service. Wati's rate card. GST. Who holds the Meta Business Manager. Whether the status template survives review as utility. Hindi transcription, which none of these prices include.
