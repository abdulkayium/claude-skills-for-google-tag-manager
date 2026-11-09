---
name: enhanced-conversions-setup
description: Plans and checks enhanced conversions for Google Ads (web and leads): data source, normalizing, hashing, GTM setup and verification. Use when someone says "enhanced conversions", "user-provided data", "improve conversion match", or "enhanced conversions not recording".
---

# Enhanced Conversions Setup

Helps send hashed first-party data with a conversion so Google can match more of them.

## Use this when
- Setting up enhanced conversions for web or for leads.
- Diagnostics shows a warning or "no recent data".
- Match quality seems low.

## Inputs to ask for
1. Conversion type: online sale, web lead, or offline lead import.
2. Where the data is available: form fields, checkout page, dataLayer, or backend.
3. Current setup: Google tag, GTM tag, or API.
4. The Diagnostics status text from the conversion action.

## Workflow
1. Pick the method: automatic collection, CSS selectors or JavaScript variables in GTM, or manual data from the dataLayer. Prefer the dataLayer when the dev team can supply clean values.
2. List the fields to send: email first, then phone, name and address if available.
3. Check normalizing before hashing: trim spaces, lowercase the email, phone in international format. The Google tag hashes plain values before sending; never send values hashed twice.
4. Check that the conversion tag fires after the data is on the page and before any redirect.
5. Check consent: `ad_user_data` must be granted for the user data to be used.
6. Verify: Tag Assistant shows the user-provided data on the tag; the conversion action Diagnostics moves to a healthy state after some traffic.

## Output format
- Method chosen and why (2 lines).
- Field map: field, source, example format.
- GTM steps in order.
- A test plan and what "healthy" looks like.

## Decision rules
- If email is not captured at conversion time, plan it at form step or move to offline import with hashed email.
- If match stays low after fixes, check form field quality (typos, fake emails) before blaming the setup.
- For lead flows, plan "enhanced conversions for leads" together with the CRM stages.

## Guardrails
- Read-only. Do not change tags. Give steps.
- Never paste real customer emails or phones into chat or reports. Use dummy values like `test@example.com`.
- Say that Google's policies and screens change, and tell the user to confirm in current Google documentation.
