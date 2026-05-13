# New York Rental Price Prediction Model

## Project Overview

This project studies whether historical rent trends can be used to predict future rental prices in New York City. Using Zillow Observed Rent Index (ZORI) data at the ZIP-code monthly level, I build predictive models to estimate next month’s rent index and analyze how rental prices vary across boroughs over time.

The project focuses on both prediction and interpretation. The main task is a supervised regression problem, while additional classification and time-series forecasting extensions are included to apply broader machine learning methods.

## Research Question

Can historical rent values, rent growth, time features, borough information, and a Long Island City indicator predict future rental prices in New York City?

## Dataset

The main dataset is the **Zillow Observed Rent Index (ZORI)** at the ZIP-code level.

Each observation represents:

```text
one ZIP code in one month
```

## Repository Structure

```
nyc-rental-price-prediction/
│
├── README.md
├── report.pdf
│
└── notebook

```

## Methods

### 1. Data Preparation

The original Zillow dataset is provided in wide format, with one row per ZIP code and monthly rent columns across time. I convert the data into long format so that each row represents a ZIP-code-month observation.

Main preprocessing steps:

  *  Filter data to NYC ZIP codes
  *  Map counties to boroughs
  *  Create a Long Island City indicator
  *  Convert monthly columns into a date column
  *  Create lagged rent features
  *  Create rent growth variables
  *  Create next-month rent as the prediction target

### 2. Exploratory Data Analysis

The EDA section explores:

  * NYC rent trends over time
  * Rent differences across boroughs
  * Long Island City rent trends
  * Rent growth patterns
  * Distribution of ZORI rent values

### 3. Regression Modeling

The main predictive task is to predict next month’s rent index.

Models used:

  * Dummy Regressor
  * Linear Regression
  * Ridge Regression
  * KNN Regression
  * Random Forest Regression

Evaluation metrics:

  * Mean Absolute Error
  * Root Mean Squared Error
  * R² score

### 4. Classification Extension

I also created a classification task to predict whether a ZIP-code-month will be classified as high-rent next month.

Models used:

  * Logistic Regression
  * KNN Classification

Evaluation metrics:

  * Accuracy
  * Precision
  * Recall
  * F1 score
  * Confusion matrix

### 5. Time-Series Forecasting Extension

Finally, I aggregate the data into an NYC average monthly rent series and apply time-series forecasting models.

Forecasting models used:
  
  * Naive Forecast
  * ARIMA
  * Exponential Smoothing

Evaluation metrics:

  * Mean Absolute Error
  * Root Mean Squared Error

## Key Findings
Historical rent values are the strongest predictors of future rent.

Linear Regression performs best among the regression models, with an average error of about $34 and an R² of about 0.998.

Logistic Regression performs best for the classification task, with an accuracy of about 96.8%.

Exponential Smoothing performs best in the forecasting extension, outperforming both ARIMA and the naive baseline.

The strong performance of simple linear models suggests that NYC rent trends are highly persistent and change gradually over time.

## Limitations

This project uses ZIP-code-level rent index data, not individual apartment listing data. Therefore, the model cannot capture apartment-level features such as:

  *  Bedrooms
  *  Bathrooms
  *  Square footage
  *  Amenities
  *  Building quality
  *  Exact address
  *  Floor level
  *  Subway distance

The results should be interpreted as predictions of aggregated rent trends, not predictions of individual apartment rents.

## Next Steps

Future work could improve the project by adding:

  *  Subway accessibility data
  *  Census income and demographic data
  *  New housing supply data
  *  Apartment-level rental listing data
  *  Separate models for each borough
  *  More detailed neighborhood-level analysis

## Author

This project is built by Tracy Chu and Lylian Li for Databootcamp.
