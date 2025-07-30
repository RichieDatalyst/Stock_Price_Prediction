# PSX Stock Price Prediction & Investment Simulation

This project builds a complete pipeline to:
- Load & clean PSX OHLC data (Date, Symbol, Open, High, Low, Close)
- Visualize trend lines, moving averages, volatility, and candlesticks
- Train **two models** for **closing price** prediction:
  - **LSTM**
  - **RandomForestRegressor** (classical ML baseline)
- Compare metrics (MAE, MSE, RMSE, R²) and plots (Actual vs. Predicted)
- Forecast specific future dates and simulate returns for an investment

> **Note:** The notebook assumes that the student have a CSV with the schema:  
> `Date, Symbol, Open, High, Low, Close`  
> For example: `psx_data_20211210_to_20241210.csv`.

## Quick Start

1) Create and activate a Python 3.10+ environment (recommended).
2) Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3) Launch Jupyter:
   ```bash
   jupyter notebook
   ```
4) Open **PSX_Stock_Prediction.ipynb**, set the config cell:
   - `CSV_PATH` to your dataset file (e.g., `./psx_data_20211210_to_20241210.csv`)
   - `SYMBOL` to the chosen PSX symbol (e.g., `"WTL"` or `"UBL"`)
5) Run all cells (top to bottom).

## Outputs Saved by the Notebook
- **models/**  
  - `lstm_model.h5` (LSTM weights)  
  - `rf_model.joblib` (Random Forest model)
- **figures/** (plots and visualizations saved as PNG)
- **metrics/** (CSV with metrics table)
- **forecasts/** (CSV with date-wise predictions and simulated returns)

## How Forecasting Works
- We train models on historical **Close** prices with sliding windows.
- We forecast daily business days forward to the requested dates:  
  - 1 June 2025, 1 September 2025, 1 December 2025, 1 June 2026
- Investment simulation assumes an investment of **10,000 PKR on 1 June 2025** and computes projected value at each forecast date.

## Candlestick Charts
- We use **mplfinance** (static) and **plotly** (interactive). If you prefer only matplotlib, you can disable plotly cells.

## Reproducibility
- Random seeds are fixed where applicable.
- Results may vary based on library versions, GPU/CPU differences, and dataset updates.

## Presentation & Recording
- See **presentation/** for the slide deck 
- A **5-minute speaker script** is included in the slides to guide your recording.

## License
For academic use.
