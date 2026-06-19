![Alt Text](./Images/pexels-pixabay-267885.jpg)

# Predicting Student Performance — Multiple Linear Regression

**An end-to-end regression project: predicting a student's Performance Index from study habits,
with full model diagnostics and a deployment-ready saved model.**

> A clean, complete supervised-learning workflow — EDA, train/test split, model fit, evaluation,
> residual diagnostics, and model serialisation. Built to demonstrate the full regression
> lifecycle, not just a `.fit()` call.

---

## Business problem
Given a student's study habits and background, can we predict their overall Performance Index?
A reliable model lets educators flag students who may need support early and identify which
habits move the needle most.

## Dataset
**Student Performance** dataset — features include Hours Studied, Previous Scores, Sleep Hours,
Sample Question Papers Practised, and Extracurricular Activities. Target: a continuous
Performance Index. Source: Kaggle.

## What I did
- **EDA:** inspected structure and plotted each feature against the target to check linearity
- **Modelling:** train/test split (70/30, seeded), `LinearRegression` fitted on the training set
- **Evaluation:** R², RMSE, and MAE on the held-out test set
- **Residual diagnostics:** residual scatter plot *and* a KDE of residuals to check for bias and
  even spread — confirming the model's errors are well-behaved
- **Interpretation:** examined coefficients to see which habits most influence performance
- **Deployment-ready:** saved the trained model with `joblib` for reuse without retraining

## Results
The model explains the target almost completely (R² ≈ 0.99 on the test set), with low RMSE and MAE.

**A note on that high R²:** this dataset is near-perfectly linear by design, so a very high R² is
expected — it reflects the data, not an overfit model (the held-out test score is just as strong).
Previous Scores and Hours Studied are the dominant drivers of performance.

## Key takeaway
Consistent study hours and strong prior performance are the clearest predictors of the Performance
Index — actionable levers for early intervention.

## Tools
Python (pandas, NumPy, seaborn, matplotlib) · scikit-learn (`LinearRegression`) · joblib

---

## Planned upgrade
The saved model is ready to ship. Next iteration: wrap it in a **Streamlit web app** where a user
enters their study habits and gets a live prediction, deployed free on Streamlit Community Cloud —
then log inputs over time to monitor for **data drift**.
