# Number of Sales Prediction

A machine learning project that predicts weekly sales for a store and department using historical sales data.

This project was done as part of my internship at SparkIIT (with Wipro).

## Problem Statement

To develop a machine learning model that predicts the number of customer orders for a product or service based on historical data.

## Dataset

- Weekly sales data with 421,570 rows and 5 columns
- Columns: `Store`, `Dept`, `Date`, `Weekly_Sales`, `IsHoliday`
- The notebook downloads the data automatically using `gdown` from Google Drive, so the dataset is not included in this repo (it is too big)

## What I did

1. Loaded the data and checked shape, columns and missing values (no missing values found)
2. Removed rows with negative `Weekly_Sales` (1,285 rows) because they are returns or cancelled orders
3. Converted `IsHoliday` to 0 and 1
4. Made new columns `Year`, `Month`, `Week` and `Day` from the `Date` column
5. Did simple EDA: average sales per month and holiday vs non-holiday sales
6. Split the data into 80% train and 20% test
7. Trained three models and compared them

## Models and Results

| Model | MAE | RMSE | R2 Score |
|-------|-----|------|----------|
| Linear Regression | 15157.31 | 22494.70 | 0.030 |
| Random Forest | 1372.83 | 3676.92 | 0.974 |
| XGBoost | 2174.78 | 4120.08 | 0.967 |

Random Forest gave the best result.

## Things I noticed

- Sales go up in November and December (festival and holiday season)
- Linear Regression did badly because the data is not linear
- Random Forest and XGBoost handled it much better

## How to run

1. Clone the repo
2. Install the libraries
   ```
   pip install -r requirements.txt
   ```
3. Open `Number_Of_Order_Prediction.ipynb` in Jupyter Notebook or Google Colab and run all cells

## Tech used

Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, XGBoost

## Things to improve

- I used a random train-test split. For time based data, splitting by date (train on older weeks, test on newer weeks) would give a more realistic score
- Can try hyperparameter tuning for Random Forest and XGBoost
- Can add more features like lag sales and rolling averages
