# How Bad Could It Be? Accident Severity Prediction

**Authors:** Sam Simmons, David Jorgensen, Christopher Caryotakis

## Overview

An analysis of how weather conditions and road infrastructure relate to traffic accident severity, using a dataset of roughly 7 million U.S. car accidents (Moosavi et al.). The project evaluates which environmental and infrastructural factors are the strongest predictors of accident severity and distance of road impacted.

## Approach

- Cleaned the dataset by removing hard-to-interpret categorical features (city/state/county names, wind direction, airport codes) and handled missing data by dropping incomplete rows (~5M records retained)
- Cleaned continuous features using an IQR-based outlier removal, with several columns (visibility, temperature, wind chill) hard-coded to their physically sensible ranges
- Built decision tree, random forest, and XGBoost classifiers to predict accident severity, and matching regressors to predict distance of road affected
- Analyzed feature co-occurrence (e.g., crossings, stations, traffic signals) to understand how infrastructure features interact
- Discussed ethical limitations of the dataset's severity metric, which measures traffic delay rather than injury or fatality

## Key Results

- An unoptimized XGBoost classifier reached 85.31% accuracy predicting severity, identifying wind chill, temperature, and air pressure as top weather-related features
- A random forest classifier on infrastructure-filtered data reached 85.25% accuracy, identifying crossings, traffic signals, and stations as the most important features
- Daytime vs. nighttime conditions had little predictive value, a counterintuitive finding
- Noted that ~85% of records share a single severity rating, meaning raw accuracy alone overstates model quality

## Data

Uses the US Accidents (March 2023) dataset from Kaggle, based on Moosavi et al (www.kaggle.com/datasets/sobhanmoosavi/us-accidents). Not included in this repo due to size — download separately and place as `US_Accidents_March23.csv`.

## Files

- `Accident Severity Prediction.pdf` — full writeup
- `Accident Project Code.ipynb` — data cleaning and modeling code

## Tools

Python (scikit-learn, XGBoost, pandas, NumPy)
