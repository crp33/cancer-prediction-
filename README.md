# Introduction
We will be working with the Breast Cancer Wisconsin (Diagnostic) dataset, which contains detailed measurements of cell nuclei. Each observation includes a diagnosis indicating whether the cell is malignant or benign. Our objective is to train a model that can accurately predict whether a given cell is malignant based solely on its measurements.
# Data from Breast Cancer Wisconsin (Diagnostic) Data Set
Features are computed from digitized images of fine needle aspirates (FNA) of breast masses. These features describe various characteristics of the cell nuclei present in the image. The 3-dimensional space used for these measurements is described in:
K. P. Bennett and O. L. Mangasarian: "Robust Linear Programming Discrimination of Two Linearly Inseparable Sets", Optimization Methods and Software 1, 1992, 23-34.
# How we cleaned the data
Using a heatmap, we visualized the presence of missing values in the dataset. One column was entirely composed of NAs, so we dropped it. We also removed the ID column, as it does not contribute to the predictive task.
Additionally, we converted the target variable into binary format—1 for malignant and 0 for benign—to prepare it for model training.
# Logistic Regression
Once the dataset was cleaned and the variables confirmed to be reliable, we proceeded to train our model. We first separated the target variable (referred to as "y") from the predictors (referred to as "X").
# Normalize Data
To mitigate the impact of outliers and improve model performance, we normalized the data before feeding it into the model. This step helps ensure that all features contribute equally to the learning process.
# Evaluate the model
We trained a logistic regression model to predict the target variable using the input features. After training on the training set and evaluating on the test set, the model achieved an accuracy of 0.98. This high accuracy indicates strong predictive performance on unseen data.
However, accuracy alone may not be sufficient for all applications. Depending on the context, other metrics such as precision, recall, and F1 score may be more informative. We used Scikit-learn’s classification_report to compute these additional metrics.
# Conclusion
We completed our analysis using the Breast Cancer Wisconsin dataset to build a model that predicts whether a cell is malignant based on its nucleus measurements.
This model, once validated and deployed, could be a valuable tool in clinical settings helping medical professionals make faster and more accurate diagnostic decisions.
