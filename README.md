# Introduction
We will be working with the Breast Cancer Wisconsin (Diagnostic) dataset, which contains detailed measurements of cell nuclei. Each observation includes a diagnosis indicating whether the cell is malignant or benign. Our objective is to train a model that can accurately predict whether a given cell is malignant based solely on its measurements.
# How we cleaned the data
Using a heatmap, we visualized the presence of missing values in the dataset. One column was entirely composed of NAs, so we dropped it. We also removed the ID column, as it does not contribute to the predictive task.
Additionally, we converted the target variable into binary format 1 for malignant and 0 for benign to prepare it for model training.
# Logistic Regression
Once the dataset was cleaned and the variables confirmed to be reliable, we proceeded to train our model. We first separated the target variable (referred to as "y") from the predictors (referred to as "X").
# Normalize Data
To mitigate the impact of outliers and improve model performance, we normalized the data before feeding it into the model. This step helps ensure that all features contribute equally to the learning process.
# Evaluate the model
We trained a logistic regression model to predict the target variable using the input features. After training on the training set and evaluating on the test set, the model achieved an accuracy of 0.97. This high accuracy indicates strong predictive performance on unseen data.
However, accuracy alone may not be sufficient for all applications. Depending on the context, other metrics such as precision, recall, and F1 score may be more informative. We used Scikit-learn’s classification_report to compute these additional metrics.

We started with a baseline logistic regression model using all 30 features from the Breast Cancer Wisconsin dataset. The goal was to see if we could reduce the number of features while maintaining comparable predictive performance.
All 30 features → Accuracy: ≈0.9649

# Feature Reduction Using SHAP

We computed SHAP values to measure each feature’s contribution to predictions.
Top 10 SHAP features → Accuracy: ≈0.9532 (slight drop due to redundancy).
Top 5 SHAP features → Accuracy: ≈0.9800 (almost identical to baseline).

# Both SHAP and Lasso agree on the core predictive features:

worst concave points, worst perimeter, worst radius, mean concave points, worst area
These features capture tumor size and shape irregularity, which are the strongest indicators of malignancy.

# Why this matters:

Adding more features beyond these top predictors introduces redundancy and can slightly reduce performance.
Features like texture_se, smoothness_se, symmetry_mean, fractal_dimension_mean consistently ranked low in SHAP and were zeroed out by Lasso, meaning they add little value.
