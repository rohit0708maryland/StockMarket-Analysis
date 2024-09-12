# StockMarket-Analysis
**Project Title: Predicting SP500 Returns Using Machine Learning Models**
**Overview**
This project focuses on building and evaluating machine learning models to predict the returns of the S&P 500 stock index. Using historical data and technical indicators, I have trained various models, including Random Forest, XGBoost, and LSTM, to forecast future returns. The project explores different financial features such as stock returns, volatility, relative strength index (RSI), and external factors like interest rates to create a robust predictive model. The goal is to compare the predicted returns with the actual returns to understand the performance and limitations of these models in financial forecasting.

**Key Steps in the Project**
1. **Data Collection**
I used the yfinance API to download historical stock data for S&P 500, Nasdaq, and Apple. This data included adjusted close prices and trading volumes, ranging from September 2023 to January 2024.
I also integrated interest rate data from the FRED (Federal Reserve Economic Data) API, which provides macroeconomic factors that could influence market returns.

Tools Used:

**yfinance to download stock data.
fredapi to download interest rate data from FRED.**

Downloaded Data Includes:

**S&P 500 (^GSPC)
Nasdaq (^IXIC)
Apple (AAPL)
Interest Rate (DFF - Daily Federal Funds Rate)**
2. **Feature Engineering**
For each stock, I calculated essential financial indicators, including:
Daily Returns: Percentage change in the adjusted close price.
Volatility: 30-day rolling standard deviation of daily returns to capture market risk.
RSI (Relative Strength Index): A momentum oscillator to measure the speed and change of price movements over 14 days, using the pandas_ta library.
Trading Volume: Volume of trades for each stock.
Technical Indicators Included:

SP500_Return, Nasdaq_Return, Apple_Return
Nasdaq_Volatility, Apple_Volatility
SP500_RSI, Nasdaq_RSI, Apple_RSI
SP500_Volume, Nasdaq_Volume, Apple_Volume
Interest_Rate
3.**Data Merging**
I merged the technical indicators for each stock and the interest rate data into a consolidated DataFrame. The merged data included all 11 features needed for the model.
The features were aligned by the Date column, and any missing values were dropped to ensure clean and consistent data for model training.
4. **Model Building**
I trained multiple machine learning models to predict the future returns of the S&P 500:
Random Forest: A tree-based ensemble method that captures non-linear relationships in the data.
XGBoost: A boosting algorithm that optimizes model performance by sequentially improving weak models.
LSTM (Long Short-Term Memory): A recurrent neural network (RNN) that captures temporal dependencies in sequential data like stock returns.
Steps:

Split the data into features (X_train) and target variable (y_train) where y_train represents the S&P 500 returns.
Trained each model using the feature set, which included technical indicators and macroeconomic data.
5. **Model Evaluation**
After training the models, I used them to predict returns for future dates (October 2023 to January 2024).
I then compared the predicted returns with the actual S&P 500 returns to evaluate the model's performance.
Key evaluation metrics used were:
Mean Absolute Error (MAE): Measures the average magnitude of errors in a set of predictions.
Root Mean Squared Error (RMSE): Penalizes larger errors more than smaller ones to highlight significant deviations.
6. **Results Visualization**
To illustrate the model's performance, I created line plots comparing Actual vs Predicted S&P 500 Returns over the time period.
In the visualization, I used the Random Forest model's predictions and plotted them against the actual returns. The plot clearly shows that while the model captures the general trend and direction of the returns, it sometimes under- or over-estimates the magnitude of market movements.
Observations:

The model performed well during periods of moderate volatility but struggled to capture extreme market movements, particularly sharp drops or spikes.
This behavior suggests that the model may benefit from further tuning or the inclusion of additional market factors (e.g., macroeconomic indicators like inflation, GDP).

**Key Findings
Model Strengths:
**
The Random Forest model demonstrated good performance in capturing the general trend of S&P 500 returns during stable market periods.
The inclusion of multiple features such as volatility, RSI, and macroeconomic data improved the model's ability to capture market fluctuations.
Model Limitations:

The model underperformed during periods of sharp market movements (e.g., mid-December) where the predictions deviated significantly from the actual returns.
Further improvements could be made by tuning hyperparameters or incorporating more advanced models like ensemble stacking.
Feature Importance:

Feature importance analysis from the Random Forest model indicated that Nasdaq volatility, Apple returns, and RSI values were among the most influential in predicting S&P 500 returns.
External factors such as interest rates played a secondary role but provided valuable context during market volatility.
Conclusion
This project highlights the application of machine learning in financial forecasting by using technical indicators and macroeconomic data. The models built, particularly the Random Forest model, provided reasonable predictive power for S&P 500 returns, although there is room for improvement, particularly in handling extreme market events. Future work could focus on:

Hyperparameter tuning to improve model performance.
Additional features such as sentiment analysis, economic indicators (e.g., inflation rates), and geopolitical events to capture more complex market dynamics.
Alternative models like XGBoost and LSTM could also be explored further for comparison in different market conditions.
