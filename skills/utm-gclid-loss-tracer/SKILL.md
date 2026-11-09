---
name: utm-gclid-loss-tracer
description: Finds where UTMs and click IDs get lost between the ad and the conversion: redirects, cross-domain steps, payment returns, booking tools and consent delays. Use when someone says "UTMs missing", "direct traffic too high", "source lost", or "gclid disappears".
---

# UTM and Click ID Loss Tracer

Follows the visitor path step by step and marks the exact point where parameters disappear.

## Use this when
- Traffic shows as direct or unassigned.
- Leads or orders have no source.
- Parameters show on the landing page but not at the end.

## Inputs to ask for
1. The final ad URL with all parameters (use a test copy).
2. The full journey: landing page, form or cart, checkout or booking, thank-you page.
3. Any other domains in the journey (payment, booking, checkout).
4. Redirect rules the site uses (www, https, trailing slash, language or country).

## Workflow
1. **Check redirects.** Follow the URL chain and watch the parameters. Example command:
   `curl -sIL "https://example.com/?gclid=TEST&utm_source=test" | grep -iE "^(HTTP|location)"`
   Each `location` line should still contain the parameters.
2. **Check the landing page.** Open the page with the test URL. Confirm the parameters stay in the address bar and are read by the tags.
3. **Check storage.** Confirm the values are saved after arrival (cookie or storage) and survive a second page.
4. **Check internal links and buttons.** Some sites rebuild URLs and drop parameters.
5. **Check cross-domain steps.** Confirm the linker or parameter passing works to the other domain and back.
6. **Check return pages.** Payment and booking tools often return without the original parameters.
7. **Check timing.** A consent banner or slow script can delay saving the values.
8. Mark the first step where the values are gone. That is the fix point.

## Output format
- A journey table: step, URL, parameters present (yes or no), notes.
- The first loss point, with proof.
- The fix, and who owns it (site team, GTM, vendor).

## Decision rules
- Loss at a redirect: ask the developer to pass the query string through the redirect.
- Loss at an outside domain: use cross-domain settings or pass values in the URL.
- Loss after return from payment: save the values before the user leaves, and read them on return.

## Guardrails
- Read-only. Use test URLs only. Do not run tests that create real orders or real leads without the user's approval.
- Do not change redirect or server settings. Give a request for the owner.
