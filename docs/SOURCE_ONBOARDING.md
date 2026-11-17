# Onboarding a Data Source

Use this checklist when reviewing **Suggest a Data Source** issues.

## Identity and coverage

- Identify the operator, public URL, and source type.
- List supported categories and fields.
- Distinguish merchant claims, copied listings, and independent tests.
- Check for an existing registration of the same source.

## Access and attribution

- Record public access methods and documentation links.
- Record known attribution and reuse conditions; explicitly mark unresolved conditions.
- Keep authentication material out of this repository.
- Agree on which information can be published and how the source is credited before import.

## Mapping

Document each source field's destination, original unit, normalized unit, conversion, and missing-value behavior.

| Source field | Destination | Original unit | Conversion | Missing behavior |
| --- | --- | --- | --- | --- |
| To be established | To be established | To be established | To be established | `null` |

Also record source-side IDs, product / plan matching rules, region names, currency, full billing terms, special conditions, and whether one source row represents one offer or multiple offers.

## Freshness and conflicts

- Set a realistic refresh interval per type of claim.
- Separate retrieval, observation, and verification times.
- Decide when old stock or prices should become unconfirmed.
- Define how a failed refresh is logged without changing old observation times.
- Document conflicting claims and the evidence a maintainer used to resolve them.

## First import

Start with a small reviewed sample. Confirm identities, references, units, eligibility conditions, and duplicate handling before expanding coverage.

An adapter or automated import must be added and reviewed separately. Registering a source does not itself enable collection or publication.
