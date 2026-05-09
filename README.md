# NBA Shot Outcome Predictor

**Predicting made/missed NBA shots using machine learning**  
*PSTAT 131 Final Project — UC Santa Barbara, March 2026*

---

## Overview

Can we predict whether an NBA shot will go in based on game-situation data alone?
This project uses the 2014-15 NBA Shot Logs dataset (127,835 observations) to build
and compare four classification models, with the goal of predicting shot outcomes
from pre-shot variables like shot distance, defender proximity, dribbles, and shot clock.

## Dataset

**NBA Shot Logs (2014-15 season)**  
127,835 observations | 6 predictors after feature selection

Key predictors used:
- `shot_dist` — distance from the basket (ft)
- `close_def_dist` — distance of nearest defender (ft)
- `dribbles` — number of dribbles before shot
- `touch_time` — time player held the ball before shooting
- `shot_clock` — time remaining on shot clock
- `pts_type` — 2-point or 3-point attempt

> Dataset available on Kaggle: [NBA Shot Logs](https://www.kaggle.com/dansbecker/nba-shot-logs)

## Models Compared

| Model | CV ROC-AUC |
|---|---|
| Logistic Regression | 0.631 |
| Elastic Net | 0.631 |
| Random Forest | 0.637 |
| **Gradient Boosted Tree** | **0.642** |

The gradient boosted tree (XGBoost) was selected as the best model.  
**Final test set ROC-AUC: 0.638**

## Methodology

- 80/20 train/test split stratified on outcome
- 10-fold cross-validation repeated across all models
- Tidymodels pipelines for reproducible preprocessing and tuning
- Correlation analysis used to remove redundant features

## Tech Stack

**Language:** R  
**Libraries:** tidymodels, ggplot2, tidyverse, xgboost  
**Environment:** RStudio / R Markdown

## Files

| File | Description |
|---|---|
| `Final Project.Rmd` | Full analysis and modeling code |
| `Final-Project.html` | Rendered report with all outputs and visualizations |
| `codebook.txt` | Variable descriptions for the dataset |

## Key Finding

The NBA field goal percentage baseline is ~45.3%. Our best model (boosted tree)
correctly predicted shot outcomes 63.8% of the time on unseen test data,
representing a meaningful lift over a naive baseline.
