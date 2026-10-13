# Week 02 — Energy Efficiency: Multiple Linear Regression

## Dataset
UCI Energy Efficiency (768 buildings, 8 design attributes). Target: Heating Load (Y1).
Qualitative columns X6 (Orientation) and X8 (Glazing Area Distribution) were removed — 
they are categorical-like integer codes with no meaningful numeric order, so they are not 
valid quantitative predictors. Cooling Load (Y2) was excluded so one target never predicts 
another. Remaining predictors: X1–X5, X7 (6 quantitative). No missing values.

## EDA Findings

**Most related to Heating Load**
- Overall Height (X5) — strongest, positive (r = +0.89): taller buildings need more heating.
- Roof Area (X4) — strongest negative (r = −0.86).
- Surface Area (X2, r = −0.66) and Relative Compactness (X1, r = +0.62) — moderate.
- Wall Area (X3, r = +0.46) and Glazing Area (X7, r = +0.27) — weaker.

**Shape:** Relationships are mostly linear (regression plots), supporting a linear model.

**Skew / outliers:** No extreme outliers. Several predictors are discrete/bimodal rather 
than smoothly continuous — Overall Height (X5) and Roof Area (X4) are clearly bimodal, 
Glazing Area (X7) takes a few distinct levels. Heating Load (Y1) is mildly right-skewed.

**Collinearity:** Very strong. Relative Compactness (X1) and Surface Area (X2) are almost 
perfectly correlated (r = −0.99), and Roof Area (X4) and Overall Height (X5) nearly so 
(r = −0.97). Glazing Area (X7) is the exception — uncorrelated with everything else.

**New chart types used:** KDE (density) plots, violin plots, and a correlation clustermap 
(three beyond the class set). The KDE and violin plots revealed the discrete/bimodal nature 
of the predictors; the clustermap grouped the collinear predictors together, making the 
X1–X2 and X4–X5 overlap obvious at a glance.

## Model Performance
Multiple linear regression on standardized predictors, 75/25 train/test split 
(576 / 192 rows), random_state = 42.

| Set   | R²    | RMSE  | MAE   |
|-------|-------|-------|-------|
| Train | 0.915 | 2.920 | 2.024 |
| Test  | 0.915 | 2.989 | 2.147 |

The model explains ~91.5% of the variance in Heating Load on unseen data, with a typical 
error of about 3 units (RMSE) — small relative to the Heating Load range (~6–43). 
Train and test scores are identical, so there is no overfitting. Residual diagnostics show 
errors centred at zero with mild heteroscedasticity (wider spread at higher loads).

## Parameter Interpretation
Coefficients are on standardized features, so they show the change in predicted Heating Load 
per one-standard-deviation increase in a feature, holding others fixed.

- **Intercept = 22.1** — predicted Heating Load for an average building.
- **Overall Height (X5): +7.0** — biggest driver; taller buildings need much more heating. 
  Physically sensible.
- **Relative Compactness (X1): −6.8** — sign is *flipped* vs its raw positive correlation, 
  caused by collinearity with Surface Area (X2). Not reliable on its own.
- **Roof Area (X4): −4.2** and **Surface Area (X2): −3.9** — negative; X2 shares the same 
  collinearity caution.
- **Glazing Area (X7): +2.7** — more windows raise heating load; trustworthy because X7 is 
  independent of other predictors.
- **Wall Area (X3): +0.8** — smallest effect.

**Takeaway for a designer:** Building height and glazing area are the clearest, most reliable 
levers on heating load. The compactness/surface-area coefficients are large but entangled by 
collinearity, so building shape should be treated as one combined factor rather than tuned 
individually.