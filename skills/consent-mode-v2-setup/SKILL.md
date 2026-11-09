---
name: consent-mode-v2-setup
description: Plans and verifies Google Consent Mode v2 with a consent banner (Cookiebot, Usercentrics, and others): default states, update on choice, GTM order, and how to read the gcs and gcd values. Use when someone says "consent mode v2", "consent mode not working", or "cookie banner and Google tags".
---

# Consent Mode v2 Setup

Makes the banner and Google tags speak to each other.

## Use this when
- Setting up Consent Mode v2 for EEA or UK traffic.
- Google Ads or GA4 warns about missing consent signals.
- Conversions drop after a banner was added or changed.

## Inputs to ask for
1. The consent banner (CMP) and how it is installed (GTM template, script, plugin).
2. The regions that need consent.
3. A screenshot of the GTM container tags and the Tag Assistant Consent tab.
4. Which mode is wanted: basic (tags wait) or advanced (tags load with limited, cookieless pings).

## Workflow
1. Confirm the four signals exist: `ad_storage`, `analytics_storage`, `ad_user_data`, `ad_personalization`.
2. Check the **default** state is set to denied for regions that need consent. It must run before any Google tag, so use the Consent Initialization trigger (or the CMP's own template).
3. Check the **update** call runs when the visitor chooses, and that it maps each banner category to the right signals.
4. Check each tag's consent settings in GTM (built-in checks for Google tags, additional checks for others).
5. Verify in the network tab: on a Google request, the `gcs` value shows state. `G100` means ad and analytics storage denied. `G111` means both granted.
6. Test the cases: default, reject all, accept all, partial choice. Then test a region without consent rules.

## Output format
- A pass or fail list for the 6 checks.
- The fixes in order.
- A test table with expected `gcs` and expected tags.

## Decision rules
- If tags fire before the default is set, fix order first. Nothing else matters until then.
- If update never changes the state, the banner and GTM are not connected. Check the CMP template and trigger.
- Explain basic and advanced in plain words and let the business choose. Do not choose for them on legal topics.

## Guardrails
- Read-only. Do not change banner or GTM settings.
- This is not legal advice. Say that consent rules depend on law and the company's own advice.
- Do not promise how much conversion data modeling will recover.
