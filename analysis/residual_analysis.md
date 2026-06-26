# Residual Analysis — Multiple Regression Model

## Final Model Used

**Equation:**
```
monthly_sales = 146,249.80 + 33.68 × footfall + 1.18 × marketing_spend + 3,062.93 × inventory_availability_pct − 39,654.57 × Residential_dummy − 22,957.90 × HighStreet_dummy − 11,306.63 × Mall_dummy
```

- **R² = 0.8199** → Model explains 82% of monthly sales variation
- **Reference Category:** Airport store
- **Observations:** 320

---

## Step 1 & 2 — Predicted Sales and Residuals

Predicted sales were calculated using the multiple regression equation above.

- **Residual** = Actual Monthly Sales − Predicted Sales
- **Residual%** = (Residual / Actual Monthly Sales) × 100

These values were added as new columns (Predicted_Sales, Residual, Residual_pct) in the cleaned data sheet of the regression workbook.

---

## Step 3 — Top 5 Largest POSITIVE Residuals
*(Model UNDER-predicted — Actual sales were much higher than expected)*

| Rank | Store ID | Predicted Sales  | Residual  | Residual % |
|------|----------|-------------------|--------------|------------|
| 1 | STR-1073 | 707,767.97 | +105,548.74 | +12.98% |
| 2 | STR-1030 | 715,770.95 | +104,748.09 | +12.77% |
| 3 | STR-1028 | 614,751.11 | +98,860.05 | +13.85% |
| 4 | STR-1032 | 815,726.57 | +98,817.60 | +10.81% |
| 5 | STR-1050 | 642,285.15 | +93,501.49 | +12.71% |

### Business Meaning — Positive Residuals
These stores are **outperforming** what the model predicts.

Possible business reasons:
- **Local advantages** not captured in data — e.g. proximity to busy transit hub, university campus, or popular shopping area
- **Loyal customer base** built over time through excellent service quality
- **Strong store management** delivering better customer experience
- **Local events or seasonal promotions** specific to that catchment area
- These stores represent **best practice examples** — leadership should study what these stores do differently and replicate across the chain

---

## Step 4 — Top 5 Largest NEGATIVE Residuals
*(Model OVER-predicted — Actual sales were much lower than expected)*

| Rank | Store ID | Predicted Sales  | Residual  | Residual % |
|------|----------|-------------------|--------------|------------|
| 1 | STR-1017 | 844,194.64 | −158,815.56 | −23.17% |
| 2 | STR-1023 | 749,860.67 | −122,688.77 | −19.56% |
| 3 | STR-1012 | 713,439.74 | −117,972.14 | −19.81% |
| 4 | STR-1007 | 902,543.28 | −102,091.34 | −12.75% |
| 5 | STR-1009 | 743,585.50 | −101,720.47 | −15.85% |

### Business Meaning — Negative Residuals
These stores are **significantly underperforming** vs model expectations.

Possible business reasons:
- **Local competition** — nearby competitor stores pulling customers away
- **Poor store operations** — staff issues, long queues, poor store layout
- **Neighbourhood decline** — area demographics or footfall patterns changed
- **Temporary disruptions** — renovation, construction nearby, road closures
- **Unmeasured factors** — poor parking, bad public transport links
- These stores need **immediate management attention** and operational review

---

## Step 5 — Business Interpretation Summary

| Residual Type | What It Means | Business Action |
|---------------|---------------|-----------------|
| Large Positive (+£90k to +£105k) | Store beats model expectations significantly | Study & replicate success factors across chain |
| Near Zero (±£10k) | Model predicts accurately | Store performing as expected — maintain |
| Large Negative (−£100k to −£158k) | Store falls far below expectations | Urgent investigation & management intervention |

The largest negative residual is **−£158,816 (STR-1017, −23.17%)** which is very significant — this store needs immediate attention.

The largest positive residual is **+£105,549 (STR-1073, +12.98%)** which shows strong local factors working in its favour.

---

## Step 6 — Under-predicting vs Over-predicting Pattern

### Model OVER-PREDICTS (negative residuals) for:
- Stores like STR-1017, STR-1023, STR-1012 where residuals exceed −£100,000
- These are likely **Residential or High Street** stores facing unmeasured local challenges such as competition or operational problems
- Residual% reaching −23.17% indicates serious unexplained underperformance

### Model UNDER-PREDICTS (positive residuals) for:
- Stores like STR-1073, STR-1030, STR-1028 where residuals exceed +£90,000
- These stores benefit from **local factors** such as loyal customers, events, or unique location advantages not in the dataset
- Maximum positive residual of +£105,549 shows consistent outperformance

### Overall Assessment

The model performs well overall (R² = 0.82), meaning predictions are reasonably accurate for most of the 320 records. However, the presence of large residuals (both positive and negative exceeding ±£100,000) indicates important missing variables:

