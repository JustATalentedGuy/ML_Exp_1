# 📊 Exploratory Data Analysis on Multiple Datasets

This repository contains a comprehensive exploratory data analysis (EDA) of five distinct datasets. The objective of this assignment is to perform essential preprocessing, correlation analysis, and data transformations required for machine learning tasks.

All analysis is documented in a single Jupyter Notebook: `ML_exp_1.ipynb`.

---

## 📁 Files Included

- `ML_exp_1.ipynb` — Main notebook with all analyses and code.
- `ML_exp_1_documentation` — Documentation of the assignment.
- `datasets/` — Folder containing CSVs or original datasets used.

---

## 📌 Datasets and Tasks

| Dataset                              | ML Task Type               | Description                                                                 |
|--------------------------------------|----------------------------|-----------------------------------------------------------------------------|
| Iris Dataset                         | Multi-class Classification | Classify iris species based on sepal and petal measurements.                |
| Loan Amount Prediction               | Regression                 | Predict loan amount based on applicant data.                                |
| Predicting Diabetes (Pima Dataset)   | Binary Classification      | Predict if a person has diabetes using medical records.                     |
| Email Spam Classification            | Binary Classification      | Classify emails as spam or not using bag-of-words representation.           |
| Handwritten Character Recognition    | Multi-class Classification | Classify hand-written character images using pixel values.                  |

---

## 🔍 Techniques Performed

The following objectives were completed for each dataset, wherever applicable:

### ✅ 1. Handling Missing Values
- Filled missing entries with statistical measures such as mean, median, or mode.
- Ensured completeness and consistency before model building.

### ✅ 2. Feature Correlation Analysis
- Computed Pearson correlation coefficients between input features and output label.
- Visualized correlations using heatmaps for better interpretability.

### ✅ 3. Standardization
- Applied Z-score normalization to numerical features:
  \[
  z = \frac{x - \mu}{\sigma}
  \]
- Prevented features with large magnitudes from dominating the model.

### ✅ 4. Label Encoding
- Converted categorical string labels into numeric form using `LabelEncoder` to make them suitable for machine learning models.

### ✅ 5. Text Feature Analysis (for Spam Dataset)
- Used a Bag-of-Words model to represent emails.
- Computed relative frequencies of words in spam vs. non-spam classes.
- Applied frequency thresholds to remove low-value noisy tokens.

---

## 📈 Visualizations and Outputs

- Correlation heatmaps (matplotlib/seaborn)
- Word importance bar charts (for spam detection)
- Distribution plots for understanding feature spread

---

## 💡 Learning Outcomes

This assignment helped reinforce the following machine learning concepts:

- Data preprocessing and cleaning
- Feature selection based on correlation and importance
- Normalization techniques and when to apply them
- Model-ready transformation of raw data

---

## 🛠️ Requirements

To run the notebook, you will need:

- Python 3.7+
- Jupyter Notebook / JupyterLab
- Required Python packages:
  ```bash
  pip install numpy pandas matplotlib seaborn scikit-learn
