---
name: ads-vs-crm-reconciliation
description: Compares Google Ads conversions with CRM leads using a fair method (same dates, click ID filter, clean lifecycle dates) and finds which layer the gap comes from. Use when someone says "Ads and CRM don't match", "CRM has fewer leads", or "reconcile ads and HubSpot".
---

# Ads vs CRM Reconciliation

Compares like with like. Then points to the layer where the numbers split.

## Use this when
- Google Ads says one number and the CRM says another.
- A client doubts the ad data.
- Before blaming tracking, to check if the comparison itself is fair.

## Inputs to ask for
1. Google Ads conversions by action, for an exact date range (export).
2. CRM contacts or leads for the same range (export), with created date, source, click ID and stage dates.
3. Time zones used by both systems.
4. How spam, test and duplicate leads are handled.

## Workflow
1. **Make the comparison fair.** Same dates, same time zone, same definition of a "lead".
2. **Filter the CRM.** Keep leads that have a click ID. Remove test, spam and duplicates (by email). Write down the rule used.
3. **Use the right date.** For stage counts, use the date the contact entered that stage, not the created date.
4. **Count both sides.** Write the two numbers and the gap.
5. **Find the layer.** Walk the chain and count at each step:
   - ad click to landing page
   - landing page to form submit
   - form submit to CRM record
   - CRM record to click ID saved
   - CRM stage to import into Google Ads
6. **Explain the gap.** Split it into: known and fair (spam, duplicates, time zone), explainable (late data), and unexplained.
7. **Decide.** Trust it, fix it, or ask for more data.

## Output format
- A summary line: "Ads X, CRM Y, fair gap Z, unexplained W".
- A funnel table with counts per layer.
- Actions: fix, monitor, or request data.
- A short message the user can send to the client in plain English.

## Decision rules
- If the CRM count with click ID is lower than Ads, check click ID capture first.
- If counts match after filtering, say tracking is healthy and the first comparison was unfair.
- If the gap sits between form submit and CRM, check the form to CRM integration.

## Guardrails
- Read-only. Do not edit CRM or ads data.
- Never say tracking is broken before the comparison is fair.
- Do not include personal data in the report. Use counts.
