# Claude Skills for Conversion Tracking

25 free, open-source Claude Skills for people who set up, fix and explain conversion tracking.

Built by [Abdul Kayium](https://abdulkayium.com), a conversion tracking specialist (GTM, GA4, Google Ads, Meta CAPI, server-side tracking).

## Why this exists

"Check my tracking" is too broad for a normal prompt. These skills break the work into small jobs. Each one asks for the right inputs, follows a set workflow, and gives you a clear output.

Every skill has:
- required inputs
- a step-by-step workflow
- an output format
- decision rules
- guardrails

## What they do not do

The audit and setup skills are **read-only**. The writing skills only write text for you to send. None of them edit tags, change conversion actions, touch budgets or write to your CRM. They give you the findings and the exact steps. You decide and apply.

They also never invent numbers. If data is missing, they tell you what to bring.

## The 25 skills

### Build and set up
| Skill | What it does |
|---|---|
| `ecommerce-datalayer-spec` | GA4 ecommerce dataLayer spec a developer can build from |
| `form-submit-tracker-gtm` | GTM listener for real form submits (native, AJAX, popup) |
| `google-ads-conversion-plan` | Which conversions to create, primary or secondary, One or Every |
| `enhanced-conversions-setup` | Plan and check enhanced conversions for web and leads |
| `meta-capi-dedup-setup` | Pixel plus CAPI with correct event IDs and deduplication |
| `server-side-gtm-launch` | Do you need server-side? If yes, a phased launch plan |
| `consent-mode-v2-setup` | Consent Mode v2 plan, GTM order and how to read `gcs` |
| `gclid-utm-crm-capture` | Save GCLID and UTMs into your CRM with every lead |
| `offline-conversion-import-plan` | Send CRM stages back to Google Ads the right way |

### Debug and audit
| Skill | What it does |
|---|---|
| `gtm-preview-debugger` | Find why a tag does not fire, fires twice or sends wrong values |
| `gtm-container-audit` | Review an exported container for duplicates, risky triggers and gaps |
| `duplicate-conversion-hunter` | Find where one action is counted more than once |
| `ga4-vs-ads-gap-explainer` | Explain why GA4 and Google Ads differ, normal or a problem |
| `ads-vs-crm-reconciliation` | Compare Ads and CRM with a fair method and find the layer of the gap |
| `utm-gclid-loss-tracer` | Follow the visitor path and find where parameters disappear |
| `booking-tool-tracking-check` | Track Calendly, Cal.com and similar booking tools |
| `consent-banner-test` | A repeatable test matrix for banner and tracking |
| `landing-page-tracking-qa` | QA a new or changed page from first load to CRM |
| `shopify-pixel-audit` | Audit Shopify pixels, apps, purchase values and consent |
| `conversion-drop-diagnosis` | A decision tree for a sudden drop in conversions |

### Explain and report
| Skill | What it does |
|---|---|
| `tracking-audit-report` | Turn findings into a clear client report |
| `delivery-message` | A short, trusted message after a setup or fix |
| `owner-friendly-explainer` | Explain tracking in business words |
| `developer-handoff-request` | A ticket a developer can finish without questions |
| `weekly-tracking-update` | A short weekly status update |

## How to install

### Claude (web or desktop app)
1. Download a zip from the `zips/` folder. Use `all-skills.zip` for everything, or one zip per skill.
2. In Claude, open Settings, then the Skills section, and upload the zip. (Menu names can change. Look for where skills are managed.)
3. For `all-skills.zip`, unzip it first and upload each skill zip, or upload the ones you need.

### Claude Code
Copy the skill folders from `skills/` into `~/.claude/skills/` (all projects) or `.claude/skills/` (one project).

```bash
git clone https://github.com/abdulkayium/claude-skills-for-google-tag-manager.git
cp -r claude-skills-for-google-tag-manager/skills/* ~/.claude/skills/
```

## How to use

Just describe the job. Examples:
- "Our Google Ads shows 2x the leads our CRM has. Reconcile them." (`ads-vs-crm-reconciliation`)
- "Conversions fell to zero on Monday." (`conversion-drop-diagnosis`)
- "Write a ticket for the developer to add purchase events." (`developer-handoff-request`)

Bring what each skill asks for: exports, screenshots, Preview traces, counts. Remove personal data first.

## Good to know

- Google, Meta, Shopify and consent tools change often. Skills tell you to confirm current limits in official documentation.
- This is not legal advice. Consent rules depend on your law and your own advisor.
- Not affiliated with Google, Meta, Shopify, Stape or Anthropic.

## Contribute

Found a mistake or want a new skill? Open an issue or a pull request. Keep skills small, read-only and honest about what they can not know.

## License

MIT. See [LICENSE](LICENSE).
