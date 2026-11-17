# ai relays — Community Data

Community-maintained listings, source records, and corrections for **ai relays**: AI API relays, AI subscription channels, and VPS / cloud hosting plans.

This repository is the public home for data contributions and review history. Website application code is maintained separately.

## Contribute

Choose the form that matches your request:

- [Submit a Listing](https://github.com/tonngyousenn/ai-relays/issues/new?template=01-listing.yml)
- [Report a Correction](https://github.com/tonngyousenn/ai-relays/issues/new?template=02-correction.yml)
- [Suggest a Data Source](https://github.com/tonngyousenn/ai-relays/issues/new?template=03-source.yml)

Include public evidence and the date you checked it. If a value is unknown, say so rather than estimating it. A submission is a request for review; it does not automatically publish a listing or award certification.

Contributions may be written in **English, Simplified Chinese, or Russian**. English is the default language for repository documentation, field names, IDs, and labels. Keep official merchant and product names in their original spelling.

## How changes reach the directory

1. A contributor opens an issue with the relevant form.
2. A maintainer checks the evidence, record identity, and applicable specifications.
3. A pull request adds or corrects the normalized data and references the issue.
4. A maintainer reviews and merges the change.
5. A website integration imports the approved data when that integration is available.

**Current stage:** repository setup. No production listings, collection adapters, automatic data validation, or website publication workflow have been added yet. Submitting or merging an issue alone does not update the website.

## Repository structure

```text
.github/
  ISSUE_TEMPLATE/          Listing, correction, and source forms
  pull_request_template.md
CONTRIBUTING.md            Contributor and maintainer workflow
DATA_STANDARD.md           Shared data contract
CHANGELOG.md               Changes to this repository's conventions
DATA_REUSE.md              Source attribution and reuse guidance
data/
  sources/                 Registered origins and collection methods
  merchants/               Shared merchant identities
  relays/                  API relay records and scoped model quotes
  subscriptions/
    products/              Standardized subscription products
    offers/                Merchant-specific product offers
  vps/
    plans/                 VPS and cloud hosting plans
  certifications/          Maintainer-issued public certification records
  README.md                File naming and directory guidance
docs/
  SOURCE_ONBOARDING.md      Source mapping and freshness checklist
  MAINTAINER_WORKFLOW.md    Review and merge procedure
```

The data directories start empty on purpose. Documentation examples are not live listings.

## Data principles

- Every factual claim should be traceable to a source and an observation time.
- Merchant identity, product identity, and individual offers are separate records.
- Original prices, units, currencies, billing terms, and conditions are preserved.
- Missing values are `null`, never an inferred zero or a fabricated measurement.
- A directory listing is separate from a certification decision.
- Machine-readable translations share stable IDs and numeric data.

Read the [data standard](DATA_STANDARD.md), [contribution guide](CONTRIBUTING.md), and [source onboarding checklist](docs/SOURCE_ONBOARDING.md) before preparing data files.

## Public information only

Issues, pull requests, and merged records are public. Do not include passwords, API keys, private customer information, or unredacted order records. Use public evidence or a redacted excerpt where necessary.

## Data reuse

Attribution and reuse conditions are recorded per source. This repository currently declares no blanket license for third-party material. See [DATA_REUSE.md](DATA_REUSE.md).
