# Nifty50-intraday-ml-project
Machine Learning project for predicting next-minute NIFTY50 price direction using intraday OHLCV data. Includes preprocessing, feature engineering, multiple ML models (Logistic Regression, Random Forest, XGBoost), Buy/Sell signal generation, and PnL computation based on assignment rules.
 

## 1. Project Overview

I used 1-minute data to build a binary classifier:

- **1 → next candle close higher**  
- **0 → next candle close lower/same**

Predictions were converted to:

- **BUY → subtract close**  
- **SELL → add close**


## 2. Setup Instructions

pip install pandas numpy scikit-learn xgboost matplotlib

I used **Google Colab** for execution 

 ## 3. Feature Engineering

I created the following features:

 **a.Basic Features**

range (high − low)

body (close − open)

Momentum

ret_1, ret_2, ret_3

Trend

ma_5, ma_15

Volatility

vol_5, vol_15

Direction Flag

dir_1 (previous return > 0)

**b.Technical Indicator**

**RSI** (14-period)

Removed Features

I experimented with **MACD**, but removed them because they introduced noise and hurt model stability.

## 4. Models Trained

Logistic Regression (with StandardScaler)

Random Forest

XGBoost

Evaluated using accuracy, precision, recall.

## 5. Model Performance
Model	Accuracy
Logistic Regression	0.5087
Random Forest	0.5058
XGBoost	0.5033

## 6. Best Model 

**Logistic Regression performed the best, achieving the highest accuracy.**
It behaved more consistently on noisy intraday data, while tree-based models fluctuated more.
I selected Logistic Regression for generating final Buy/Sell signals and PnL.

**Note**
Even though Logistic Regression was only slightly better than the other models, this small improvement is meaningful because intraday price movement is extremely noisy and hard to predict. In high-frequency scenarios, even small gains in classification stability are valuable. I think the accuracy values in this project are also normal for 1-minute data, so the results are realistic and expected.


## 7. Buy/Sell Signals & PnL
BUY  = 34,980  
SELL = 28,809


**Because BUY subtracts the close price, more BUYs result in a negative PnL.**

Final Cumulative PnL:

-151,193,834.45

(This is fine due to the assignment's PnL logic.)

## 8. Output Table Includes

Timestamp

Close

Prediction

Buy/Sell Call

PnL Step

Cumulative PnL

## 9. Conclusion

I built the full ML workflow: preprocessing, target labeling, feature engineering, model comparison, Buy/Sell conversion, and PnL calculation.
**Logistic Regression** performed best and was used as the final model.

All assignment requirements are completed successfully.
