---
name: gclid-utm-crm-capture
description: Plans how to capture GCLID and UTM values on the landing page and save them into a CRM (HubSpot, Salesforce, Pipedrive, and others) with every lead. Use when someone says "save gclid in CRM", "UTM tracking for leads", "hidden fields for UTM", or "source missing in CRM".
---

# GCLID + UTM to CRM Capture

Keeps the ad click data attached to the lead so sales can be matched back to ads.

## Use this when
- Leads in the CRM have no source or no click ID.
- Offline conversion import is planned and needs the GCLID.
- Forms are on several pages, or a booking tool sits in the journey.

## Inputs to ask for
1. The CRM and the form tool.
2. The landing page and form URLs.
3. Whether Google Ads auto-tagging is on.
4. Existing CRM properties for source fields.

## Workflow
1. Confirm auto-tagging is on, so `gclid` (and `gbraid`, `wbraid` for app and privacy-limited traffic) is added to ad URLs.
2. Capture from the URL on arrival: `gclid`, `gbraid`, `wbraid`, and `utm_source`, `utm_medium`, `utm_campaign`, `utm_term`, `utm_content`.
3. Store the values so they survive page changes: first-party cookie or local storage. Note that Safari can limit how long script-set cookies live, so plan to save to the CRM at the first form submit.
4. Fill hidden form fields at submit time from the stored values.
5. Map each hidden field to a CRM property. Create properties if missing. Keep **first touch** and **last touch** in separate fields.
6. Test with a dummy URL such as `?gclid=TEST123&utm_source=test`. Submit a test lead and check the CRM record.
7. Add a weekly check: percent of new leads with a click ID, split by source.

## Output format
- A field map: URL parameter, hidden field name, CRM property.
- The steps for the user's form tool.
- A test plan and a monitoring query idea.

## Decision rules
- If the form is on another domain or in an iframe, pass the values through the URL or the vendor's hidden field feature.
- If a booking tool is used, check the values survive into the booking record.
- A fake `TEST123` value will not match a real click. Do not import test leads to Google Ads.

## Guardrails
- Read-only. Do not edit forms, CRM properties or records.
- Do not store more personal data than needed.
- Never invent a capture rate. Calculate it from data the user provides.
