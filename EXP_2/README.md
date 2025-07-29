# Loan Amount Prediction using Linear Regression

This project aims to predict loan amounts using a Linear Regression model and evaluate the model's performance using K-Fold Cross-Validation. The project tracks both training and testing metrics to assess model fitting (overfitting/underfitting).

## 📊 Dataset Overview

- **Dataset Size (after preprocessing)**: 21,457 samples
- **Train/Test Split Ratio**: 80:20 (K = 5 in Stratified K-Fold Cross-Validation)
- **Target Variable**: `Loan Sanction Amount (USD)`

### 🧮 Features Used

- Gender  
- Age  
- Income (USD)  
- Income Stability  
- Profession  
- Type of Employment  
- Location  
- Loan Amount Request (USD)  
- Current Loan Expenses (USD)  
- Expense Type 1  
- Expense Type 2  
- Dependents  
- Credit Score  
- No. of Defaults  
- Has Active Credit Card  
- Property Age  
- Property Type  
- Property Location  
- Co-Applicant  
- Property Price  
- **Target**: Loan Sanction Amount (USD)

---

## 🧠 Model: Linear Regression

We use scikit-learn’s `LinearRegression()` model and evaluate it with Stratified K-Fold Cross-Validation to ensure fair performance across all target value ranges.

---

## 🔁 Cross-Validation

- **Type**: Stratified K-Fold (on binned target variable)
- **Number of Folds**: 5

## 🧪 Performance Metrics

Both **training** and **validation** (test) metrics are computed on each fold:

- Mean Absolute Error (MAE)  
- Mean Squared Error (MSE)  
- Root Mean Squared Error (RMSE)  
- R² Score  
- Adjusted R² Score

---

## 🔍 How to Identify Overfitting or Underfitting?

- If **Train R² >> Test R²** and **Train MAE << Test MAE**, the model is likely **overfitting**.
- If **Train R² ≈ Test R²** and both are low, it's likely **underfitting**.
- If both **Train and Test metrics** are high-quality and similar, the model is likely **well-generalized**.

---

## 📦 Dependencies

```bash
pip install numpy pandas scikit-learn