---
name: offline-conversion-import-plan
description: Plans Google Ads offline conversion imports from a CRM: which stages to send, required columns, timestamps, values, upload method and checks. Use when someone says "offline conversion tracking", "send qualified leads to Google Ads", "OCT setup", or "import CRM stages".
---

# Offline Conversion Import Plan

So Google Ads learns from qualified leads and closed deals, not only form fills.

## Use this when
- Lead quality is weak and the CRM knows which leads are good.
- Sales happen offline, by phone, or after a long cycle.
- An OCT upload runs but Diagnostics shows errors.

## Inputs to ask for
1. The CRM and its stages (lead, qualified, opportunity, won).
2. Monthly volume at each stage.
3. Whether GCLID is saved on the lead (see the `gclid-utm-crm-capture` skill).
4. The upload method wanted: scheduled file or Sheet, API, Zapier or Make, or a partner tool.
5. The account time zone.

## Workflow
1. Pick the stages to send. Match one conversion action to one stage.
2. Decide primary or secondary for each, based on volume. A stage with very low volume is usually secondary.
3. Define the columns: click ID (GCLID), conversion name (exactly as in Google Ads), conversion time, value, currency.
4. Set the time format and time zone rule. Use the format Google expects and the account time zone or an explicit offset.
5. Set the value rule: real deal value, or a fixed value per stage, agreed in writing.
6. Plan dedupe: do not send the same lead and stage twice.
7. Plan the schedule (daily is common) and a small first batch to test.
8. After upload, check the import status and Diagnostics. Compare imported counts with CRM counts for the same dates.

## Output format
- A stage table: stage, conversion action, primary or secondary, value rule.
- A column map with an example row (dummy data).
- A launch checklist and a weekly check.

## Decision rules
- No GCLID on leads: fix capture first, or use enhanced conversions for leads with hashed email.
- Conversion name mismatch is the most common error. Check the exact spelling and case.
- Import limits and windows depend on the conversion action settings and Google's rules. Tell the user to confirm the current limits in Google documentation before launch.

## Guardrails
- Read-only. Do not upload or edit anything.
- Never paste real leads into reports. Use dummy rows.
- Do not promise better ROAS. Explain what the data change enables.
