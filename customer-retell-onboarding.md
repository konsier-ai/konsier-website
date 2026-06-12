# Customer Retell AI Onboarding Runbook

**Role:** VA (Fulfillment Lead)
**Trigger:** Slack #konsier-review alert from AGENT-06
**Estimated time:** 10–15 minutes per customer

---

## Your Role in Onboarding

You are the **quality reviewer** — not the builder. Your job is to review the AI-generated onboarding draft, catch anything missing or wrong, and confirm it is ready. Vladimir handles all technical setup.

---

## Step 1 — Find the AGENT-06 Alert

1. Open Slack → **#konsier-review**
2. Look for the message: "✅ New Onboarding Draft Ready — Review Required"
3. Click the Notion link inside the message

---

## Step 2 — Review the Draft in Notion

The Notion page contains the onboarding draft. Go through each item:

- [ ] **Missing info** — is the `missing_info` field empty? If anything is listed there, **stop immediately** and message Drew in #konsier-review before continuing
- [ ] **Business name** — correct and properly spelled
- [ ] **Niche** — matches what the customer signed up for (HVAC / Dental / Legal / Roofing / etc.)
- [ ] **Service area** — city, state, or region is filled in and makes sense
- [ ] **Hours of operation** — complete, no blank days
- [ ] **Emergency routing rule** — present and appropriate for the niche
- [ ] **Pricing policy** — if set to "in_home_estimate_only", verify no prices are mentioned in the draft
- [ ] **Medical/Dental** — must include a HIPAA compliance note
- [ ] **Legal** — must include an anti-UPL (no legal advice) note
- [ ] **System prompt** — scan for any `[BRACKETED PLACEHOLDERS]` — if any remain unfilled, stop and flag

---

## Step 3 — Decision

### If everything looks good:
Post in **#konsier-review**:

```
✅ [Business Name] — draft reviewed, ready to provision
Niche: [niche] | Area: [service area]
No issues found. Vladimir — good to go.
```

### If something is wrong or missing:
Post in **#konsier-review**:

```
⚠️ [Business Name] — review flagged
Issue: [describe the problem clearly]
Waiting on: [Drew / Vladimir / customer info]
```

Do not proceed until the issue is resolved and Vladimir confirms.

---

## Escalation Rules

| Situation | Action |
|---|---|
| `missing_info` field is not empty | Stop — message Drew in #konsier-review |
| Bracketed placeholder left in system prompt | Stop — flag to Drew |
| Business name or niche looks wrong | Stop — flag to Drew |
| Medical/Dental draft missing HIPAA note | Stop — message Drew |
| Legal draft missing anti-UPL note | Stop — message Drew |
| Unsure about anything | Ask Vladimir in #konsier-review — do not guess |

---

## What Happens After You Confirm

Vladimir handles all technical steps:
- Creating the agent in Retell AI
- Configuring the voice and system prompt
- Setting up post-call data extraction
- Assigning the phone number
- Testing the agent
- Updating Notion and WordPress

Your job ends at Step 3. You will see Vladimir's confirmation post in #konsier-review when the agent is live.

---

## Reference

- Notion KS — Client Onboarding: linked from #konsier-review Slack alert
- Questions: message Vladimir in #konsier-review
