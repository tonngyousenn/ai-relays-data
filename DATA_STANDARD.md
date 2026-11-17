# Data Standard

Version: **0.1 — Draft**

This is the initial contract for future production records. It is a documentation standard, not an implemented JSON Schema or automated validation system.

## 1. Three layers

1. **Shared contract:** identity, official URLs, provenance, time, and record state.
2. **Category extensions:** model quotes, subscription offers, or VPS specifications.
3. **Source mappings:** translate a source's field names, units, and update behavior into this contract.

Each source gets a mapping, not an independent business data format.

## 2. Files and identifiers

Use UTF-8 JSON and one record per file. Filenames must match the record's `id`, such as `merchant-example.json`. Use lowercase ASCII letters, digits, and hyphens. IDs remain stable when names, domains, translations, or prices change.

References use IDs, not display names. Do not duplicate the same merchant because it offers more than one product category. Offers and plans receive their own IDs.

No production JSON files are included in the initial repository scaffold.

## 3. Shared fields

| Field | Meaning |
| --- | --- |
| `id` | Stable unique identifier. |
| `recordType` | `source`, `merchant`, `relay`, `subscription-product`, `subscription-offer`, `vps-plan`, or `certification`. |
| `name` | Official or original display name. |
| `description` | Localized text object: `en`, `zh-CN`, `ru`; each value is text or `null`. |
| `officialUrl` | Relevant official page, or `null` when genuinely unknown. Ordinary directory records require a known official URL before publication. |
| `status` | `active`, `unavailable`, or `unconfirmed`. This does not grant certification. |
| `provenance` | Evidence references for factual fields; see below. Source registry entries describe their own origin separately. |
| `updatedAt` | Time this repository record was last substantively edited. |
| `isDemo` | Boolean; production records must be `false`. |

Keep product-specific URLs in fields such as `purchaseUrl` and `documentationUrl`. Public outbound URLs must use HTTPS, or a reviewed HTTP endpoint where HTTPS is unavailable. Never include authentication tokens or customer-specific checkout URLs.

## 4. Evidence and time

Each provenance entry has:

| Field | Meaning |
| --- | --- |
| `sourceId` | Reference to an entry under `data/sources/`. |
| `sourceRecordUrl` | Public page supporting this particular claim. |
| `sourceRecordId` | Source-side identifier, or `null`. |
| `observedAt` | When the source information was observed. |
| `verifiedAt` | When a maintainer checked the claim, or `null`. |
| `method` | `manual`, `api`, or `import`. |
| `fields` | Field paths supported by this evidence, such as `price.amount` or `stock`. |
| `note` | Conditions, conflicts, or limitations; text or `null`. |

Use ISO 8601 timestamps with a time zone, preferably UTC, such as `2026-11-18T03:00:00Z`. Do not update the observation date merely because an import ran. A failed refresh must retain the previous evidence time and record the failure separately.

A merchant description being edited does not make its older prices or stock observations fresh.

## 5. Source registry

In addition to identity fields, source records specify:

- `url`: the source's public root or documentation URL.
- `sourceType`: `official`, `merchant-submission`, `third-party-directory`, or `independent-test`.
- `coverage`: record categories and fields provided.
- `accessMethod`: `web`, `api`, `file`, or `manual`.
- `refreshPolicy`: expected refresh interval and when manual review is needed.
- `mapping`: source fields, units, conversions, and missing-value rules.
- `attribution`: required source credit, or `null` if still being confirmed.
- `reuseNotes`: known reuse conditions and supporting link; use `null` for unknown terms.
- `lastFetchedAt` and `lastVerifiedAt`: successful retrieval and maintainer review times, or `null`.

Official information, merchant claims, directory copies, and tests are distinct kinds of evidence. Source type does not itself mean that every value is verified. Preserve and review conflicts instead of selecting whichever source was fetched most recently.

## 6. Merchant and relay records

Merchants have an official name, domain, and public contact / documentation URLs where available. Keep separate identities when ownership is not established; mark a possible duplicate for review.

Relays reference a merchant and record:

- API base URL and supported interface formats.
- Exact model identifiers and service groups.
- Input, output, and cache prices with currency, unit, and applicable group.
- Model / group-specific availability evidence.
- Links to public terms, refund information, and support instructions where available.

Never infer model authenticity, response speed, or uptime from a merchant's marketing text. Tests must state their method, sample time, and scope. A representative model quote is not a whole-site minimum price.

## 7. Subscription products and offers

**Product:** a standardized item or entitlement. Include platform, product type, entitlement, region restrictions, duration, and access arrangement where relevant.

**Offer:** a specific merchant's sale of that product. Reference `productId` and `merchantId`; preserve the source product name, delivery method, price, stock, after-sales terms, and `purchaseUrl`.

Shared accounts, exclusive accounts, and activation / top-up services must remain distinguishable. A similar title is not enough to establish equivalent products. Offers with unresolved differences may be grouped for discovery but must not be presented as directly equivalent prices.

## 8. VPS and cloud plans

Plan records reference `merchantId` and include:

- `regions`: an array of region codes with separately maintained display names.
- `cpuCores`, plus processor / sharing information if known.
- `memoryMiB`, `diskGiB`, and `storageType`.
- `trafficGB`, `trafficResetPeriod`, and `bandwidthMbps`.
- IP type / count, virtualization, and network route information if known.
- Original price, billing term, renewal price, tax notes, stock, and purchase link.

GiB / MiB use binary units; GB uses decimal units. Source conversions must be explicit. A multi-region plan with the same configuration and price is one plan record with multiple regions. Region-specific price differences require distinct offers or plan records.

CPU core counts do not establish dedicated-core performance. Port bandwidth does not establish measured throughput.

## 9. Prices, stock, and missing values

- Preserve the original amount as a non-negative decimal string, such as `"9.99"`.
- Store ISO currency codes, billing quantity / unit, full payment term, and promotion / eligibility conditions.
- Use `null` for unknown values. Zero is valid only when the source explicitly states a zero price or quantity.
- Stock is `in_stock`, `out_of_stock`, or `unknown`, with its own observation evidence. It is separate from merchant operational status.
- Derived prices retain their formula and input provenance. Keep the exchange-rate source and observation time.
- Monthly equivalent = full-term amount × conversion rate ÷ term length in months, where that conversion is meaningful.
- Hourly, usage-based, and unusual multi-year plans need an explicit assumption; do not silently force them into a monthly comparison.
- Tax, renewals, disk / traffic surcharges, and introductory rates remain separately visible.

A missing price must not enter a budget filter or cheapest-price ranking as zero. Monthly equivalent does not imply that monthly payment is available.

## 10. Certification

Only maintainers issue public certification records after a separate review. Include certificate ID, merchant / relay identity, exact domain, covered model / group / offer IDs, issue / expiry dates, review dates, and public evidence summaries.

Do not store private application or payment details here. Contributors cannot grant their own verified state. The website displays a gold badge only when its effective-date and scope checks pass. Listing inclusion and payment are not certification decisions.

## 11. Review before publication

Before merging production records, verify:

- Unique stable IDs and valid references.
- Matching merchant / product identity; no unresolved duplicate merge.
- Evidence for changed fields and correct time zones.
- Numeric units, currency, term, and comparison assumptions.
- Missing values remain unknown.
- Outbound links resolve to the intended public destination.
- Localized text does not alter shared factual values.
- Certification changes have separate maintainer approval.

These checks are manual until validation tooling is introduced. Schema and adapter changes should be reviewed and documented in the changelog.
