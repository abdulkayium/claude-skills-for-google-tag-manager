---
name: form-submit-tracker-gtm
description: Writes a Google Tag Manager Custom HTML listener that tracks a real successful form submit (native, AJAX, or popup) and pushes it to the dataLayer. Use when the built-in Form Submission trigger is unreliable, or someone says "track this form", "popup form tracking", or "form submit not firing".
---

# Form Submit Tracker for GTM

Gives a copy-ready script and a safe way to test it.

## Use this when
- The thank-you page is not a reliable signal (popup, AJAX, embedded form).
- The built-in Form Submission trigger fires on failed or blocked submits.
- Leads are counted on page view instead of real submit.

## Inputs to ask for
1. The page URL and a screenshot or HTML of the form.
2. How the form behaves after submit (redirect, message, popup closes).
3. The form builder (native HTML, HubSpot, Typeform, Webflow, Framer, and so on).
4. Whether the form sends data with `fetch` or XHR, and the endpoint if known.

## Workflow
1. Check first if a built-in trigger can work: Form Submission with "Check Validation" and "Wait for Tags". If yes, use it and stop.
2. If not, choose a signal in this order: success response from the form endpoint, then a success message appearing in the page, then a validated native submit.
3. Fill in the template below. Replace the selector and endpoint.
4. Create a Custom Event trigger on `form_submit_success`. Attach the conversion tags to it.
5. Test in Preview: failed submit must not fire, valid submit must fire once.

## Template (edit the three values at the top)
```html
<script>
(function () {
  var FORM_SELECTOR = 'form#REPLACE_ME';      // the form to watch
  var ENDPOINT_HINT = 'REPLACE_ME';           // part of the submit URL, or '' for native forms
  var fired = false, pending = null;

  function push(source, form) {
    if (fired) return;
    fired = true;
    window.dataLayer = window.dataLayer || [];
    window.dataLayer.push({
      event: 'form_submit_success',
      form_id: (form && form.id) || '',
      form_source: source
    });
    setTimeout(function () { fired = false; }, 3000);
  }

  document.addEventListener('submit', function (e) {
    var f = e.target && e.target.closest ? e.target.closest(FORM_SELECTOR) : null;
    if (!f) return;
    if (f.checkValidity && !f.checkValidity()) return;   // ignore invalid submits
    pending = f;
    if (!ENDPOINT_HINT) push('native_submit', f);         // native form, no AJAX
  }, true);

  if (ENDPOINT_HINT && window.fetch) {
    var orig = window.fetch;
    window.fetch = function () {
      var url = String(arguments[0] && arguments[0].url ? arguments[0].url : arguments[0]);
      var p = orig.apply(this, arguments);
      if (pending && url.indexOf(ENDPOINT_HINT) > -1) {
        p.then(function (r) { if (r && r.ok) { push('fetch_ok', pending); pending = null; } })
         .catch(function () {});
      }
      return p;
    };
  }
})();
</script>
```

## Output format
- The finished script with the user's real selector.
- The trigger and tag setup in 3 to 5 lines.
- A test table: action, expected result, pass or fail.

## Decision rules
- If the form has a visible success message, prefer that signal over the click on the button.
- If two signals fire for one submit, keep the more reliable one and remove the other.
- If the form is inside an iframe from another domain, say the script cannot see it and suggest the vendor's own event or postMessage.

## Guardrails
- Read-only. Do not edit tags or triggers. Give the script and the steps for the user to apply.
- Do not publish the container. Let the user publish after Preview.
- Do not push email, phone or name into the dataLayer by default.
- Say clearly that the script is a template and must be tested on the real site.
