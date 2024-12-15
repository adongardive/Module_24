# Credit Risk Prediction for Counterparties in Commodity Trading

## Overview
This project focuses on predicting counterparty credit risk in commodity trading using machine learning models. By leveraging financial, rating, and exposure metrics, we aim to build a predictive model that provides actionable insights for minimizing financial losses and optimizing trading decisions.

---

## Problem Statement
Credit risk management is vital in the commodity trading sector due to the significant transaction values and market volatility. Failure to assess counterparty creditworthiness accurately can lead to severe financial losses and regulatory repercussions. This project addresses the question: **How can we predict counterparty credit risk to safeguard financial stability and make data-driven decisions?**

---

## Objectives
- Build a machine learning model to predict counterparty **Internal Ratings** (1-10), representing their creditworthiness.
- Identify the most important features contributing to credit risk.
- Provide actionable business insights to optimize trading volumes and mitigate risk.

---

## Dataset
### Source
The dataset (`enriched_financials_data.csv`) was curated by combining public financial data, ratings from external agencies, and simulated trading exposure data.

### Structure
- **Rows**: 2029 counterparties.
- **Columns**: 36 features, including:
  - **Financial Ratios**: Current Ratio, Debt Ratio, Net Profit Margin, etc.
  - **Exposure Metrics**: Current Exposure, Long-Term Exposure.
  - **Ratings**: Internal Rating (target variable), External Ratings (e.g., Moody’s).

### Preprocessing
- Missing values were imputed for numeric features using the median.
- Categorical features were encoded using one-hot encoding.
- Numerical features were scaled using `StandardScaler`.

---

## Approach
This project followed the CRISP-DM methodology:
1. **Business Understanding**: Identified credit risk as a key problem in commodity trading.
2. **Data Understanding**: Explored feature distributions, correlations, and sectoral patterns.
3. **Data Preparation**: Preprocessed data to handle missing values, outliers, and scaling.
4. **Modeling**: Trained baseline and advanced models, evaluated using cross-validation.
5. **Evaluation**: Selected the best-performing model and analyzed its feature importance.

---

## Modeling
### Baseline Models
We tested multiple models to predict **Internal Ratings**:
- **Linear Regression**: A baseline approach, but unsuitable due to the non-linear nature of the data.
- **Random Forest**: Strong performance with non-linear relationships.
- **XGBoost**: Robust handling of feature interactions and noise.
- **Gradient Boosted Trees**: Achieved the best performance in cross-validation.
- **Support Vector Regression**: Moderate performance but less scalable.

### Final Model Selection
After hyperparameter tuning, **Gradient Boosted Trees** emerged as the best model:
- **MSE**: 0.1926
- **R²**: 0.9750

### Feature Importance
The top predictors of creditworthiness included:
1. **External_Rating_Numeric**: Alignment with external credit ratings.
2. **Current_Exposure**: Reflects the risk associated with counterparty exposure.
3. **Current Ratio**: Indicates liquidity and financial stability.

---

## Results
### Key Findings
1. **High-Risk Entities**:
   - Counterparties with high **Debt Ratios** and low **External Ratings** were flagged as high-risk.
2. **Sector Insights**:
   - Stable sectors like **Energy** and **Basic Industries** scored higher on average.
   - Riskier sectors like **Technology** and **Consumer Services** require closer scrutiny.

### Model Performance
| **Model**                 | **R² (CV)** | **MSE (Test)** | **R² (Test)** |
|---------------------------|-------------|----------------|---------------|
| **Linear Regression**     | -1355754.97 | 333728.85      | -43231.14     |
| **Random Forest**         | 0.9646      | 0.2795         | 0.9638        |
| **XGBoost**               | 0.9730      | 0.2203         | 0.9715        |
| **Gradient Boosted Trees**| **0.9743**  | **0.1926**     | **0.9750**    |

---

## Business Insights
### Actionable Recommendations
1. **Proactively Manage High-Risk Counterparties**:
   - Increase due diligence on entities with low predicted ratings.
   - Adjust exposure limits for high-risk counterparties.
2. **Sector Focus**:
   - Expand partnerships in stable sectors (e.g., Energy).
   - Implement stricter credit controls for sectors with higher volatility (e.g., Technology).
3. **Leverage Feature Insights**:
   - Monitor liquidity metrics (e.g., Current Ratio) as leading indicators of risk.
   - Use exposure metrics to prioritize resource allocation.

---

### How to Use
1. Clone this repository.
2. Install the required libraries manually:
   ```bash
   pip install numpy pandas matplotlib seaborn scikit-learn xgboost joblib
3. Run the Jupyter Notebooks in the following order:
   - `24.1_1_Data_Understanding_and_Preprocessing.ipynb`
   - `24.1_2_Baseline_Modeling_and_Selection.ipynb`
   - `24.1_3_Hyperparameter_Tuning_and_Insights.ipynb`


##### **Contact and Further Information**

For additional information or collaboration opportunities, please contact Amit Dongardive at amit.dongardive@gmail.com.
