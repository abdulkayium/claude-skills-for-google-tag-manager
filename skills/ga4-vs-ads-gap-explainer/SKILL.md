---
name: ga4-vs-ads-gap-explainer
description: Explains why GA4 and Google Ads show different conversion numbers and tells apart normal differences from real tracking problems. Use when someone says "GA4 and Google Ads don't match", "why different conversions", or "which number is right".
---

# GA4 vs Google Ads Gap Explainer

Most gaps are by design. This skill shows which part is normal and which part is a problem.

## Use this when
- A client or manager asks why two numbers differ.
- Someone wants to know which tool to trust for a decision.

## Inputs to ask for
1. Both numbers, for the **same dates**.
2. Which conversion action and which GA4 event or key event are compared.
3. Whether the Google Ads action is a native tag or a GA4 import.
4. Attribution settings in both tools.
5. Whether consent mode is in use.

## Workflow
1. Check the match first: same dates, same time zone, same goal definition, same traffic (Google Ads only, or all).
2. Walk through the normal reasons:
   - **Date logic.** Google Ads reports a conversion on the day of the ad interaction by default. GA4 reports on the day of the event.
   - **Credit.** Google Ads gives credit to its own ads. GA4 shares credit across all channels with its own model.
   - **Imported vs native.** An imported GA4 key event follows GA4 rules and can arrive later.
   - **Consent and modeling.** Both tools can model missing data in different ways.
   - **Cross-device and view-through.** Google Ads can count these. GA4 does not count them the same way.
   - **Delay.** Late-arriving data changes recent days.
3. Check the problem causes: duplicate firing, missing tags on some pages, filters, wrong event used.
4. Give a verdict: normal difference, explainable but worth fixing, or likely tracking problem.

## Output format
- One-line answer for a non-technical reader.
- A table: reason, direction (which number goes up or down), how to check, status (normal or problem).
- A recommendation: which source to use for which decision.

## Decision rules
- Use Google Ads numbers to judge and optimize ads in Google Ads.
- Use GA4 for site behavior and cross-channel view.
- Use CRM or shop data as the final truth for money.
- Tell the user not to expect an exact match.

## Guardrails
- Read-only. Do not change settings.
- Do not give a "correct" number. Show the range and the reason for each side.
- Say that product behavior can change, and ask the user to confirm in current documentation when it matters.
