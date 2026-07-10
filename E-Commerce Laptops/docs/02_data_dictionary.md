# Data Dictionary
**File name: `02_data_dictionary.md`**

Dataset: `priceoye_laptops_version_2.csv`
Rows: 306 | Columns: 10 (+ unnamed index column)

| Column | Type (raw) | Description | Missing | Quality Issues Observed |
|---|---|---|---|---|
| `Unnamed: 0` / index | int | Row index from original scrape | 0 | Not a meaningful ID; can be dropped or used as `listing_id` |
| `Name` | string | Full product listing title (brand + model + specs combined) | 0 | Free text; specs sometimes embedded here too (e.g., "8GB-256GB") |
| `Discounted Price` | float | Current selling price (PKR) | 0 | Clean numeric, but wide range (86K–1.55M) suggests outliers/luxury segment |
| `Actual Price` | float | Original / pre-discount price (PKR) | 15 (~5%) | Missing where no discount exists — needs logic check |
| `Saving` | string | Discount percentage as text, e.g. `"21% OFF"` | 15 (~5%) | Stored as text with "% OFF" suffix; must be parsed to numeric |
| `Rating` | float | Average customer rating (scale appears 0–5) | 280 (~91%) | Mostly missing — only 26 products have any rating |
| `Reviews` | float | Number of reviews backing the rating | 280 (~91%) | Missing in lockstep with Rating (same 26 products) |
| `Brand` | string | Manufacturer brand | 0 | Case inconsistency: e.g. `Lenovo` vs `LENOVO`, `Asus` vs `ASUS`, `Dell` vs `DELL`, `Acer` vs `ACER` — needs normalization |
| `Core` | string | Processor family/tier (e.g., Core i5, Ultra 7, Ryzen 5, M3) | 87 (~28%) | Inconsistent formatting; at least one malformed value (`Core i513420`, likely a merged model number) |
| `SSD` | string | Combined RAM + storage spec, e.g. `"16GB-512GB SSD"` | 214 (~70%) | Free text, inconsistent delimiters (`-` vs ` - `), inconsistent spacing (`512GBSSD` vs `512GB SSD`), mixes RAM and SSD size in one field |
| `Model` | string | Model name (Brand and spec-stripped version of Name) | 0 | Generally clean but should be spot-checked for residual spec text |

## Derived / Engineered Fields (to be created during cleaning)
| New Field | Derived From | Logic |
|---|---|---|
| `Brand_clean` | `Brand` | Title-case normalization, merge duplicate brand spellings |
| `Discount_Pct` | `Saving` | Strip `"% OFF"`, cast to numeric (or recompute from prices as a QA check) |
| `RAM_GB` | `SSD` / `Name` | Extract leading number before first `GB` in the RAM-SSD string |
| `Storage_GB` | `SSD` / `Name` | Extract storage size (GB, converted if in TB) |
| `Storage_Type` | `SSD` | Flag SSD vs HDD vs unspecified |
| `CPU_Brand` | `Core` | Group into Intel / AMD / Apple Silicon |
| `CPU_Tier` | `Core` | Normalize tier labels (i3/i5/i7/i9, Ultra 5/7/9, Ryzen 3/5/7/9, M1–M4) |
| `Has_Rating` | `Rating` | Boolean flag for whether product has any customer feedback |
| `Price_Band` | `Discounted Price` | Bucket into Budget / Mid-range / Premium / Flagship |

## Notes for Cleaning Phase
- Verify `Actual Price` missingness correlates with `Saving` missingness (both 15 — likely same rows, no discount recorded).
- Confirm no negative or zero prices exist.
- Investigate the malformed `Core i513420` value manually.
- Standardize `SSD` field with regex before splitting into RAM/Storage.
