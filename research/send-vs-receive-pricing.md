# Send and receive are not the same price

## The problem

The number going around is 0.115, and a rough guess of about ₹1,000 a month for 1,000 complaints at 5–6 messages each. Neither was sourced. A complaint is not one price: what the citizen sends us and what we send back are billed differently, and since 1 October 2026 the old "replies are free" rule is gone.

## What we'd do

Price one complaint the way it will actually run, on Meta's INR list effective 1 October 2026, and reuse that mix in every other file so the provider comparison does not invent a second arithmetic.

India row, from the "INR list rates" workbook linked on Meta's pricing page:

| Category | Per delivered message, India |
|---|---|
| Marketing template | ₹0.8631 |
| Utility template | ₹0.115 |
| Authentication template | ₹0.115 |
| Authentication-international | ₹2.4971 |
| Service (ordinary reply inside 24 hours) | ₹0.115 |

0.115 is real. It is rupees. It is utility, authentication, and service. It is not marketing.

Utility stays at the list rate until 25 million messages a month. Authentication until 750,000. A city at 10,000 complaints never sees a volume tier.

## The rules that decide the bill

Meta charges a message from us to the citizen, and only when it is delivered. A message from the citizen to us is not on the card. Text, a voice note, a photo, a location pin: receive is ₹0.

What we send depends on the clock.

- Inside 24 hours of their last message, ordinary text is a **service** message. Each number gets **1,000 service messages free per month**. They do not roll over. The 1,001st is ₹0.115.
- A utility template inside that window was free from July 2025. From 1 October 2026 it is ₹0.115 as well. Meta's page puts this under "Charging for messages that were previously free". The pricing type on the webhook goes from `free_customer_service` to `regular`.
- After 24 hours we cannot send free text. A status the next day has to be a template. A plain status should be utility, ₹0.115. If Meta's review calls the wording marketing, it is ₹0.8631. That is the risk that moves the bill. A provider does not remove it.

The business FAQ still says per conversation, and 1,000 free conversations. That page is behind the rate card. See [business-app-vs-platform.md](business-app-vs-platform.md).

## The numbers

Mix, reused everywhere: **2 service replies** (a clarifying question, then the complaint id) and **2 utility templates** (status the next day, then closure). Citizen messages not counted.

Once the month has at least 1,000 service messages, billable sends = 4×N − 1,000, times ₹0.115. Both categories are the same rate, so making the acknowledgement a utility template instead of text does not change the total.

| Complaints / month | Billable sends | Meta only |
|---|---|---|
| 1,000 | 3,000 | **₹345** |
| 5,000 | 19,000 | **₹2,185** |
| 10,000 | 39,000 | **₹4,485** |

Check: 3,000 × 0.115 = 345. 19,000 × 0.115 = 2,185. 39,000 × 0.115 = 4,485.

The ₹1,000 guess does not fall out of this. 5.5 messages × 1,000 × 0.115 = ₹632.50, and that wrongly charges the citizen's own messages. The guess is high for a utility/service bot.

If both templates are classed as marketing (₹0.8631) and the two replies stay service:

| Complaints | Marketing | Service past the free tier | Total |
|---|---|---|---|
| 1,000 | 2,000 × 0.8631 = ₹1,726.20 | 1,000 × 0.115 = ₹115 | **₹1,841** |
| 10,000 | 20,000 × 0.8631 = ₹17,262 | 19,000 × 0.115 = ₹2,185 | **₹19,447** |

GST is not on the card. Not added.

## How this is better, and worse, than the old story

Better: we can separate receive (free, from Meta) and send (₹0.115 if we stay off marketing). The 0.115 figure is sourced. The ₹1,000 guess can be retired.

Worse: replies are no longer unlimited-free. A chatty bot, asking a different follow-up per category, spends the 1,000 free service messages quickly and then pays ₹0.115 a line. That is still small next to a markup or a subscription. It stops being small if the templates are marketing.

## What the later bot changes

More inbound, still free from Meta: a photo, a pin, a name, a second answer. More outbound: one extra question per category is one more service message. Five sends instead of four, at 1,000 complaints, is 5,000 − 1,000 = 4,000 billable × 0.115 = ₹460. Same shape of bill. The category questions change the send count. They do not change the provider.

Voice notes are inbound audio. Meta does not charge them. Nobody on the rate card transcribes Hindi. That cost is not a WhatsApp line.

## Sources (accessed 2026-10-23)

- Pricing on the WhatsApp Business Platform, including the 1 October 2026 changes and the INR workbook links — https://developers.facebook.com/docs/whatsapp/pricing/
- Mint, 1 October 2026, reporting the same change (secondary; the workbook is the rate) — https://www.livemint.com/technology/whatsapp-business-platform-gets-costlier-from-today-what-indian-businesses-need-to-know-about-new-messaging-charges-11790836512655.html
- October 2025 INR card, hosted by Gupshup. India utility and authentication already ₹0.1150, service listed n/a, marketing ₹0.7846 — https://www.gupshup.ai/resources/wp-content/uploads/2025/10/INR_Oct2025.pdf
- January 2026 INR card, hosted by Gupshup, marked on the pdf as a future card. Marketing already ₹0.8631, utility still ₹0.1150 — https://www.gupshup.ai/resources/wp-content/uploads/2025/12/INR_Jan2026.pdf

**Unknown:** GST on Meta's invoice. Whether a real status template survives review as utility. Both are things to check before a number goes into a proposal. The list rates themselves are not unknown.
