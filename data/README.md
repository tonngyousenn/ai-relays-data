# Data Directory

This folder is reserved for approved normalized records. It currently contains no production data.

| Directory | Record type |
| --- | --- |
| `sources/` | Source registry entries and field mappings. |
| `merchants/` | Shared merchant identities. |
| `relays/` | API relay records and scoped model quotes. |
| `subscriptions/products/` | Standardized products / entitlements. |
| `subscriptions/offers/` | Merchant-specific offers referencing products. |
| `vps/plans/` | VPS and cloud hosting plans referencing merchants. |
| `certifications/` | Maintainer-issued public certification records. |

Use UTF-8 JSON and one record per file. The filename must be `<id>.json`. Placeholder `.gitkeep` files only preserve empty directories and are not data records.

Read [DATA_STANDARD.md](../DATA_STANDARD.md) before adding records. Register a source before referencing its ID. Preserve original prices and observation dates; unknown values must be `null`.

Record validation and website ingestion are not implemented yet. Review remains manual. Private applications, payment details, credentials, and customer records do not belong in this public directory.
