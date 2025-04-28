# Execution Algorithm Development and Testing

This repository contains the code and report for developing a short-term equity execution algorithm using machine learning and dynamic thresholding strategies.

## Project Overview
We developed and tested an execution strategy that buys one share per minute based on predictive features extracted from the limit order book (LOB). The goal is to capture favorable trading opportunities within each minute by dynamically adjusting execution thresholds over time.

The project was conducted as part of Milestone 2 in the Execution Algorithm Development course.

## Files Included
- `milestone2.ipynb`: Jupyter Notebook containing code for feature engineering, model training (MLP and Decision Tree), and backtesting results.
- `Milestone_2.pdf`: Full project report, including methods, model evaluations, performance comparisons, and visualizations.

## Features Used
- **Spread**: Difference between ask and bid price.
- **Order Imbalance**: Buy vs. sell pressure at the top of the book.
- **Momentum**: 5-tick mid-price trend indicator.
- **Execution Intensity**: Rolling execution volume.
- **Order Direction Mean**: Short-term buy/sell sentiment.
- **VWAP**: Volume-weighted average price over last 10 orders.
- **Time Pressure**: Seconds within the minute normalized to [0,1].

## Models Developed
- **MLPClassifier**: Neural network with two hidden layers (64, 32 units).
- **DecisionTreeClassifier**: Tuned with grid search over tree depth and leaf size.

## Strategy Logic
- Predict if current tick's ask price is among the bottom 3% for the minute.
- Execute a market order if model confidence exceeds a time-adaptive threshold.
- Force fallback execution at the 60th second if no trade is triggered.

## Key Results (for AAPL stock)
- **Average Price Improvement**: -$0.0182 per share compared to fallback strategy.
- **Hit Rate**: Captured 66% of bottom 3% ask prices.
- **Execution Time**: Majority of trades executed within the first 30 seconds.
- **Spread Exposure**: Most trades occurred with a spread < 0.2.

## Performance Metrics
- **Precision/Recall (MLP)**: 0.13 / 0.66
- **Precision/Recall (Tree)**: 0.24 / 0.63
- **Buy-side Slippage**: Approx. 1.6 cents improvement per share

## Future Improvements
- Further tuning of MLP architecture and threshold adaptation.
- Extending strategy to sell-side trading.
- Incorporating additional market microstructure signals.

---


