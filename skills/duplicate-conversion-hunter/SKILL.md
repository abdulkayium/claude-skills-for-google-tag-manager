---
name: duplicate-conversion-hunter
description: Finds where one real action is counted more than once across GTM, GA4, Google Ads, Meta and the CRM, then gives a ranked fix list. Use when someone says "duplicate conversions", "conversions too high", "counted twice", or "numbers look inflated".
---

# Duplicate Conversion Hunter

Looks at every place a duplicate can start, from most to least common.

## Use this when
- Platform conversions are higher than real orders or leads.
- A thank-you page can be reloaded or bookmarked.
- GA4 import and a native tag both exist for the same goal.

## Inputs to ask for
1. Counts for the same date range: platform conversions, GA4 events, CRM or shop orders.
2. A screenshot of Google Ads conversion actions (source, count setting, status).
3. A list of tags that fire on the key page or event.
4. Whether transaction IDs are sent.

## Workflow
1. Measure the gap: platform count divided by real count. Write the ratio.
2. Check the **count setting**. A lead action set to **Every** counts repeat clicks and reloads. Leads usually need **One**.
3. Check **two sources for one goal**: GA4 import plus a native Google Ads tag, or two tags in two containers.
4. Check **page-based triggers**. A thank-you page view counts again on reload or when the sales team opens it.
5. Check **two signals for one action**: form submit plus thank-you page, or button click plus submit.
6. Check **pixel and server events** without a shared event ID (see `meta-capi-dedup-setup`).
7. Check **single-page app** route changes that send the event again.
8. Check **transaction ID** repeats in exports. Repeated IDs prove duplicates.
9. Rank the causes by evidence, then by how common they are.

## Output format
- The gap ratio and what it suggests.
- A ranked list: cause, evidence found or needed, test, fix.
- A "safe first fix" at the top.

## Decision rules
- If the ratio is close to 2, look for two sources firing together.
- If the ratio is above 2 with no pattern, look at count setting and reloads.
- If repeated transaction IDs exist, fix once-only firing before anything else.

## Guardrails
- Read-only. Do not change conversion actions or tags.
- Do not call a gap "fraud" or "bug" before checking definitions and date ranges.
- Do not invent counts. Use only the numbers the user gives.
