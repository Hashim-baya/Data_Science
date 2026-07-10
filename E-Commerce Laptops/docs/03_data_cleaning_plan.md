# Data Cleaning & Preparation Plan
**File name: `03_data_cleaning_plan.md`**

This is the step-by-step plan to take `priceoye_laptops_version_2.csv` from raw to analysis-ready using pandas.

## 1. Load & Initial Inspection
- Load CSV, set a proper index or `listing_id`.
- Run `.info()`, `.describe()`, `.isna().sum()`, `.duplicated().sum()`.
- Check for exact duplicate listings.

## 2. Brand Standardization
- Normalize case: `.str.strip().str.title()` on `Brand`.
- Merge known duplicates (`Lenovo`/`LENOVO` → `Lenovo`; `Asus`/`ASUS` → `Asus`; `Dell`/`DELL` → `Dell`; `Acer`/`ACER` → `Acer`).
- Validate final unique brand list against expected brands (Apple, HP, Lenovo, Asus, Dell, Acer, Infinix).

## 3. Price Fields
- Confirm `Discounted Price` and `Actual Price` are numeric (already float).
- For rows missing `Actual Price`: decide rule — e.g., assume `Actual Price = Discounted Price` (no discount) or leave null and exclude from discount analysis.
- Sanity check: flag any row where `Discounted Price > Actual Price` (data error).
- Cross-validate `Saving` % against calculated `(Actual - Discounted) / Actual * 100`.

## 4. Discount / Saving Field
- Strip `"% OFF"` and any whitespace, cast to numeric → `Discount_Pct`.
- Recompute discount from prices as `Discount_Pct_calc` and compare to reported value for QA.
- Fill missing `Discount_Pct` with 0 where no discount data exists (only if justified by `Actual Price` check above).

## 5. Core / CPU Field
- Trim whitespace, standardize casing.
- Split into `CPU_Brand` (Intel Core / Intel Ultra / AMD Ryzen / Apple M-series) and `CPU_Tier` (i3/i5/i7/i9, 5/7/9, 3/5/7/9, M1-M4).
- Investigate and manually fix malformed entries (e.g., `Core i513420` → likely `Core i5` + stray model number; verify against `Name`/`Model` column).
- Decide handling for missing Core (~28%): impute from `Name` text if extractable, else leave as `Unknown`.

## 6. RAM / SSD Field
- Standardize separators: replace variants (`GB -`, `GB-`, `GBSSD`, extra spaces) via regex before parsing.
- Extract two numbers: first = RAM (GB), second = Storage (GB or TB, convert TB→GB ×1024).
- Create `Storage_Type` (SSD/HDD/Unknown) based on keyword presence.
- For missing SSD (~70%) — attempt extraction from `Name` field where the spec is embedded there instead (e.g., `"(8GB-256GB)"` pattern seen in row 0); fall back to `Unknown`/NaN otherwise.

## 7. Rating & Reviews
- Given ~91% missing, do NOT impute (imputing would fabricate customer sentiment).
- Create `Has_Rating` boolean flag for segment comparison (rated vs unrated products).
- Treat rating-based analysis as a small-sample/exploratory sub-analysis, not a core KPI, due to low coverage.

## 8. Feature Engineering
- `Price_Band`: bucket `Discounted Price` into quantile-based or fixed bands (e.g., <150K, 150–300K, 300–500K, 500K+).
- `Brand_clean`, `CPU_Brand`, `CPU_Tier`, `RAM_GB`, `Storage_GB`, `Storage_Type`, `Discount_Pct`, `Has_Rating`, `Price_Band`.

## 9. Validation Checks (post-cleaning)
- Re-run `.isna().sum()` — confirm intentional nulls only (e.g., Rating for unrated items).
- Re-run `.describe()` on numeric fields — confirm no impossible values (negative price, RAM > 128GB, etc.).
- Spot-check 10–15 random rows against original `Name` text to confirm parsed fields are correct.

## 10. Output
- Save cleaned dataset as `priceoye_laptops_cleaned.csv` for use in the analysis notebook.
