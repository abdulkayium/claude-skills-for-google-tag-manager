---
name: ecommerce-datalayer-spec
description: Writes a GA4 ecommerce dataLayer spec for a custom site (Laravel, custom cart, headless) that a developer can build from. Use when someone says "dataLayer for my store", "ecommerce tracking spec", "what events do I need", or "dev spec for GA4 purchase".
---

# Ecommerce dataLayer Spec

Turns a store's funnel into a clear dataLayer spec: events, fields, sample code and a test list.

## Use this when
- A custom or headless store has no dataLayer yet.
- Purchase tracking is missing, wrong, or fires twice.
- A developer asks "what exactly should I push?"

## Inputs to ask for
1. Platform and stack (Laravel, custom PHP, Next.js, and so on).
2. Which steps exist: product list, product page, cart, checkout steps, thank-you page.
3. Product fields the site already has (id, name, price, category, variant).
4. Currency, and whether prices include tax.
5. Which tools will read the data (GTM web, server-side GTM, GA4, Google Ads, Meta).

## Workflow
1. List only the events the funnel really has: `view_item_list`, `select_item`, `view_item`, `add_to_cart`, `remove_from_cart`, `view_cart`, `begin_checkout`, `add_shipping_info`, `add_payment_info`, `purchase`.
2. For each event, define the fields. Every ecommerce event needs `currency`, `value` (a number) and `items[]`. Each item needs `item_id`, `item_name`, `price`, `quantity`. `purchase` also needs `transaction_id`.
3. Write one sample push per event. Clear the old object first with `dataLayer.push({ ecommerce: null });`.
4. Add rules for `purchase`: fire once per order, never on page reload, use the same `transaction_id` every time.
5. Add a short QA list the developer can run in GTM Preview.

## Output format
- A table: event, when it fires, required fields.
- One code block per event with real field names from the store.
- A test list with expected values.
- A list of open questions for the developer.

## Decision rules
- If prices come as strings, ask the developer to send numbers.
- If the thank-you page can be reloaded, require a once-only guard (cookie, session flag, or server flag).
- If tax or shipping is unclear, define `value` in writing before any ad platform is set up.

## Guardrails
- Read-only. Do not edit GTM or the site. Give the spec and let the user approve changes.
- Never put raw email, phone or name in the dataLayer unless the user needs it for enhanced conversions and has consent.
- Never invent product data. Mark unknown fields as "to confirm".
