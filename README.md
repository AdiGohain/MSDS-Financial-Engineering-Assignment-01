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

### Data Preparation, Pipeline & Programming
- I used historical daily futures price data between (200-2025) sourced using Yahoo! Finance for each of the four commodities. For each of the datasets, I created a pipeline for preprocessing and feature engineering by deriving the following features/indications:
  - Lagged prices for 1–3 days or today’s price, price 2 days ago, and price 3 days ago.
  - Similarly, tading volume lags for 1-3 days
  - Exponential moving averages using the lagged prices in order to mitigate leakage which acted as indicators for momentum.
  - Log returns, by calculating the natural log of relative prices which was used as a regresstion target as well as for classifying.
  - Binary targets where 1 indicated if the returns were positive while 0 indicated negative returns
- Notes
  - In terms of the programming process, I removed any null values that got created from the lagging process and standardized the data prior to training the models.
  - The analysis was primarily done using Python and I used the Polars and Pandas libraries to clean the data, transform tables, and compute the features. I also incorporated scikit-learn to preprocess, cross-valdate, and to perform logistical regression and derive evaluation metrics. Lastly, I used Matplotlib and Seaborn for creating time series vizualizations and heatmaps.

### Methodology
- Feature Selection
  - Evaluating features using wrapper methods (all-subsets, stepwise, or embedded feature importance from XGBoost).

- Model Development
  - Predicting binary (up/down) or ternary (up/stable/down) returns.
  - Starting with logistic regression for benchmarking.
  - Training tree-based ensemble models (XGBoost, Binary Logistic).
  - Using time-series cross-validation (rolling window).

- Hyperparameter Tuning
  - Optimizing with randomized/grid search.
  - Evaluation
  - ROC-AUC, accuracy, precision, recall, and confusion matrix.
  - Comparing performance across commodities.

### How to use this repository:
- First download Gohain_Programming_Assignment_01.ipynb
  - Upon running this file in jupyter notebook, the code will first download historical data for the commodities from yahoo finance and save it into a newly created folder called historical_data
  - The code will then re import each csv file per commodity from historical_data, and begin cleaning and processing the files for ML by computing lag price features, HML, OMC, volume lag metrics, and a target.
  - The processed files will be saved in a newly created folder called processed_data
- Next, download each of the {commodity}_futures_ML.ipbyn files and save them into the processed_data folder.
  - Each of the ipbyn files has the same code with the only difference being that they pull their own commodity processed_data csv file. Also training data for each commodiity individually is less processor intensive compared to training data for all commodities together under a for loop.  
