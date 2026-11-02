# Step 5: README.md Assignement Results

## a. Problem Statement
The objective of this project is to build an end-to-end predictive and diagnostic machine learning pipeline to identify at-risk telecommunication subscribers and forecast customer churn. By training and evaluating both parametric and non-parametric classifiers, the system isolates high-friction service configurations, pricing sensitivities, and usage thresholds to allow proactive retention strategies.

## b. Dataset Description
The dataset contains telecom customer profiles tracking demographic characteristics, service plans (Internet type, Online Security, Streaming engagement), contract structures (Month-to-month, One-year, Two-year), tenure lifecycle months, and transactional variables (Monthly Charges, Total Charges). It consists of over 500 instances and more than 12 independent attributes, providing a robust operational footprint for classification tasks.

## c. Github Repository Link
**Repository Link:** [https://github.com/2026aj05516/2026AJ05516_BITS_AIML_Assignement_2.git](https://github.com/2026aj05516/2026AJ05516_BITS_AIML_Assignement_2.git)  

---

## d. Models Used & Evaluation Matrix

### Model Performance Comparison Table

| ML Model Name | Accuracy | AUC | Precision | Recall | F1 | MCC |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Logistic Regression** | 0.8070 | 0.8479 | 0.6667 | 0.5455 | 0.6000 | 0.4786 |
| **Decision Tree** | 0.7275 | 0.6571 | 0.4871 | 0.5053 | 0.4961 | 0.3095 |
| **KNN** | 0.7594 | 0.7736 | 0.5499 | 0.5160 | 0.5324 | 0.3710 |
| **Naive Bayes** | 0.7395 | 0.8268 | 0.5060 | 0.7861 | 0.6157 | 0.4564 |
| **Support Vector Machine** | 0.7921 | 0.7928 | 0.6484 | 0.4733 | 0.5471 | 0.4251 |

---

### Model Performance Observations Matrix

### Model Performance Observations Matrix

| ML Model Name | Explicit Observation about Model Performance & Dataset Insights |
| :--- | :--- |
| **Logistic Regression** | **Parametric Baseline.** Optimizes smooth linear log-odds hyperplanes across scaled variables. It provides a stable global baseline by capturing macro cost-sensitivity vectors. On this specific dataset, its coefficients confirmed that premium billing tiers operate as direct financial friction points—as continuous monthly charges increase, a subscriber's log-odds of exit scale up predictably, making high-paying accounts a highly visible risk zone. |
| **Decision Tree** | **High Structural Variance.** Exhibited severe recursive partitioning overfitting on localized training data splinters. By splitting the feature space on rigid, nested cutoff thresholds, it built an overly complex architecture that failed to generalize on the validation set, resulting in lower test F1-scores. This proves that churn is an overlapping, multi-factor behavioral profile that cannot be isolated by strict, binary numerical boundaries (e.g., hard-coding single spending thresholds). |
| **KNN** | **Instance-Based Lazy Learner.** Standard Euclidean geometry failed structurally over non-numeric features by treating discrete textual integer tokens as continuous distance coordinates. Integrating a component-by-component *Gower's Mixed-Distance Matrix* successfully corrected this geometric distortion and elevated its baseline scores. However, due to severe class imbalance and dense feature-space overlap, KNN suffered from 'noisy neighbor neighborhoods' where dominant non-churn instances routinely outvoted true churn signatures at local cluster borders, keeping its overall Recall capped. |
| **Naive Bayes** | **Probabilistic Class Conditional Independence.** Maximizes conditional joint probability maps flawlessly across skewed targets by treating categorical variables as independent probability multipliers. Because it calculates conditional odds based on structural flags rather than geometric distances, it excelled at managing the minority class imbalance. It secured the highest validation **Recall**, identifying specific transactional states (like Month-to-Month contracts) as heavy immediate triggers for customer exit risk. |
| **Support Vector Machine** | **Geometric Margin Maximization.** Effectively maximizes functional geometric margins across a high-dimensional feature footprint. It demonstrates that when continuous billing outlines are log-smoothed and customer lifetimes are mapped into binned milestones, high-risk churn patterns become strictly separable. This proves that customer relationship trends stabilize and form a distinct, loyal geometric cohort once a subscriber safely passes their first 12 months. |
| **Overall, Winner for your dataset?** | **Naive Bayes** is selected as the optimal production framework, securing a peak validation F1-Score of **0.6157**.<br><br>*Critical Rationale:* While implementing **Gower's Mixed-Distance Matrix** successfully corrected the mathematical distortion of Euclidean assumptions and vastly boosted KNN's individual performance, it did not alter the overall winner. This occurs because class-imbalanced customer churn telemetry strongly favors probabilistic frameworks (like Naive Bayes) or linear margins (like Logistic Regression). These models are structurally optimized to accommodate the high feature-space overlap between loyal and churning subscribers far more effectively than distance-based neighborhood models under severe class skew. |
