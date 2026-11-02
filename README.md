# Step 5: README.md Project Report

## a. Problem Statement
The objective of this project is to build an end-to-end predictive and diagnostic machine learning pipeline to identify at-risk telecommunication subscribers and forecast customer churn. By training and evaluating both parametric and non-parametric classifiers, the system isolates high-friction service configurations, pricing sensitivities, and usage thresholds to allow proactive retention strategies.

## b. Dataset Description
The dataset contains telecom customer profiles tracking demographic characteristics, service plans (Internet type, Online Security, Streaming engagement), contract structures (Month-to-month, One-year, Two-year), tenure lifecycle months, and transactional variables (Monthly Charges, Total Charges). It consists of over 500 instances and more than 12 independent attributes, providing a robust operational footprint for classification tasks.

## c. Github Repository Link
**Repository Link:** [https://github.com](https://github.com)  

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

| ML Model Name | Observation about model performance |
| :--- | :--- |
| **Logistic Regression** | **The Baseline Standard.** This model looks for smooth, steady trends like a straight line. In our data, it perfectly proved that the higher a customer's monthly bill is, the more likely they are to leave. It creates a very stable prediction boundary because it isn't distracted by individual weird anomalies in the data, making it great for spotting high-paying users who are about to quit. |
| **Decision Tree** | **The Overfitted Rule-Maker.** This model works like a strict flow-chart. Because it tried to make perfect, hyper-specific rules for every single customer in the training set, it got completely confused when we tested it on new data. It proves that customer behavior is too complex to split using rigid, exact numeric cutoffs. |
| **KNN** | **The Group-Finder (Neighborhood Lookups).** KNN looks at a new customer and matches them with the 5 closest similar profiles. Standard KNN failed because it couldn't calculate the 'distance' between text categories like 'Contract Type'. Implementing Gower's Matrix fixed this, allowing it to group similar users together. However, because we have way more loyal customers than churning ones, the loyal 'neighbors' often outvoted and hid the true churning users at the borders, leaving its Recall capped. |
| **Naive Bayes** | **The Probability Champion.** Instead of measuring geometric distances, this model uses pure percentage odds. It assumes every feature acts independently to multiply the final risk score. Because it focuses on structural percentages rather than spatial lines, it easily handled our imbalanced data and caught the highest number of actual churning accounts (Highest Recall), proving that being on a Month-to-Month contract is the single biggest statistical trigger for leaving. |
| **Support Vector Machine** | **The Margin Maximizer.** This model tries to draw a wide, safe highway boundary separating loyal users from churning users. It performed beautifully because our feature engineering simplified the map for it: once we smoothed out the massive 'Total Charges' spikes using log math and grouped 'Tenure' into clear yearly milestones, the model easily separated the high-risk users from the loyal ones. |
| **Overall, Winner for your dataset?** | **Naive Bayes** is selected as the final production winning architecture, securing an outstanding validation F1-Score of **0.6157**.<br><br><em>Critical Rationale:</em> Churn telemetry is heavily class-imbalanced, which causes geometric boundary models to get dragged toward the dominant class. Naive Bayes completely bypasses this issue by using pure conditional percentage odds instead of geometric spatial lines. This structural focus allows it to isolate high-risk transactional milestones—such as Month-to-Month contracts—and maximize our capacity to catch actual at-risk accounts, delivering the highest overall model <strong>Recall</strong> performance profile across our experiments. |
