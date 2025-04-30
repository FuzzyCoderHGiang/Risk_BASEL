# Credit Risk Modelling: IFRS 9 & Basel Framework Implementation

This project outlines the implementation of credit risk modelling components under the IFRS 9 and Basel frameworks. The focus is on estimating Expected Loss (EL) through key components: Probability of Default (PD), Exposure at Default (EAD), and Loss Given Default (LGD). The process includes detailed data preprocessing, feature engineering, model application, and estimation.

---

## 📘 Background: Role of EL in Basel & IFRS 9

**Expected Loss (EL)** represents the anticipated loss from credit risk over a given time horizon and is central to risk management and accounting standards. It is calculated using the formula:

$$
\text{EL} = \text{PD} \times \text{EAD} \times \text{LGD}
$$

- **Basel Framework**: EL forms the foundation of the Internal Ratings-Based (IRB) approach used by banks to calculate regulatory capital. Accurate estimates of PD, LGD, and EAD are essential to ensure capital adequacy and risk sensitivity.

- **IFRS 9**: Requires financial institutions to recognize expected credit losses (ECL) on financial assets. The ECL is derived from similar components as Basel, with additional considerations for forward-looking information and staging (12-month vs. lifetime expected loss).

---

## 🔄 Project Workflow Summary

### 1. **Data Preprocessing**
- Combined multiple datasets for PD, LGD, and EAD estimation.
- Encoded categorical variables into dummy variables.
- Removed reference categories to avoid multicollinearity.
- Structured feature sets based on economic and credit characteristics.
- Chunked processing and memory-efficient handling due to large dataset size.

### 2. **LGD Modelling**
- **Two-step regression** approach:
  - Step 1: Predict recovery rate using model 1.
  - Step 2: Adjust recovery using model 2.
- Final LGD computed as:
  $$
  \text{LGD} = 1 - (\text{Recovery}_{\text{step1}} \times \text{Recovery}_{\text{step2}})
  $$
- Clipped predicted recovery values to [0, 1] to ensure validity.

### 3. **PD Feature Processing**
- Built a list of selected and reference features for dummy encoding.
- Removed reference categories to ensure statistical stability.
- Processed in chunks to avoid memory overflow.
- Feature matrix constructed for downstream use in PD models.

### 4. **Expected Loss Estimation**
- Final expected loss estimated with:
  $$
  \text{EL} = \text{PD} \times \text{EAD} \times \text{LGD}
  $$

---

## ⚠️ Note on PCA
While PCA was considered to reduce dimensionality, it was skipped due to memory constraints and because dummy variables often do not benefit from PCA in a credit risk context.

---

## 📌 Summary
This project reflects a full pipeline for estimating expected loss under real-world banking standards. It emphasizes:
- Clean preprocessing.
- Modular modelling of LGD and PD.
- Scalable design in line with IFRS 9 and Basel standards.

The methodology enables financial institutions to embed credit risk estimates into both regulatory reporting and internal risk management frameworks.

