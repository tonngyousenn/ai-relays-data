# Maintainer Workflow

## 1. Triage the issue

Determine whether it is a listing, correction, or source proposal. Ask for missing evidence through the issue when needed. Check for duplicates and disclosed merchant relationships.

English is the default working language, but Chinese and Russian submissions are accepted. Do not reject useful evidence solely because of its language.

## 2. Review the evidence

Verify which fields the evidence actually supports. Confirm identity, currency, unit, payment term, region, and conditions. A source page being reachable does not verify a service's performance.

Record the date checked. Keep unverified or missing values unknown.

## 3. Prepare a data pull request

Add or update the normalized record and source references. Link the issue and complete the PR template. Keep certification decisions in a separately reviewed change.

Do not merge a raw issue body or an unreviewed scrape directly into production data.

## 4. Check and merge

Use the checklist in DATA_STANDARD.md. Inspect the diff for unrelated changes and private information. Merge only after the record and evidence are acceptable.

The repository currently has no automatic schema or collection workflow. Do not claim that a CI check exists until one has been added.

## 5. Track publication

A merged record and a published website update are different events. Until website synchronization is configured, note whether the approved change has actually been imported and published.

Close the issue with a reference to the implementing PR and a clear outcome. If a proposal is not accepted, explain which evidence or requirement was missing.

## Suggested labels

These names are suggestions; create them in GitHub before using them. Issue forms do not depend on labels being present.

- Types: `listing`, `correction`, `source`, `documentation`.
- Review: `needs-review`, `needs-information`, `approved`, `duplicate`, `not-planned`.
- Categories: `relay`, `subscription`, `vps`.

## Future automation

Introduce schema checks, reference / uniqueness checks, and a deployment integration after the first manually reviewed data cycle is working. Review workflow permissions before enabling automatic publishing.
