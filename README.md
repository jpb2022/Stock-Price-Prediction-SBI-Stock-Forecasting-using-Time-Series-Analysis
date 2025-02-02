
# Stock Price Prediction using ARIMA
This project demonstrates how to predict stock prices using the ARIMA (AutoRegressive Integrated Moving Average) model. The analysis is performed on historical stock price data, with multiple ARIMA model configurations being evaluated for prediction accuracy.

## Table of Contents
Introduction
Requirements
Data
Model
Evaluation
Results
Usage
License
## Introduction
Stock price prediction is a critical application in financial analytics, and the ARIMA model provides a popular approach to time series forecasting. This project leverages ARIMA models of different configurations to forecast the closing stock prices for a given company over a period of time. The goal is to determine the most accurate ARIMA configuration for the task by comparing different models' performance.

## Requirements
The following libraries are required for running the code:

pandas
numpy
matplotlib
statsmodels

### You can install them using the following command:

bash
Copy
Edit
pip install pandas numpy matplotlib statsmodels
## Data
The dataset consists of historical stock price data, with the primary column being the "Close" price, which represents the closing price of the stock at each trading session. The dataset is divided into two parts:

Training Data: Used to fit the ARIMA model.
Validation Data: Used to evaluate the predictions made by the model.
Data Format
### The dataset has the following structure:

Date: Date of the stock price data (as an index).
Close: Closing price of the stock.
## Model
### In this project, we explore multiple ARIMA configurations to predict stock prices:

ARIMA(1,1,1): A basic ARIMA model with 1 lag for AR, differencing order 1, and 1 lag for MA.
ARIMA(0,3,3): An ARIMA model with 0 AR lags, 3 orders of differencing, and 3 MA lags.
ARIMA(2,1,1): ARIMA model with 2 AR lags, 1 order of differencing, and 1 MA lag.
ARIMA(2,1,2): ARIMA model with 2 AR lags, 1 order of differencing, and 2 MA lags.
ARIMA(3,1,1): ARIMA model with 3 AR lags, 1 order of differencing, and 1 MA lag.
Each configuration is evaluated by calculating the Mean Squared Error (MSE) between the predicted and actual values in the validation dataset.

## Evaluation
After fitting the ARIMA model, the prediction is made for the closing prices over a specified range (from index 1050 to 1094 in this case). The accuracy of each model is evaluated using the Mean Squared Error (MSE). Lower MSE indicates better prediction performance.

### Example Model Configuration
from statsmodels.tsa.arima.model import ARIMA

# Fit the ARIMA model
model = ARIMA(train_df['Close'], order=(1, 1, 1))
model_fit = model.fit()

# Make prediction
yhat = model_fit.predict(1050, 1094, typ='levels')
print(yhat)
Results
## The MSE for different ARIMA models is calculated as follows:

ARIMA(1,1,1): MSE = 2017.77
ARIMA(2,1,1): MSE = 1931.36
ARIMA(2,1,2): MSE = 1944.12
ARIMA(3,1,1): MSE = 1944.12
In the plots, the actual closing prices from the validation data are compared with the predicted values from the ARIMA model.


License
This project is licensed under the MIT License - see the LICENSE file for details.
