---
name: shopify-pixel-audit
description: Audits tracking on a Shopify store: customer events and custom pixels, app pixels, duplicate purchase events, values, consent and checkout steps. Use when someone says "Shopify tracking audit", "custom pixel", "purchase event wrong", or "Shopify conversions don't match orders".
---

# Shopify Pixel Audit

Checks how events leave the store and whether each purchase is counted once with the right value.

## Use this when
- Ad platform purchases do not match Shopify orders.
- A custom pixel is used, or is planned.
- Apps and manual code both send events.

## Inputs to ask for
1. Store plan and whether checkout customization is used.
2. A list of installed sales channel apps and tracking apps.
3. Settings, Customer events: the list of pixels (apps and custom).
4. A sample of order data and the matching platform data for the same dates.
5. Consent and privacy settings.

## Workflow
1. **List every sender.** App pixels, custom pixels, theme code, and any old checkout scripts. Write each one down with the platform it feeds.
2. **Find overlaps.** Two senders for the same platform and event is a duplicate risk. Example: a sales channel app and a custom pixel both sending Purchase.
3. **Check the events.** For a custom pixel, the standard customer events include page viewed, product viewed, product added to cart, checkout started and checkout completed. Confirm each needed event is subscribed and mapped.
4. **Check Purchase data.** Order ID, value, currency, items. Decide if value includes tax and shipping and compare with the platform's meaning of revenue.
5. **Check consent.** Pixel permissions in customer privacy settings. Check that events respect the visitor's choice.
6. **Check old methods.** Old checkout or order status scripts are being retired by Shopify. Confirm what is still active in the store.
7. **Compare numbers.** Orders vs platform purchases for the same dates. Note the ratio.
8. **Test.** Place a test order with the user's approval, and follow it in each platform's test view.

## Output format
- A sender table: sender, platform, events, status.
- Findings with risk and fix.
- The comparison ratio and a plain explanation.

## Decision rules
- One platform event should come from one sender. Remove or disable the extra sender after approval.
- If value does not match order total, document the rule and fix at the source.
- If events do not fire after consent, check pixel permission settings first.

## Guardrails
- Read-only. Do not change pixels, apps or settings.
- Test orders must be refunded or cancelled by the owner.
- Shopify features change. Tell the user to confirm current behavior in Shopify's documentation.
