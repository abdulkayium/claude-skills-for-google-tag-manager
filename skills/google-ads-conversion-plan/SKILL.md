---
name: google-ads-conversion-plan
description: Plans which Google Ads conversion actions to create, which should be primary or secondary, how to count them, and where each one comes from. Use when someone says "set up conversions in Google Ads", "which conversion should be primary", or "what should Google optimize for".
---

# Google Ads Conversion Plan

Builds a clean conversion list so Google learns from real business results.

## Use this when
- A new account has no clear goals.
- The account counts page views, clicks or spam as conversions.
- Several sources (GA4 import, native tag, CRM import) feed the same goal.

## Inputs to ask for
1. The business type and the real goal (sale, qualified lead, booked call).
2. The funnel steps and rough monthly volume of each.
3. Current conversion actions (a screenshot of Goals, Conversions, Summary is enough).
4. Where each action is measured today (tag, GA4 import, CRM import).

## Workflow
1. List the funnel steps from first touch to money.
2. Mark each step: **primary** (bidding uses it) or **secondary** (reporting only).
3. Pick the count setting: **One** for leads and bookings, **Every** for purchases.
4. Pick one source of truth per action. Never feed the same event from two sources.
5. Set values: real order value for sales; a fixed or modeled value for leads, written down and agreed.
6. Check the conversion window and attribution model. Keep defaults unless there is a reason.
7. Give a short rollout order: fix the main action first, then add deeper stages.

## Output format
A table with these columns: action name, funnel step, primary or secondary, count (One or Every), source, value, owner of the fix.
Then 3 to 5 lines on risks and the next step.

## Decision rules
- Page views, scroll and button clicks are secondary at most.
- If lead quality is weak, plan a deeper stage (qualified lead, won deal) through offline import before changing bids.
- If volume of a deep stage is very low, keep it secondary and use a higher stage for bidding. Google does not publish one fixed minimum, so say "low volume" and explain the trade-off.

## Guardrails
- Read-only. Do not create, edit or remove conversion actions. Give exact steps for the user to apply.
- Never promise results from the change.
- Do not invent values. If the lead value is unknown, say so and ask.
