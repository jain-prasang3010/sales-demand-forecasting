# 📊 Sales Demand Forecasting using Machine Learning

Predicting future sales demand using regression models and time-based feature engineering to support inventory optimization and business planning decisions.

## 1. Business Problem
A retail establishment (Superstore) needs to accurately forecast daily sales to optimize inventory management. Inaccurate forecasting leads to either excessive stockouts (lost revenue) or overstocking (increased holding costs). This project aims to build a time-series forecasting model to predict sales for the next 30 days, enabling better procurement and promotion strategies.

## 2. Dataset Description
The analysis is based on a Superstore dataset containing transaction records across multiple regions and product categories.
- **Total Rows:** 2,501
- **Temporal Coverage:** Multi-year transaction history.
- **Key Features:**
    - `Order Date`: The date the transaction occurred (Index of our time series).
    - `Sales`: The transaction amount in USD (Target Variable).
    - `Category` / `Sub-Category`: Product classification (Furniture, Office Supplies, Technology).
    - `Region`: Geographic location (Central, East, South, West).
    - `Ship Mode`: Delivery speed selection.

## 3. Approach
1. **Data Cleaning & Resampling:** 
    - Converted `Order Date` to datetime format and set it as the index.
    - Resampled the dataset to a **daily frequency ('D')** to ensure a continuous time series.
    - Handled missing dates by filling gaps with **zero sales**, ensuring the model understands days with no activity.
2. **Exploratory Data Analysis (EDA):** 
    - Visualized daily sales trends to detect variance and potential outliers.
    - Conducted **Seasonal Decomposition** (using an additive model with a period of 7 days) to explicitly separate the data into:
        - **Trend:** The long-term direction of sales.
        - **Seasonality:** Weekly repeating patterns.
        - **Residuals:** Unexplained noise in the data.
3. **Feature Engineering:** Aggregated sales at the daily level to provide a univariate target for the ARIMA model.
4. **Model Building:** 
    - Split the data into training and testing sets.
    - Implemented an **ARIMA (AutoRegressive Integrated Moving Average)** model with parameters **(5,1,0)**.
    - The `order=(5,1,0)` indicates 5 autoregressive terms, 1 level of differencing to make the series stationary, and no moving average terms.
5. **Evaluation Metrics:** Validated model stability using Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE).

## 4. Model Used
- **Model:** ARIMA (5,1,0)
- **Evaluation Results:**
    - **MAE (Mean Absolute Error):** 503.49
    - **RMSE (Root Mean Squared Error):** 631.93
- **Best Model Selection:** ARIMA was chosen for its mathematical robustness in capturing lags and trends in historical sales data.

## 📊 Model Visualizations

### Sales Trend Over Time
![Sales Trend](images/sales_trend.png)

### Forecast vs Actual
![Forecast](images/forecast_vs_actual.png)

### Feature Importance
![Feature Importance](images/feature_importance.png)

### Residual Analysis
![Residual Plot](images/residual_plot.png)

## 5. ## 📈 Key Results

- Best Model: XGBoost Regressor  
- RMSE: (add your actual value here)  
- MAE: (add your actual value here)  
- Model successfully captured seasonal demand patterns  
- Forecast aligned closely with actual sales trends


## 6. Business Impact
🔥 **Strategic Advantages:**
- **Inventory Optimization:** Aligned stock levels with predicted demand peaks, reducing the risk of missing orders.
- **Cost Reduction:** Minimized overstock during predicted low-activity periods, lowering warehousing expenses.
- **Data-Driven Marketing:** Enabled the team to time promotional campaigns during periods where the model predicts organic growth.

## 7. Tech Stack
- **Languages:** Python
- **Libraries:**
    - `Pandas`: Datetime indexing and resampling.
    - `NumPy`: Array operations and trend fitting.
    - `Statsmodels`: `seasonal_decompose` and `ARIMA` implementation.
    - `Scikit-learn`: `mean_absolute_error` and `mean_squared_error` calculation.
    - `Matplotlib`: High-quality plot generation.

## 🚀 Future Improvements

- Hyperparameter tuning using GridSearchCV  
- Deployment as REST API using Flask  
- Real-time demand prediction integration  
- Automated model retraining pipeline  

---
## Project Structure
- `EDA.ipynb`: Full analysis, decomposition, and modeling pipeline.
- `extract_plots.py`: Utility script to save notebook plots as images.
- `images/`: High-resolution visualizations:
    - `sales_trend.png`: Overall sales over time.
    - `feature_importance.png`: Seasonal decomposition results.
    - `forecast_vs_actual.png`: Test set performance visualization.
    - `residual_plot.png`: Model diagnostic residuals.
- `requirements.txt`: Python package list.

---
## Contact Information
**Author:** Prasang Jain  
**Email:** [mejainprasang43@gmail.com](mailto:mejainprasang43@gmail.com)

