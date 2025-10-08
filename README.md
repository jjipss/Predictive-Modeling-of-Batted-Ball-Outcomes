# Predictive-Modeling-of-Batted-Ball-Outcomes

# Overview

This project uses the TrackMan 2022 baseball dataset to predict the expected total bases from batted balls. We built and compared multiple machine learning models, including Random Forest and XGBoost, and applied feature engineering, hyperparameter tuning, and model interpretation techniques (correlation analysis and SHAP values).

The final model achieved:
- RMSE: 0.615
- R²: 0.653

These results show that while the model captures much of the variance in outcomes, further improvements are possible.

# Project Motivation

Baseball is full of measurable physical variables — exit velocity, launch angle, spin rate — that influence the outcome of each hit. By predicting expected total bases, we can provide insights for:

- Opponent scouting: anticipate likely hit outcomes and adjust defensive positioning.
- Player development: give hitters instant feedback on the likely value of their contact.
- Game strategy: understand which types of batted balls are most valuable to prevent or generate .


# Data and Target Variable

- Source: TrackMan 2022 dataset.
- Target: TotalBases (numeric).

Constructed by mapping PlayResult values (e.g., “Single” = 1, “Double” = 2, “Out” = 0).

Initial Features: ExitSpeed, Angle, Direction, Distance, HitSpinRate, HangTime, MaxHeight, VertApprAngle, HorzApprAngle, HitType .

# Feature Engineering

- One-hot encoding: applied to categorical HitType.
- Correlation analysis: dropped HangTime (strongly correlated with Angle, Distance, MaxHeight).
- SHAP values: identified and removed low-importance features (e.g., PopUp, GroundBall, VertApprAngle, HorzApprAngle).
- Final Features: ExitSpeed, Angle, Direction, Distance, HitSpinRate, MaxHeight, HitType_Undefined, HitType_LineDrive, HitType_FlyBall .

# Evaluation

Metrics: Root Mean Squared Error (RMSE) and R².

Why these metrics?
1. RMSE captures average prediction error (lower is better).
2. R² measures explained variance (higher is better).

# Limitations

1. Focused primarily on physical characteristics of the ball; contextual factors (pitcher, batter, stadium) not included.
2. “Out” mapped to 0 may oversimplify certain events.
3. Performance can be improved — RMSE is still relatively high .
