# 🚀 Machine Learning Project: Travel Product Subscription Prediction

## 🎯 Project Goal
The primary objective of this project is to analyze customer data for a travel product and develop a robust classification model capable of predicting whether a client is likely to **subscribe to the product** (`ProdTaken`). The project emphasizes rigorous MLOps pipeline practices and effective handling of class imbalance.

## 🛠️ Technical Stack and Libraries
| Component | Tool / Library |
| :--- | :--- |
| **Language** | Python 3.x |
| **Analysis** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **Modeling** | Scikit-learn (SVC, RF, DT, AdaBoost) |
| **Optimization** | RandomizedSearchCV, ColumnTransformer |

---

## 🗺️ Modeling Pipeline (Key Steps)

### 1. 🔍 Exploratory Data Analysis & Data Preparation

* **Cleaning & Imputation:**
    * Correction of textual inconsistencies ('Fe Male' → 'Female', 'Unmarried' → 'Single').
    * Strategic Imputation: **Median** for numerical variables sensitive to outliers, **Mode** for categorical variables.
* **Feature Engineering:** Creation of key informative variables to boost predictive power: `Income_Per_Person`, `Engagement_Score`, `Total_visiting`, etc.
* **Correlation:** Analysis via Heatmap to identify and manage multicollinearity.

### 2. 🛡️ Imbalance Handling and Preprocessing

* **Imbalance:** The target variable (`ProdTaken`) shows significant class imbalance.
* **Stratified Split:** Data was divided into training and testing sets (80/20) using **stratification** to maintain class proportion consistency.
* **Preprocessing Pipeline:** A `ColumnTransformer` was implemented to ensure zero *Data Leakage*:
    * **Numerical:** `StandardScaler` (Normalization).
    * **Categorical:** `OneHotEncoder`.

### 3. ⚖️ Training, Evaluation & Optimization

* **Initial Evaluation:** Multiple classification models were assessed (Logistic Regression, SVC, RF, DT, AdaBoost).
    * **Key Metric:** The **weighted F1-score** was chosen as the primary metric due to class imbalance.
* **Hyperparameter Tuning:** The best-performing models (Random Forest and Decision Tree) were selected for optimization.
    * Used `RandomizedSearchCV` for **time-efficient** yet effective hyperparameter search.

### 4. 📈 Results and Final Analysis

| Optimized Model | Optimization Metric | **Final F1-Score (Test)** | **Ranking** |
| :--- | :--- | :--- | :--- |
| **Optimized Random Forest** | F1-Score (CV): ~0.78 | **[Final Score Obtained]** | 🥇 Best Model |
| Optimized Decision Tree | F1-Score (CV): ~0.68 | [Final Score Obtained] | 🥈 Second Best |

---

## 💡 Interpretability and Conclusion

* **Best Model:** The **Optimized Random Forest** demonstrated the strongest generalization capability.
* **Feature Importance Analysis:**
    * This step identified the variables that have the most significant impact on the subscription decision (e.g., `MonthlyIncome`, `Passport`, `Engagement_Score`). This information is directly actionable for the marketing team.
* **ROC/AUC Evaluation:** In-depth analysis was performed using the **ROC Curve** and the **AUC Score** to confirm the model's robustness independent of the classification threshold.

> **Conclusion:** The pipeline successfully produced a robust Random Forest model capable of predicting subscription with high reliability, providing clear actionable insights for customer engagement.
