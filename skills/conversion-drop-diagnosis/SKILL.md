---
name: conversion-drop-diagnosis
description: A decision tree for a sudden drop in conversions: is the drop real, when did it start, what changed, and which layer broke. Use when someone says "conversions dropped", "no conversions since Monday", "tracking stopped", or "sudden fall in leads".
---

# Conversion Drop Diagnosis

Separates a real business drop from a tracking break. Works with simple exports.

## Use this when
- Conversions fall fast or go to zero.
- A client says "something broke".
- Before changing bids or budgets because of a drop.

## Inputs to ask for
1. Daily data for 4 to 8 weeks: clicks, cost, conversions per action.
2. The exact date or day the drop started.
3. Changes around that date: site release, GTM publish, banner change, ad changes, DNS or hosting change, form change.
4. Business data for the same days (orders, CRM leads, calls).

## Workflow
1. **Is it real?** Compare conversions with clicks and cost. If clicks also fell, it may be a traffic or budget issue, not tracking.
2. **Compare with the business.** If orders or CRM leads are steady while ads conversions fell, suspect tracking.
3. **Find the start.** Pin the first low day. Check the weekday pattern. Weekends and holidays are normal dips.
4. **One action or all?** One action down points to that tag or trigger. All actions down points to the container, consent, or the site.
5. **Check changes on that date.** GTM version history, site releases, banner updates, plugin updates.
6. **Check the platform.** Conversion action status and Diagnostics in Google Ads. Test events in Meta.
7. **Test now.** Make a test conversion. Watch Preview and the network calls.
8. **Rank the causes** by evidence and by how often they happen.

## Output format
- A first answer: "likely real drop" or "likely tracking break", with confidence level (high, medium, low).
- A timeline of the drop and the changes near it.
- Ranked causes, each with the test that proves or removes it.
- Who to ask for what.

## Decision rules
- Clicks steady and conversions zero: tracking first.
- Clicks and conversions both down: look at traffic and budget first.
- Drop right after a site or GTM change: roll back or fix that change first, after approval.
- Do not call it a tracking break from one low day.

## Guardrails
- Read-only. Do not change bids, budgets, tags or conversion actions.
- Do not make up causes. If data is missing, list what you need.
- Keep the message to the client calm and factual.
