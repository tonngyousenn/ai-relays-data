# Contributing to ai relays

Thank you for helping keep the directory useful and current.

## Choose a contribution path

### Submit a listing

Use **Submit a Listing** for a new API relay, subscription merchant / product, or VPS merchant / plan. Include the official URL, category, known specifications, public evidence, and your relationship to the service.

A merchant may submit its own service. Disclose that relationship so the claim and its verification can be recorded separately.

### Report a correction

Use **Report a Correction** for incorrect prices, specifications, availability, expired links, duplicates, or misleading descriptions. Identify the page or record, describe the current value and proposed correction, and link to evidence with an observation date.

### Suggest a source

Use **Suggest a Data Source** for an official website, documentation page, public feed, API, directory, or independent test. Explain its coverage, update behavior, known attribution / reuse conditions, and any access requirements. Do not post access credentials.

## Languages

- English, Simplified Chinese, and Russian submissions are welcome.
- Repository instructions and machine-readable field names use English.
- IDs do not change between languages.
- Preserve official names. Put translated summaries in `description.en`, `description.zh-CN`, and `description.ru` when available.
- Do not manufacture translations for missing content; an absent translation remains `null`.

## Editing data with a pull request

1. Check existing issues and records for duplicates.
2. Read [DATA_STANDARD.md](DATA_STANDARD.md).
3. Create a branch named `listing/<short-name>`, `correction/<record-id>`, or `source/<source-id>`.
4. Change only the relevant records. Keep unrelated formatting changes separate.
5. Add source references and observation dates for changed claims.
6. Complete the pull request template and link the related issue.
7. Request maintainer review. Address review comments before merging.

Do not submit demo fixtures as production data. If a source contradicts an existing record, explain the conflict rather than silently replacing the evidence.

## Review criteria

Maintainers check identity, duplicates, source traceability, units, billing terms, conditional pricing, and which fields have actually been verified. Availability must not be inferred from a working home page alone.

Certification records are issued by maintainers after a separate review. A community listing, payment, or merchant claim cannot set a verified badge.

## Publishing

An approved issue must lead to a reviewed data change. Issues are not the site's database. Automatic validation and website synchronization are not configured yet; maintainers must track publication separately.
