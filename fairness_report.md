# Fairness Metrics Report — JJUSHYCSH Referral No-Show Risk Model

Generated 2026-10-01 by Abdi Farah Ahmed from the Module 3 test split (16,499 appointments). Favourable outcome = being flagged High risk (it triggers extra outreach support, never reduced care).

Criteria (Module 2 plan): disparate impact ratio >= 0.8; equalized-odds difference <= 0.1. Primary criterion: equal opportunity (recall parity), because the aim is to reach at-risk patients equally in every group. Protected attributes are the Module 3 bias-audit groups.

## gender

| Group | n | No-show base rate | Flag rate | Recall (TPR) | FPR | Precision |
|---|---|---|---|---|---|---|
| F | 10,878 | 0.205 | 0.430 | 0.707 | 0.359 | 0.336 |
| M | 5,621 | 0.207 | 0.423 | 0.710 | 0.349 | 0.346 |

- Demographic parity difference: 0.007
- Disparate impact ratio: 0.984 (meets 0.8)
- Equalized-odds difference: 0.010 (meets 0.1); TPR gap 0.003, FPR gap 0.010
- Fairlearn cross-check: DP diff 0.007, EO diff 0.010

## age_band

| Group | n | No-show base rate | Flag rate | Recall (TPR) | FPR | Precision |
|---|---|---|---|---|---|---|
| 0-5 | 1,683 | 0.203 | 0.541 | 0.936 | 0.441 | 0.351 |
| 18-34 | 3,607 | 0.242 | 0.650 | 0.925 | 0.562 | 0.344 |
| 35-54 | 4,606 | 0.205 | 0.434 | 0.691 | 0.368 | 0.326 |
| 55-69 | 2,919 | 0.156 | 0.091 | 0.211 | 0.069 | 0.360 |
| 6-17 | 2,326 | 0.245 | 0.624 | 0.879 | 0.542 | 0.344 |
| 70+ | 1,358 | 0.150 | 0.060 | 0.108 | 0.052 | 0.268 |

- Demographic parity difference: 0.589
- Disparate impact ratio: 0.093 (below 0.8)
- Equalized-odds difference: 0.828 (exceeds 0.1); TPR gap 0.828, FPR gap 0.510
- Fairlearn cross-check: DP diff 0.589, EO diff 0.828

## scholarship

| Group | n | No-show base rate | Flag rate | Recall (TPR) | FPR | Precision |
|---|---|---|---|---|---|---|
| 0 | 14,825 | 0.198 | 0.409 | 0.682 | 0.341 | 0.330 |
| 1 | 1,674 | 0.270 | 0.596 | 0.876 | 0.492 | 0.397 |

- Demographic parity difference: 0.187
- Disparate impact ratio: 0.686 (below 0.8)
- Equalized-odds difference: 0.194 (exceeds 0.1); TPR gap 0.194, FPR gap 0.150
- Fairlearn cross-check: DP diff 0.187, EO diff 0.194

## has_disability

| Group | n | No-show base rate | Flag rate | Recall (TPR) | FPR | Precision |
|---|---|---|---|---|---|---|
| 0 | 16,223 | 0.206 | 0.431 | 0.712 | 0.358 | 0.340 |
| 1 | 276 | 0.163 | 0.217 | 0.378 | 0.186 | 0.283 |

- Demographic parity difference: 0.214
- Disparate impact ratio: 0.504 (below 0.8)
- Equalized-odds difference: 0.335 (exceeds 0.1); TPR gap 0.335, FPR gap 0.172
- Fairlearn cross-check: DP diff 0.214, EO diff 0.335

## Mitigation

Applied on **age_band**: group-specific thresholds chosen on validation (equal opportunity).
Group thresholds: 0-5=0.618, 18-34=0.622, 35-54=0.554, 55-69=0.506, 6-17=0.610, 70+=0.500.
TPR gap 0.828 -> 0.076; DI ratio 0.093 -> 0.739.
Overall after mitigation: recall 0.719, precision 0.325, flag rate 0.454.
Fairlearn ThresholdOptimizer comparison: TPR gap 0.081, recall 0.901, flag rate 0.618.

## Data bias carried forward from Module 3

- Module 3 flag: has_disability 1 — under-represented (share=0.0201)
