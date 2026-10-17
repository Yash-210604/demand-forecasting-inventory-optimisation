# Demand Forecasting and Inventory Optimisation

## Overview
This project develops a machine-learning prototype for forecasting daily retail demand and estimating an inventory reorder point using historical sales data from the UCI Online Retail dataset.

## Objectives
- Clean and aggregate transaction data into daily demand.
- Engineer lag-based and calendar-based forecasting features.
- Compare machine-learning models against a moving-average baseline.
- Estimate lead-time demand, safety stock, and an illustrative reorder point.

## Dataset and Processing
The UCI Online Retail dataset contains transaction records from 2010–2011. The analysis filters for UK transactions, excludes cancelled invoices, and removes non-positive quantities and unit prices. Quantity sold is aggregated by calendar day, including zero-demand days.

## Methodology
1. Data cleaning and daily demand aggregation.
2. Feature engineering using previous-day, previous-week, and previous-fortnight demand, rolling averages, and calendar variables.
3. Chronological 80/20 train-test split.
4. Comparison of a seven-day average baseline, Random Forest, and Gradient Boosting.
5. Illustrative inventory planning using a three-day lead time and an assumed 95% one-sided service-level factor.

## Forecasting Results

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Random Forest | 6,474.29 | 9,969.75 | 0.46 |
| Gradient Boosting | 7,818.77 | 10,615.40 | 0.39 |
| Seven-day average baseline | 9,175.57 | 13,097.21 | 0.07 |

Random Forest achieved the lowest MAE among the tested models. Its most important feature was demand from seven days earlier (`Lag_7`), with an importance score of 0.4169.

## Inventory Planning Prototype
- Assumed replenishment lead time: 3 days
- Estimated lead-time demand: approximately 56,839 items
- Estimated safety stock: approximately 28,151 items
- Illustrative reorder point: approximately 84,990 items

These estimates are based on aggregate demand and a simplified forecast-error assumption. They are not operational SKU-level recommendations.

## Limitations
- The dataset covers a limited historical period.
- The model forecasts aggregate UK item quantities rather than individual products.
- The test period includes sharp demand spikes that the model does not fully capture.
- The inventory calculation assumes a fixed lead time and simplified forecast-error behaviour.
- Forecast accuracy and inventory service levels would require further validation before operational use.

## Tools
Python, pandas, NumPy, scikit-learn, Matplotlib, Google Colab.

## Future Improvements
- Develop SKU-level demand forecasts.
- Evaluate rolling-origin time-series validation.
- Compare seasonal-naive and additional forecasting models.
- Simulate inventory costs, stockouts, and service levels using historical demand.

