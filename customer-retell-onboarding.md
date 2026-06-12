# Customer Retell AI Onboarding Runbook

**Role:** Rommel (VA #2 — Fulfillment Lead)  
**Trigger:** Slack #konsier-review alert from AGENT-06  
**Estimated time:** 15–20 minutes per customer

---

## Prerequisites

- Access to Retell AI dashboard — app.retellai.com
- Access to Notion KS — Client Onboarding database
- Access to WordPress Konsier admin
- Konsier Retell account credentials (from Drew)

---

## Step 1 — Find the AGENT-06 Draft

1. Open Slack → **#konsier-review**
2. Look for the message: "✅ New Onboarding Draft Ready — Review Required"
3. Click the Notion link in the message
4. The Notion page contains:
   - Agent name suggestion (Avery / Jordan / Casey / Riley / Morgan)
   - Voice recommendation
   - System prompt draft (400–600 words, paste-ready)
   - FAQ entries (6–12 for Starter/Pro, 15–20 for Enterprise)
   - `missing_info` array — if anything is listed here, **stop and message Drew** before continuing

---

## Step 2 — Review the Draft

Before opening Retell, verify:

- [ ] `missing_info` is empty
- [ ] Business name, niche, and service area are correct
- [ ] Hours of operation are complete and formatted
- [ ] Emergency routing rule makes sense for the niche
- [ ] Pricing section does not expose prices if `pricing_policy = "in_home_estimate_only"`
- [ ] Medical/Dental draft includes a HIPAA compliance note
- [ ] Legal draft includes an anti-UPL (no legal advice) note

If anything looks wrong, post in **#konsier-review** and wait for Drew's response. Do not provision until resolved.

---

## Step 3 — Create the Agent in Retell AI

1. Go to **app.retellai.com** → log in
2. Click **Create Agent** → select **LLM (Single Prompt)**
3. Set agent name to the `agent_name_suggestion` from the Notion draft (e.g., "Avery")
4. Under **Voice**, select the voice from `voice_recommendation` in the draft
   - No recommendation listed → use **Aria** for warm niches (dental, medical, legal) or **Derek** for direct niches (HVAC, roofing, plumbing, electrical)

---

## Step 4 — Paste the System Prompt

1. In the LLM editor, find the **System Prompt** field
2. Copy the full `system_prompt_draft` from the Notion page
3. Paste it into Retell — do not edit unless something is factually wrong
4. Scan for any `[BRACKETED PLACEHOLDERS]` — if any remain unfilled, stop and flag to Drew

---

## Step 5 — Configure Post-Call Data Extraction

In the agent's **Post-Call** settings, add these fields:

| Field name | Type |
|---|---|
| caller_name | Text |
| caller_phone | Text |
| reason_for_visit | Text |
| appointment_booked | Boolean |
| urgency_level | Text |

Add any additional fields listed under `post_call_data_extraction_fields` in the Notion draft.

---

## Step 6 — Assign a Phone Number

1. In Retell → **Phone Numbers**
2. Purchase a local number in the customer's primary area code if needed
3. Assign it to the new agent
4. Copy the number — you will add it to the WordPress record in Step 9

---

## Step 7 — Test the Agent

Call the assigned number and run through every check:

- [ ] **Greeting tone** — matches the niche (HVAC: direct/peer-warm · Dental: warm/professional · Legal: measured/formal)
- [ ] **Service inquiry** — ask about one of the customer's listed services, verify correct answer
- [ ] **Booking flow** — attempt to book, verify it collects name, phone, and reason for visit
- [ ] **Emergency routing** — say "this is an emergency" — verify correct response for the niche
- [ ] **Out-of-area** — give a location outside the service area — verify polite decline
- [ ] **AI disclosure** — ask "am I talking to a real person?" — verify it discloses it is an AI
- [ ] **Hours** — ask about a day outside business hours — verify correct hours response

If any check fails, update the system prompt in Retell and retest. After two failed attempts on the same issue, stop and message **Vladimir** in #konsier-review.

---

## Step 8 — Update the Notion Page

Back in the Notion KS — Client Onboarding page:

1. Set **Onboarding Status** → **Live**
2. Add a comment with: Retell agent ID, assigned phone number, date provisioned

---

## Step 9 — Update WordPress Customer Record

1. Log into WordPress Konsier admin
2. Find the customer under **Customers** (custom post type)
3. Fill in:
   - **Retell Agent ID** — copy from Retell dashboard agent settings
   - **Phone Number** — the assigned Retell number
   - **Status** → `live`
4. Save the record

---

## Step 10 — Notify in Slack

Post in **#konsier-review**:

```
✅ [Business Name] — Retell agent live
Agent: [agent_name] | Voice: [voice_used] | Niche: [niche]
Phone: [assigned_number]
All 7 test checks passed
Notion: [link]
```

---

## Escalation Rules

| Situation | Action |
|---|---|
| `missing_info` not empty | Stop — message Drew in #konsier-review |
| Bracketed placeholder left in system prompt | Stop — flag to Drew |
| Test call fails after 2 prompt edits | Stop — message Vladimir |
| Medical/Dental draft missing HIPAA note | Stop — message Drew |
| Legal draft missing anti-UPL note | Stop — message Drew |
| Customer requests human agent during test | Note it, flag to Drew — may need config adjustment |

---

## Reference

- Retell dashboard: app.retellai.com
- Notion KS — Client Onboarding: linked from #konsier-review Slack alert
- Konsier Pipedrive stage after live: **Stage 102 — Live & Healthy**
- Questions: message Vladimir in #konsier-review
