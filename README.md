# SIADS-696
Milestone II Repositry

# Volatility Regime Detection and Near-Term Risk Forecasting

This project was completed as part of **SIADS 696: Milestone II** in the University of Michigan Master of Applied Data Science (MADS) program.

The goal of the project is to identify different market volatility regimes from historical S&P 500 and VIX data and test whether information about these regimes can improve short-term volatility forecasts.

## Team

* Shub M
* Lina Al-Rawahi
* Yu Fang

# SIADS 696 – Milestone II

## Market Regimes and Equity Volatility

This repository contains our Milestone II project for SIADS 696 in the University of Michigan MADS program.

The project looks at whether different market volatility regimes can be identified from historical S&P 500 and VIX data, and whether those regimes are useful for forecasting future realized volatility.

## Team

- Shub M
- Lina Al-Rawahi
- Yu Fang

## Project Idea

Financial markets do not behave the same way all the time. There are relatively calm periods, periods where volatility starts to increase, and periods of significant market stress.

Our project tries to identify these different market environments using an unsupervised learning model. We then use the regime information as an input to a supervised model and test whether it improves short-term volatility forecasts.

Our main research question is:

> Can latent market regimes identified from historical market behavior improve the prediction of future realized volatility?

## Data

We are using daily market data from 2000 through 2025.

The main datasets are:

- S&P 500 daily price and volume data
- CBOE VIX daily data
- A merged dataset aligned by trading date

The merged dataset contains roughly 6,500 daily observations.

We also create features such as:

- 5-, 10-, and 20-day realized volatility
- VIX level and changes in VIX
- rolling skewness
- rolling kurtosis

## Part B – Unsupervised Learning

We start with the unsupervised part of the project.

The main model is a Gaussian Hidden Markov Model (HMM), which is used to identify latent market regimes from the market features.

We currently interpret the states as broadly representing:

- Calm
- Transition
- Stressed

The labels are assigned after looking at the characteristics of each state, including VIX levels, realized volatility, and market behavior during each regime.

We also use K-means clustering as a simpler comparison model. Unlike the HMM, K-means does not explicitly account for the time dependence of market regimes.

For the HMM analysis, we look at:

- regime characteristics
- regime persistence
- transition probabilities
- behavior during major market stress periods
- how the HMM regimes compare with K-means clusters

## Part A – Supervised Learning

The supervised part of the project focuses on forecasting future realized volatility.

The idea is to first build models using standard market features and then test whether adding the regime information from Part B improves the forecasts.

Inputs include variables such as:

- recent realized volatility
- VIX
- skewness
- kurtosis
- estimated regime information from the HMM

Forecast performance will be compared using RMSE and MAE.

We will also compare the models against a simple persistence baseline, where future volatility is assumed to be similar to recent realized volatility.

## Project Workflow

The overall workflow is:

1. Collect and clean S&P 500 and VIX data
2. Create rolling market and volatility features
3. Use an HMM to identify market regimes
4. Compare the HMM regimes with K-means
5. Use regime information as an additional input to the supervised model
6. Compare volatility forecasts with and without regime information

## Repository Structure

```text
SIADS-696/
│
├── data/
│   └── market datasets used in the analysis
│
├── notebooks/
│   └── data analysis and modeling notebooks
│
├── figures/
│   └── charts and model outputs
│
└── README.md