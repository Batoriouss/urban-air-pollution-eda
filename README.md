# Urban Air Pollution Challenge — EDA & Regression

Exploratory data analysis and a baseline regression model based on the [Zindi — Urban Air Pollution Challenge](https://zindi.africa/competitions/zindiweekendz-learning-urban-air-pollution-challenge): predicting daily PM2.5 air pollution levels across multiple cities using weather data and Sentinel 5P satellite readings (NO2, O3, CO, HCHO, SO2, CH4, cloud and aerosol data).

## Task
Predict PM2.5 particulate matter concentration (a regression problem) from 67 numeric features combining ground weather data and satellite-derived atmospheric measurements.

## Key findings
- **Missing data**: satellite features have varying levels of missingness — from ~1% (O3) up to **81% for CH4**, which was dropped entirely rather than imputed.
- **Target distribution** is strongly right-skewed (mean 61.1, median 50, max 815) — a log transform produces a much more symmetric distribution.
- **Correlations with target are moderate** at best: the strongest real predictor is CO column density (r = 0.38), followed by HCHO and NO2 measurements. No single feature dominates — weather features alone show weak correlation with PM2.5.
- **Data quality issue identified**: a single monitoring station (`426FKUG`) repeatedly reported implausible readings — a sensor "floor" of 1.0 with very few daily readings early in the period, later producing isolated extreme spikes (PM2.5 = 815) that account for the dataset's main outliers.

## Models
| Model | Validation RMSE |
|---|---|
| Linear Regression (baseline) | 37.42 |
| Random Forest (100 trees) | 30.36 |

Random Forest submission scored **34.58 RMSE** on Zindi's public leaderboard.

## Tools
Python, pandas, matplotlib, numpy, scikit-learn

## Files
- `eda_urban_air_pollution.ipynb` — full analysis: EDA, missing data handling, outlier investigation, correlation analysis, and model comparison
