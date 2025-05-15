# 📈 S&P 500 Market Direction Predictor

This project uses historical data and machine learning to **predict the next-day direction** (up or down) of the S&P 500 index based on market indicators such as daily Open, Close, High, Low, and Volume.

## 🚀 Project Overview

The goal of this project is to build and evaluate a classification model that predicts whether the S&P 500 will close higher or lower the following day. It leverages the `yfinance` API for data collection and applies a **Random Forest Classifier** for prediction.

Key features include:
- Historical data fetching and caching
- Feature engineering for target classification
- Model training using a rolling backtesting approach
- Evaluation with accuracy and precision metrics

## 🧠 Technologies Used

- Python
- pandas, NumPy
- yfinance
- scikit-learn
- matplotlib (for visualization)

## 🛠️ How It Works

1. **Data Collection:**  
   - Retrieves daily historical data for the S&P 500 (^GSPC) using `yfinance`.
   - Saves the data locally in `sp500.csv` to avoid repeated API calls.

2. **Feature Engineering:**  
   - Creates a `Tomorrow` column to represent the next day's closing price.
   - Adds a `Target` column: 1 if tomorrow’s price is higher, 0 otherwise.
   - Uses core predictors: `Open`, `High`, `Low`, `Close`, `Volume`.

3. **Modeling:**  
   - Trains a `RandomForestClassifier` with `n_estimators=100`, `min_samples_split=100`.
   - Applies a rolling `backtest()` function to simulate real-world deployment and avoid lookahead bias.

4. **Evaluation:**  
   - Uses `precision_score` to evaluate predictions.
   - Plots and analyzes model performance across test intervals.

## 📊 Example Result

The model delivers a precision score of approximately **57%**, slightly above the baseline chance (~51%), suggesting the presence of weak but exploitable market signals.


## 🤔 Limitations

- Targets **binary movement** prediction only (not actual price change magnitude).
- Does not incorporate macroeconomic or technical indicators.
- Backtesting uses static parameters and a basic strategy.

## ✅ Potential Improvements

- Integrate advanced features like moving averages, RSI, MACD.
- Test other models (XGBoost, SVM, LSTM) for comparison.
- Use time-series aware cross-validation methods.
- Include multi-day forecasting horizons.
