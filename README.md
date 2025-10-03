# MSDS-Financial-Engineering-Assignment-01
Predicting Ag Commodity Futures

### Objective
- As a drivetrain engineer for John Deere, I gained several insights into the highly cyclical nature of the agricultural heavy machinery sector. The cyclicality is typically influenced by various environmental factors such as global weather patterns, crop conditions, evolving diets, technological advancements, and commodity price fluctuations.

- Since this course presented me an opportunity to analyze any market, I wanted to understand the overall financial impact from price fluctuation of major commodities such as Corn, Soybeans, Cotton, and Wheat, and how it may impact revenue or product sales for companies in agricultural heavy machinery industry. My objective was to develop a machine learning model for predicting short-term price movements (upward, downward, or stable) using historical financial data of the futures for these commodities. The project focused on feature engineering, model building, and evaluation.

### Data
I used historical daily futures price data (open, high, low, close, volume) for the four commodities, sourced via Yahoo! Finance.
I also derived technical indicators for the commodities such as:
Lagged prices (1–3 days) — today’s price, price 2 days ago, and price 3 days ago
High–Low spreads (HML)
Open–Close spreads (OMC)
Exponential moving averages (2, 4, 8-day)
Trading volume lags

### Methodology
- Feature Selection
  - Evaluating features using wrapper methods (e.g., all-subsets, stepwise, or embedded feature importance from XGBoost/LightGBM).

Model Development
- Predicting binary (up/down) or ternary (up/stable/down) returns.
  - Starting with logistic regression for benchmarking.
  - Training tree-based ensemble models (XGBoost, LightGBM, Random Forest).
  - Using time-series cross-validation (rolling window).

Hyperparameter Tuning
- Optimizing with randomized/grid search.
- Evaluation
- ROC-AUC, accuracy, precision, recall, and confusion matrix.
- Comparing performance across commodities.

How to use this repository:
