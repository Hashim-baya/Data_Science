# Business Questions
**File name: `04_business_questions.md`**

These are the questions the analysis should answer once the notebook/images are provided. Grouped by theme, with the metric(s) each answer relies on.

## A. Pricing & Discounting
1. What is the distribution of `Discounted Price` across the catalog? Are there distinct price tiers (budget/mid/premium/flagship)?
2. Which brands offer the deepest average discounts (`Discount_Pct`)? Which offer the least?
3. Is there a relationship between price band and discount percentage (e.g., do premium laptops get discounted more or less aggressively)?
4. What are the top 10 most expensive and top 10 cheapest listings, and which brands dominate each end?

## B. Brand & Assortment
5. What is the brand market share within this catalog (count of listings per brand)?
6. How does average/median price differ by brand?
7. Which brand has the widest price range (most diverse portfolio: budget to flagship)?

## C. Specifications
8. What is the most common CPU tier (`CPU_Tier`) in the catalog, and how does it vary by brand?
9. What is the distribution of RAM (`RAM_GB`) and Storage (`Storage_GB`) sizes across listings?
10. Do higher CPU tiers (e.g., i7/i9, Ultra 7/9, M3/M4) correlate with higher `Discounted Price`, as expected?
11. Is there a "sweet spot" RAM+Storage configuration that appears most frequently (likely the market's default configuration)?

## D. Customer Feedback (small-sample, exploratory)
12. Among the ~26 products with ratings, which brands/models are best-rated?
13. Does having a rating correlate with a specific price band (e.g., are premium products more likely to be reviewed)?
14. *(Caveat: with only ~9% of products rated, this analysis is directional, not statistically robust — should be flagged as a data-limitation, not a firm conclusion.)*

## E. Cross-Cutting / Strategic
15. Which brand+spec combination offers the best "value" (e.g., lowest price per GB of RAM/Storage, or best spec-for-price ratio) — a potential merchandising highlight?
16. Are there any outlier listings (unusually high/low price for their spec tier) worth flagging for review (mispricing or data errors)?
17. Based on the above, what 2–3 recommendations would you give the merchandising/marketing team (e.g., which brand to promote, which price band to expand, which segment is under-represented)?

## How to Use This
When you provide the notebook/images, each output (chart/table) should be mapped back to one of the numbered questions above so the final summary can walk through Q1→Q17 with the supporting visual and a one-line insight.
