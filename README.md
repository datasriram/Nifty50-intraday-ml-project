# Nifty50-intraday-ml-project
Machine Learning project for predicting next-minute NIFTY50 price direction using intraday OHLCV data. Includes preprocessing, feature engineering, multiple ML models (Logistic Regression, Random Forest, XGBoost), Buy/Sell signal generation, and PnL computation based on assignment rules.
 

1. Project Overview

I created a binary target using next-minute close price movement:

1 → price goes up next minute

0 → price stays same or goes down

Predictions were converted to:

BUY → subtract close

SELL → add close

as required by the assignment.

2. Setup Instructions

Install required libraries:

pip install pandas numpy scikit-learn xgboost matplotlib


I ran the notebook in Google Colab.

3. Feature Engineering

I created the following features:

Basic Features

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

Technical Indicator

RSI (14-period)

Removed Features

I experimented with MACD & MACD histogram, but removed them because they introduced noise and hurt model stability.

4. Models Trained

Logistic Regression (with StandardScaler)

Random Forest

XGBoost

Evaluated using accuracy, precision, recall.

5. Model Performance
Model	Accuracy
Logistic Regression	0.5090
Random Forest	0.5055
XGBoost	0.5031
6. Best Model (2–4 Line Justification)

Logistic Regression performed the best, achieving the highest accuracy, precision, and recall.
It behaved more consistently on noisy intraday data, while tree-based models fluctuated more.
I selected Logistic Regression for generating final Buy/Sell signals and PnL.

7. Buy/Sell Signals & PnL
BUY  = 34,801  
SELL = 28,965


Because BUY subtracts the close price, more BUYs result in a negative PnL.

Final Cumulative PnL:

-143,026,430.45


(This is expected due to the assignment's PnL logic.)

8. Output Table Includes

Timestamp

Close

Prediction

Buy/Sell Call

PnL Step

Cumulative PnL

9. Conclusion

I built the full ML workflow: preprocessing, target labeling, feature engineering, model comparison, Buy/Sell conversion, and PnL calculation.
Logistic Regression performed best and was used as the final model.
All assignment requirements were completed successfully.
