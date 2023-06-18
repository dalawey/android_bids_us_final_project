# README.md

This project contains a Python script for predicting clicks on Android apps using various machine learning algorithms. The script loads data, preprocesses it, trains several models, and prints their performance metrics.

## Prerequisites

The script uses the following Python packages:

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- imbalanced-learn
- pytz

Please ensure these are installed. You can do this with pip:

```
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn pytz
```

## How to Run

1. Ensure that you have the dataset `android_bids_us.csv` in the data folder at the root of the project.
2. Run the script with Python 3.7 or later.
3. The script prints the performance of each model, both on the training set and the test set, and finally prints the model with the highest test f1-score.

## What the Script Does

1. **Data Loading and Preprocessing**: The script loads the Android app bidding data from the `android_bids_us.csv` file. It then merges this with another dataset (`app_df`), replaces None values with numpy NaN, drops columns with over 50% missing data, and drops a list of unwanted columns. The script also converts the timestamp from UTC to local time.

2. **Data Splitting**: The script splits the data into a training set and a test set based on the timestamp. The test set is the last month's data, and the rest is the training set.

3. **Missing Values Imputation**: The script imputes missing values in the 'score', 'device_maker', and 'device_model' columns using the most frequent strategy.

4. **Feature Encoding and Scaling**: Categorical features are encoded using label encoding, and numerical features are scaled using min-max scaling.

5. **Feature Selection**: The script uses Recursive Feature Elimination (RFE) with a decision tree classifier to select the top 10 features.

6. **Model Training and Evaluation**: The script trains several models:

   - Logistic Regression
   - Logistic Regression with class balance
   - AdaBoost classifiers with different base estimators, numbers of estimators, and learning rates
   - Multi-layer Perceptron (MLP) Classifier

   After training each model, the script evaluates it on both the training and test sets, using the f1-score as the key metric.

7. **Model Comparison**: Finally, the script prints the performance of all models and identifies the one with the highest test f1-score.

Please note that the script uses a random state for certain operations, which can affect the reproducibility of the results.

## Contributions

Contributions, issues, and feature requests are welcome!

## License

This project is licensed under the terms of the MIT license.
