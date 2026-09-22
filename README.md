# SIADS-696
Milestone II Repositry

# Volatility Regime Detection and Near-Term Risk Forecasting

This project was completed as part of **SIADS 696: Milestone II** in the University of Michigan Master of Applied Data Science (MADS) program.

The goal of the project is to identify different market volatility regimes from historical S&P 500 and VIX data and test whether information about these regimes can improve short-term volatility forecasts.

## Team

* Shub M
* Lina Al-Rawahi
* Yu Fang

## Project Overview

Financial markets often move through different environments, such as calm, transitional, and stressed periods. These regimes are not directly observed, so the first part of this project uses unsupervised learning to identify them from market data.

We then use the estimated regime information as an additional feature in a supervised learning model to test whether it improves forecasts of future realized volatility.

The main research question is:

> Can market regimes be identified from S&P 500 and VIX data without predefined labels, and does including this information improve short-term volatility forecasts?

## Data

The analysis uses daily market data from **January 2000 through December 2025**.

The main datasets are:

* S&P 500 daily price and volume data
* CBOE VIX daily data
* A merged dataset aligned by trading date

The final merged dataset contains approximately **6,500 daily observations**.

## Methodology

### Part A — Supervised Learning

The supervised portion predicts forward realized volatility using market features such as:

* 5-, 10-, and 20-day realized volatility
* VIX level
* Skewness
* Kurtosis
* Estimated market regime probabilities

Models with regime information are compared against models using only standard market indicators.

Performance is evaluated using **RMSE and MAE**, along with a simple volatility persistence baseline.

### Part B — Unsupervised Learning

The unsupervised portion identifies market regimes using:

* **Gaussian Hidden Markov Model (HMM)**
* **K-means clustering** as a simpler comparison

The HMM captures both the characteristics of each regime and the probability of moving between regimes.

The resulting states are interpreted using measures such as VIX level, realized volatility, persistence, and behavior during known periods of market stress.

## Evaluation

The project focuses on out-of-sample performance using a time-based training and testing approach.

The main comparison is whether adding regime information improves volatility forecasts relative to:

1. A simple persistence baseline
2. Models using standard market variables without regime information

We also examine regime persistence, transition probabilities, clustering quality, and behavior during major stress periods such as the 2008 financial crisis and the 2020 COVID market shock.

## Visualizations

Key visualizations include:

* S&P 500 performance colored by estimated market regime
* Regime transition probability heatmap
* Predicted versus actual volatility
* Forecast error comparisons
* Market characteristics across regimes

## Tools

The project is implemented in Python using libraries including:

* pandas
* NumPy
* scikit-learn
* XGBoost
* hmmlearn
* matplotlib
* yfinance

## Repository Structure

```text
├── data/               # Raw and processed market data
├── notebooks/          # Exploratory analysis and modeling
├── src/                # Reusable analysis and modeling code
├── figures/            # Final charts and visualizations
├── report/             # Project proposal and final report
└── README.md
```

## Course Context

SIADS 696 Milestone II focuses on applying methods learned throughout the MADS program to a larger data science project.

This project combines:

* supervised learning
* unsupervised learning
* feature engineering
* model evaluation
* visualization
* communication of data science results

## Status

Work in progress as part of the Fall 2026 SIADS 696 Milestone II project.
