---
name: meta-capi-dedup-setup
description: Plans or checks Meta Pixel plus Conversions API (CAPI) with correct event IDs and deduplication, including match keys and test steps. Use when someone says "set up CAPI", "Meta events counted twice", "event match quality", or "pixel and CAPI duplicates".
---

# Meta Pixel + CAPI Deduplication

Makes browser and server events agree, so Meta counts each action once.

## Use this when
- Pixel and CAPI both send the same events.
- Events Manager shows duplicates, low match quality or missing parameters.
- A new CAPI setup (GTM server-side, partner app, or direct) needs a plan.

## Inputs to ask for
1. How CAPI is sent (server-side GTM, Shopify app, plugin, custom code).
2. A list of events in use (PageView, ViewContent, AddToCart, InitiateCheckout, Purchase, Lead).
3. Screenshots of Events Manager: Overview and Test Events.
4. Whether `fbp`, `fbc` and customer data (email, phone) reach the server.

## Workflow
1. For each event, check that the browser event and the server event use the **same event name and the same event ID**.
2. Create the event ID once per action in the browser and pass it to the server. A common pattern is the order ID for Purchase and a generated unique ID for others.
3. Check match keys: `fbp` cookie, `fbc` (built from `fbclid`), hashed email, hashed phone, IP and user agent from the real user request.
4. Check value and currency on Purchase.
5. Run the Test Events tool and confirm each event shows both sources, with "Deduplicated" where expected.
6. Compare counts after a few days. Server and browser should be close, not double.

## Output format
- A table: event, browser source, server source, event ID rule, status.
- A list of fixes in priority order.
- A short test plan.

## Decision rules
- Same name, different or missing event ID means duplicates. Fix this first.
- Server events without user data match poorly. Fix data capture before changing anything else.
- Meta only deduplicates inside a limited time window. Check Meta's current documentation for the window and tell the user.
- If the pixel is blocked often, say the server source covers that part and it is still not 100 percent.

## Guardrails
- Read-only. Do not edit events, datasets or tags.
- Never send or paste real customer data. Use dummy values.
- Do not promise a match quality score. Explain what drives it.
