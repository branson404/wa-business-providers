# What the later bot needs the pipe to carry

## The problem

The bot is not this task. Illias was clear: no AI, no webhook build. But the pipe is being chosen for a specific later conversation, and a pipe that cannot hold that conversation is the wrong saving.

The later chat asks for a photo, a location and a name. Follow-up questions differ by category: waste, a broken pipeline, a dead animal. The complaint is created at the end, not on the first message. A new message from the same person has to join the earlier thread. Prompts and the model stay in our process.

## What we'd do

Pick a provider that delivers those inbound types to a URL, and let our process keep the thread. Do not look for a provider that categorises complaints or remembers the chat for us. That is the Meta-assistant decision, already made.

Concretely, the webhook has to give us:

- The sender, stable across messages. On the Cloud API that is `wa_id` / `from`.
- A message id and a timestamp, so we can order them.
- Text, an image, and a location, as distinct types.
- A way to send the next question ourselves, inside the 24-hour window, as an ordinary service message.

We store the thread against the sender id. Category, the photo, the pin and the name live in that record. When the conversation is complete, our system creates the complaint. The provider never sees a complaint type.

## How this is better, and worse

Better: we are not locked to a BSP's chatbot, its context limit, or its "AI messages" meter. Wati's automation triggers, AiSensy's AI-agent bundle and Interakt's agents are products for a different design. Skipping them is not a missing feature.

Worse: continuity, the category questions, and Hindi on a voice note are all our code. The pipe will not do them. A voice note arrives as audio. Transcribing Hindi-English is not on any WhatsApp price list in this pack. A photo has to be downloaded when the webhook arrives: Meta says the media id on an incoming webhook lasts 7 days and the download URL lasts about 5 minutes.

## Compared with letting the provider run the chat

Their inbox keeps history on their screen. That does not help a process of ours unless the same messages also arrive on a webhook. Wati Growth has no webhooks, so the history stays in Wati. That fails both this task and the later one.

Meta Business Agent would keep the context on Meta's side and bill tokens. Rejected, because we cannot shape it the way we can shape our own prompts, and the context it keeps is smaller. Recorded as a decision, not re-opened here.

Filing the complaint is also ours, and it is awkward on both systems we already have. It does not change the provider. It is here so nobody thinks the webhook creates the complaint by itself.

NagarNet's create call is a logged-in POST to `complaints/v1/complaints/`. JWT, multipart, a description, a type, a subtype, and a ward and a zone or coordinates. The complaint belongs to that user, and the city comes from their profile. An anonymous citizen cannot file. A service user in the right city can.

GreenAssist's create call is `POST /api/v2/complaints`, a staff JWT, and an existing customer id. Status texts today are SMS, not WhatsApp. Pointing a closure at WhatsApp is later work, after the template category is settled.

## Cost

No new line. Extra questions are extra service messages at ₹0.115 after the free tier, worked in [send-vs-receive-pricing.md](send-vs-receive-pricing.md). Inbound photos and pins are free from Meta, and expensive only on a provider that charges for the receive. That is Twilio, in [providers.md](providers.md).

## What we are not designing

The question trees. The categories. The prompt. The webhook server. Which of NagarNet or GreenAssist is the system of record for Moradabad. Those wait until the pipe is chosen.

## Sources (accessed 2026-10-23)

- Incoming text webhook, `from`, `id`, `wa_id` — https://developers.facebook.com/docs/whatsapp/cloud-api/webhooks/payload-examples/
- Media ids and expiry — https://developers.facebook.com/docs/whatsapp/cloud-api/reference/media/
- Location message fields — https://developers.facebook.com/docs/whatsapp/cloud-api/messages/location-messages/
- NagarNet create — `nagarnet/complaints/api/v1/views.py` in the GreenAssist base repo, mounted under `complaints/v1/`
- GreenAssist create — `ComplaintV2Controller.java`, `POST /api/v2/complaints`

**Unknown:** the exact incoming location payload. Confirm with one test pin before the bot promises a map pin. Not a reason to prefer one API provider over another.
