# Model Validation Report: Statistical LGD Engine

**Model Name:** LGD XGBoost Regressor
**Version:** 1.0
**Status:** Approved

## 1. Executive Summary
This model predicts the Loss Given Default (LGD) for defaulted loans to estimate the severity of credit losses. The model achieved an R-squared of 0.2245.

## 2. Data Integrity & Experiments
A major target leakage issue was identified and resolved (dropped `lgd_time`). The bimodal nature of the target was stabilized using Winsorization after IQR Capping and Conditional Modeling failed to yield usable results.

## 3. Performance
*   **Algorithm:** XGBoost Regressor.
*   **R-Squared:** 0.2245
*   **Key Drivers:** Loan-to-Value (LTV) is the dominant predictor of loss severity.

## 4. Relationship to the Mortgage Engine
While this model provides a robust statistical baseline, it is important to note that in production IFRS 9 engines, this base LGD is often overlaid with macroeconomic adjustments (e.g., HPI floors). In our Freddie-Mac Engine, we applied a dynamic LGD overlay (20% base, rising to 30% if HPI falls >5%) to account for systemic shocks.

## 5. Limitations
*   **Limited Feature Set:** The model uses LTV and Purpose. Production models should include workout costs and recovery timelines.

---
**Sign-off:** Raymond Sibanda
