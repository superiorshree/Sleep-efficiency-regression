# Sleep Efficiency Prediction using Linear Regression

A small machine learning project that predicts **sleep efficiency** (a continuous value from 0 to 1) from a person's daily habits, using simple and multiple linear regression.

Course: RCA, Unit I (Regression)

## Problem
Sleep efficiency is the share of time in bed that a person actually spends asleep. Because the target is a continuous number, this is a **regression** problem, not a classification problem.

## Dataset
**Sleep Efficiency Dataset** from Kaggle (452 rows, 15 columns).

Features used: Age, Gender, Sleep duration, Deep sleep percentage, Awakenings, Caffeine consumption, Alcohol consumption, Smoking status, Exercise frequency.

Target: Sleep efficiency

## What the notebook does
1. Loads and cleans the data (drops unused columns, fills missing values with the median, converts text to 0/1).
2. Splits the data 80% train and 20% test.
3. Fits a **simple linear regression** using the best single feature.
4. Fits a **multiple linear regression** using all features and reads the coefficients.
5. Plots the **residuals**.
6. Solves least squares by hand with the **normal equation** in NumPy and checks it matches scikit-learn.
7. Predicts sleep efficiency for new data, including a cell that takes input from the user.

## Results
| Model | R² |
|---|---|
| Simple linear regression (Deep sleep percentage) | 0.59 |
| Multiple linear regression (all features) | 0.74 |

Multiple linear regression on the test set: MSE = 0.0049, MAE = 0.057

**Key findings**
- Awakenings and smoking lower sleep efficiency the most.
- Deep sleep percentage, exercise frequency and sleep duration raise it.
- Caffeine has almost no effect in this dataset.

## Design choices
- `REM sleep percentage` and `Light sleep percentage` were dropped because REM + Deep + Light = 100%. Keeping all three would make the features perfectly dependent on each other (multicollinearity).
- Missing values are filled with the median so that outliers do not distort them.

## Limitations
- Small dataset (452 rows) and a single train/test split.
- Linear regression assumes straight-line relationships between the features and the target.
- Coefficients are in different units, so their sizes cannot be compared directly.

## How to run
```bash
git clone https://github.com/superiorshree/Sleep-efficiency-regression.git
cd sleep-efficiency-regression
pip install -r requirements.txt
jupyter notebook sleep_efficiency_regression.ipynb
```
Run all cells. The last cell asks for input (age, gender, sleep duration and so on) and prints the predicted sleep efficiency.
```
## GitHub Submission

Submitted to: [@complexiota](https://github.com/complexiota)
```
## Author
Shreeyansh Mahamuni
