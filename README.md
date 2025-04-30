# Credit Risk Modelling: IFRS 9 & Basel Framework Implementation

This project outlines the implementation of credit risk modelling components under the IFRS 9 and Basel frameworks. The focus is on estimating Expected Loss (EL) through key components: Probability of Default (PD), Exposure at Default (EAD), and Loss Given Default (LGD). The process includes detailed data preprocessing, feature engineering, model application, and estimation.

---

##  Background: Role of EL in Basel & IFRS 9

**Expected Loss (EL)** represents the anticipated loss from credit risk over a given time horizon and is central to risk management and accounting standards. It is calculated using the formula:

**EL = PD × EAD × LGD**

- **Basel Framework**: EL forms the foundation of the Internal Ratings-Based (IRB) approach used by banks to calculate regulatory capital. Accurate estimates of PD, LGD, and EAD are essential to ensure capital adequacy and risk sensitivity.

- **IFRS 9**: Requires financial institutions to recognize expected credit losses (ECL) on financial assets. The ECL is derived from similar components as Basel, with additional considerations for forward-looking information and staging (12-month vs. lifetime expected loss).

---

##  Project Workflow Summary

### 1. Data Preprocessing
- Combined multiple datasets for PD, LGD, and EAD estimation.
- Encoded categorical variables into dummy variables.
- Removed reference categories to avoid multicollinearity.
- Structured feature sets based on economic and credit characteristics.
- Used chunked processing and memory-efficient handling for large dataset size.

### 2. LGD and EAD Modelling
- **Two-step regression approach**:
  - Step 1: Predict recovery rate using model 1.
  - Step 2: Adjust recovery using model 2.
- Final LGD computed as:  
  **LGD = 1 - (Recovery_step1 × Recovery_step2)**
- Predicted recovery values were clipped to [0, 1] for consistency.

### 3. PD Feature Processing
- Created feature sets from dummy variables (one-hot encoded).
- Removed reference categories to ensure statistical stability.
- Processed data in chunks to handle memory limitations.
- Output matrix used in downstream PD estimation.

### 4. Expected Loss Estimation
- Final expected loss estimated with:  
  **EL = PD × EAD × LGD**

---

## Note on PCA
While PCA was initially considered for dimensionality reduction, it was skipped due to:
- Memory limitations.
- Limited benefit of PCA when working with high-dimensional dummy variables.

---

## Summary
This project implements a scalable, modular pipeline for credit risk quantification under IFRS 9 and Basel standards. It emphasizes:

- Clean and efficient preprocessing.
- Structured modelling of EAD, LGD and PD.
- Practical design choices suitable for real-world financial datasets.

The result supports integration of Expected Loss into both regulatory capital calculation and financial reporting.
