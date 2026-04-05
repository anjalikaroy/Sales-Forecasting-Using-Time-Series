# Sales Forecasting Using Time Series

## Problem Statement
Accurate sales forecasting is important for retail businesses to manage inventory, optimize promotions, and improve operational planning. This project focuses on forecasting store sales using historical Rossmann retail data through time series analysis.

## Objective
To build a forecasting model that predicts future sales using historical sales data, customer counts, promotions, holidays, and store-related information.


## Dataset
This project uses two datasets:

- `train.csv` – historical daily store sales data
- `store.csv` – store-level information such as store type, assortment, promotions, and competition details

Both datasets were merged to create a unified dataset for analysis and forecasting.


## Approach
- Data loading and merging of `train.csv` and `store.csv`
- Missing value analysis and imputation
- Univariate, bivariate, and multivariate exploratory data analysis
- Outlier treatment for variables such as `CompetitionDistance`
- Feature engineering using date-based and store-based variables
- Time series analysis on sales and customer data
- Granger causality testing between sales and customers
- Stationarity testing using the Augmented Dickey-Fuller (ADF) test
- Autocorrelation and partial autocorrelation analysis
- Train-test split for forecasting the next 42 days
- Model building using:
  - VAR (Vector AutoRegression)
  - VARMAX (Vector AutoRegression Moving Average with exogenous variables)


## Tech Stack
- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Statsmodels


## Key Analysis Highlights
- Sales and customer count show a strong positive relationship
- Promotions have a significant impact on sales
- Weekday patterns influence both sales and customer traffic
- Competition-related variables show relatively limited direct correlation with sales
- Customer count was treated as an endogenous variable because it is strongly related to sales
- Promo and school holiday variables were used as exogenous inputs in forecasting

## Modeling
Two forecasting models were implemented:

### 1. VAR Model
Used to model the relationship between:
- Sales
- Customers

### 2. VARMAX Model
Extended the VAR approach by incorporating exogenous variables such as:
- Promo
- SchoolHoliday
- DayOfWeek dummy variables


## Results
The forecasting models were evaluated on the final 42 days of data.

### VAR
- RMSE (Sales): 0.05
- MAPE (Sales): 19.37
- RMSE (Customers): 0.03
- MAPE (Customers): 9.10

### VARMAX
- RMSE (Sales): 0.05
- MAPE (Sales): 9.48
- RMSE (Customers): 0.03
- MAPE (Customers): 8.33

VARMAX performed better than VAR in terms of sales forecasting error, especially on MAPE.

## Outcome
Built and compared multivariate time series forecasting models for retail sales prediction. The final results show that incorporating exogenous variables improves forecasting performance.

## Business Impact
This project can help retail businesses:
- Forecast short-term sales more accurately
- Improve inventory and staffing decisions
- Understand the effect of promotions and holidays on demand
- Support data-driven planning at the store level


## Future Improvements
- Forecast at individual store level instead of aggregated level
- Try SARIMAX, Prophet, and LSTM-based forecasting models
- Perform hyperparameter tuning for VARMAX
- Include additional external variables such as holidays, seasonality flags, or macroeconomic trends
- Deploy the forecasting pipeline as an interactive dashboard or web app


## Project Structure
```text
sales-forecasting-time-series.ipynb
README.md
train.csv
store.csv
