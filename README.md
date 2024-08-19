# WQU Capstone

The research project will involve the implementation of advanced machine learning methods to
portfolio allocation, with the aim of designing adaptive investment strategies based on data that
maximizes returns and minimizes risks in a real-time setting. These traditional asset allocation
methods typically utilize past data and expert judgment which may work against them due to potential
lack of adaptability and responding to the abnormal economic environment. And, when it comes to
machine learning (in particular deep learning), this offers nothing but dynamic and automate out of
the box. These algorithms can take in a massive amount of data and detect the subtlest patterns,
enabling them to modify portfolios instantly - thus improving both return and risk management.
This literature review will research what work has been done with machine learning, more specifically
the application of methods as LSTM networks, XGBoost and Random Forest for portfolio allocation.
The findings by these studies have shown that machine learning models are able to uncover intricate
financial data structures and subsequently apply this knowledge within more stable and adaptive
investment strategies. With a working experience of these methodologies, this review will investigate
how and to what extent they collectively enhance the portfolio optimization and risk management in
order to provide a detailed view on its strengths, limitations and future potential behavior.

### Solution Design Document

#### 1. **Introduction**

This document outlines the design and implementation of a Python-based solution for stock price prediction and portfolio optimization. The solution uses historical stock data, machine learning for price prediction, and portfolio optimization techniques to determine the optimal asset allocation based on the Sharpe ratio.

#### 2. **Objectives**

- **Stock Data Collection**: Automatically download historical stock price data for selected stocks.
- **Data Preparation**: Process the raw data to create features and targets for machine learning models.
- **Model Training**: Train a Random Forest model for each stock to predict future prices.
- **Prediction**: Generate price predictions for each stock and calculate prediction accuracy using Mean Squared Error (MSE).
- **Portfolio Optimization**: Use the predicted returns to optimize a portfolio based on the Sharpe ratio.
- **Visualization**: Provide visual insights, including actual vs. predicted prices and the Efficient Frontier.

#### 3. **Architecture**

The solution consists of the following key components:

1. **Data Ingestion Module**:
   - Uses the `yfinance` library to download historical stock data.
   - Stocks of interest: AAPL, MSFT, GOOGL, AMZN, TSLA.
   - Time period: January 1, 2018, to December 31, 2023.

2. **Data Preparation Module**:
   - Extracts the closing prices for each stock.
   - Generates features such as the previous day's closing price (Lag1) and daily returns.
   - Splits the data into training and testing sets.

3. **Model Training Module**:
   - Implements a Random Forest Regressor for each stock.
   - Trains the model using historical data and predicts future prices.
   - Calculates the Mean Squared Error (MSE) to evaluate prediction performance.

4. **Prediction Module**:
   - Stores models and predictions.
   - Visualizes actual vs. predicted stock prices.

5. **Portfolio Optimization Module**:
   - Calculates predicted returns from the model's predicted prices.
   - Simulates multiple portfolios using random weights.
   - Computes the expected return, volatility (standard deviation), and Sharpe ratio for each portfolio.
   - Identifies the portfolio with the highest Sharpe ratio.

6. **Visualization Module**:
   - Plots the Efficient Frontier.
   - Highlights the optimal portfolio on the plot.

#### 4. **Implementation Details**

- **Libraries Used**:
  - `numpy`: For numerical computations.
  - `pandas`: For data manipulation and analysis.
  - `matplotlib`: For plotting and visualization.
  - `yfinance`: For downloading historical stock data.
  - `sklearn`: For machine learning (Random Forest, train/test split, metrics).

- **Data Preparation**:
  - Calculate daily returns for each stock.
  - Feature engineering: Lag1 (previous day’s closing price).
  - Target variable: Current day's closing price.

- **Model Training**:
  - Model: Random Forest Regressor with 100 estimators and a random seed for reproducibility.
  - Training and Testing split: 80% training and 20% testing, without shuffling to maintain the time series order.

- **Portfolio Optimization**:
  - Simulate 10,000 portfolios with randomly assigned weights.
  - Compute the expected annualized return, volatility, and Sharpe ratio.
  - Identify and highlight the portfolio with the maximum Sharpe ratio.

- **Visualization**:
  - Plot actual vs. predicted stock prices.
  - Plot the Efficient Frontier and mark the optimal portfolio.

#### 5. **Assumptions**

- The stock data from `yfinance` is accurate and up-to-date.
- The model assumes that past performance is indicative of future returns, which may not hold true in all market conditions.
- The Random Forest model is chosen for its robustness and ability to handle complex datasets, although other models might yield different results.

#### 6. **Potential Enhancements**

- **Model Improvement**: Explore more complex models like Long Short-Term Memory (LSTM) networks for time series prediction.
- **Feature Engineering**: Incorporate additional features such as moving averages, RSI, or volume data.
- **Risk Management**: Implement more sophisticated risk management strategies, such as Value at Risk (VaR) or Conditional Value at Risk (CVaR).
- **Extended Portfolio Analysis**: Include other financial instruments like bonds or commodities for a more diversified portfolio.

#### 7. **Conclusion**

The solution provides a comprehensive approach to stock price prediction and portfolio optimization using machine learning and quantitative finance techniques. It is designed to be extendable and adaptable, allowing for further enhancements and refinements as needed.