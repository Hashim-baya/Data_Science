# Problem Statement
**File name: `01_problem_statement.md`**

## Background
PriceOye is an online electronics marketplace (Pakistan) that lists laptops from multiple brands (HP, Lenovo, ASUS, Dell, Apple, Acer, Infinix). The dataset `priceoye_laptops_version_2.csv` is a snapshot scrape of 306 laptop listings, containing pricing, discount, specs (Core/CPU, SSD/RAM), brand, model, and limited customer feedback (rating, reviews).

## Business Context
A retailer/marketplace analytics team wants to understand the current laptop catalog to:
- Benchmark pricing and discounting strategy across brands
- Understand product assortment (which specs/brands dominate the catalog)
- Identify gaps or opportunities (e.g., underpriced/overpriced segments, under-reviewed high-value items)
- Support merchandising and marketing decisions (e.g., which brands to promote, which price bands to target)

## Problem Statement
The catalog data is unstructured for analysis in its raw form: pricing/discount fields are inconsistently formatted, spec fields (Core, SSD) mix RAM and storage in free text, brand names have case/spelling inconsistencies, and rating/review data is sparse (~91% missing). The business needs a cleaned, structured dataset and a set of analyses that reveal pricing patterns, brand positioning, and specification trends to guide catalog and pricing decisions.

## Objective
1. Clean and standardize the raw dataset into an analysis-ready format.
2. Engineer features (e.g., RAM, SSD size, discount %, price bands) from messy text fields.
3. Answer a defined set of business questions (see `04_business_questions.md`) using pandas-based exploratory data analysis.
4. Present findings with visuals and a short set of actionable recommendations.

## Scope
- In scope: descriptive/exploratory analysis, data cleaning, feature engineering, visualization, business-question answering.
- Out of scope: predictive modeling (e.g., price prediction ML model), real-time scraping/pipeline automation — unless requested as a follow-up phase.

## Deliverables
- Cleaned dataset (CSV)
- Jupyter notebook with analysis code
- Visualizations (charts/images) answering each business question
- Summary insights/recommendations document
