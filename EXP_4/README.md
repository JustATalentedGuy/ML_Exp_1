# Ensemble Learning and Decision Trees for Breast Cancer Classification

## Project Overview

This project implements and evaluates various decision tree and ensemble learning algorithms for breast cancer diagnosis using the Wisconsin Breast Cancer Diagnostic dataset. The goal is to classify breast masses as benign or malignant based on cell nuclei characteristics extracted from fine needle aspirate (FNA) images.

## Dataset

**Dataset:** Wisconsin Breast Cancer Diagnostic Dataset (UCI Repository)
**Source:** Fine needle aspirate (FNA) images of breast masses
**Features:** Cell nuclei characteristics including radius, texture, perimeter, smoothness, and symmetry
**Target Variable:** Binary classification (benign/malignant)
**Data Split:** 70% training, 30% testing with stratified sampling
**Missing Values:** None detected in the dataset

## Algorithms Implemented

### 1. Decision Tree Classifier

- **Method**: Non-parametric supervised learning with recursive partitioning
- **Split Criteria**: Gini Index, Entropy, Log Loss
- **Hyperparameters Tuned**: max_depth, min_samples_split


### 2. AdaBoost (Adaptive Boosting)

- **Method**: Sequential ensemble of weak learners with adaptive sample weighting
- **Base Learner**: Decision stumps
- **Hyperparameters Tuned**: n_estimators, learning_rate


### 3. Gradient Boosting

- **Method**: Sequential ensemble fitting residual errors
- **Optimization**: Gradient descent on loss function
- **Hyperparameters Tuned**: n_estimators, learning_rate, max_depth


### 4. XGBoost (Extreme Gradient Boosting)

- **Method**: Optimized gradient boosting with regularization
- **Features**: L2 regularization, parallelization, advanced pruning
- **Hyperparameters Tuned**: n_estimators, max_depth, learning_rate, subsample, colsample_bytree


### 5. Random Forest

- **Method**: Parallel ensemble of decision trees with bagging
- **Features**: Bootstrap sampling, feature randomness
- **Hyperparameters Tuned**: n_estimators, max_depth, min_samples_split


### 6. Stacked Ensemble

- **Base Models**: SVM (RBF kernel), Gaussian Naive Bayes, Decision Tree
- **Meta-Learner**: Logistic Regression
- **Method**: Level-0 predictions as features for Level-1 classifier


## Preprocessing and Methodology

- **Feature Scaling**:
    - StandardScaler for Gaussian-like features
    - MinMaxScaler for non-Gaussian features
- **Cross-Validation**: 5-fold Stratified K-Fold
- **Hyperparameter Tuning**: GridSearchCV with accuracy scoring
- **Evaluation Metrics**: Accuracy, Precision, Recall, F1-Score, ROC-AUC


## Results Summary

### Overall Performance Comparison

| Model | Best Accuracy | F1-Score | Cross-Validation Accuracy |
| :-- | :-- | :-- | :-- |
| **Stacked Ensemble** | **96.49%** | **95.08%** | **94.47%** |
| **AdaBoost** | **95.95%** | **94.25%** | **91.94%** |
| **XGBoost** | **95.46%** | **93.89%** | **93.93%** |
| **Random Forest** | **94.96%** | **93.12%** | **92.94%** |
| **Gradient Boosting** | **93.95%** | **91.75%** | **90.93%** |
| **Decision Tree** | **93.46%** | **91.03%** | **90.44%** |

### Best Hyperparameters by Model

#### Decision Tree

- **Best Configuration**: Entropy criterion, max_depth=5
- **Performance**: 93.46% accuracy, 91.03% F1-score


#### AdaBoost

- **Best Configuration**: learning_rate=0.5, n_estimators=50
- **Performance**: 95.95% accuracy, 94.25% F1-score


#### Gradient Boosting

- **Best Configuration**: learning_rate=0.05, max_depth=2, n_estimators=100
- **Performance**: 93.95% accuracy, 91.75% F1-score


#### XGBoost

- **Best Configuration**: learning_rate=0.05, max_depth=3, n_estimators=100
- **Performance**: 95.46% accuracy, 93.89% F1-score


#### Random Forest

- **Best Configuration**: Consistent performance across various configurations
- **Performance**: 94.96% accuracy, 93.12% F1-score


#### Stacked Ensemble

- **Best Configuration**: SVM + Decision Tree + KNN with Logistic Regression
- **Performance**: 96.49% accuracy, 95.08% F1-score


### 5-Fold Cross-Validation Results

| Model | Fold 1 | Fold 2 | Fold 3 | Fold 4 | Fold 5 | Average |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| Stacked Model | 95.0% | 92.5% | 97.5% | 92.5% | 94.9% | 94.47% |
| XGBoost | 95.0% | 92.5% | 95.0% | 100.0% | 87.2% | 93.93% |
| Random Forest | 92.5% | 90.0% | 92.5% | 100.0% | 89.7% | 92.94% |
| AdaBoost | 95.0% | 85.0% | 92.5% | 97.5% | 89.7% | 91.94% |

## Key Findings

### Performance Analysis

1. **Best Overall Performance**: Stacked Ensemble achieved the highest accuracy (96.49%) and F1-score (95.08%)
2. **Ensemble vs. Single Models**: All ensemble methods significantly outperformed the single Decision Tree classifier
3. **Overfitting Detection**: Decision Tree showed clear signs of overfitting (100% training accuracy vs 90% test accuracy)
4. **Generalization**: XGBoost and Stacked models demonstrated the best generalization with minimal overfitting
5. **Hyperparameter Sensitivity**: Random Forest showed consistent performance across different hyperparameter combinations

### Model-Specific Observations

- **AdaBoost**: Performed exceptionally well with lower learning rates and fewer estimators
- **XGBoost**: Showed robust performance with built-in regularization preventing overfitting
- **Random Forest**: Demonstrated stability but limited improvement from hyperparameter tuning
- **Stacking**: Marginal but consistent improvement over individual base models


## Technologies Used

- **Python Libraries**: scikit-learn, XGBoost, pandas, numpy, matplotlib, seaborn
- **Preprocessing**: StandardScaler, MinMaxScaler, LabelEncoder
- **Model Selection**: GridSearchCV, StratifiedKFold
- **Evaluation**: Comprehensive metrics including ROC curves and confusion matrices


## Evaluation Methodology

- **Cross-Validation**: 5-fold stratified cross-validation for robust performance estimates
- **Hyperparameter Optimization**: Exhaustive grid search across relevant parameter spaces
- **Performance Visualization**: Confusion matrices and ROC curves for detailed analysis
- **Overfitting Assessment**: Train vs. test performance comparison


## Conclusion

The project successfully demonstrates the superiority of ensemble methods over single classifiers for breast cancer diagnosis. **Stacked Ensemble emerged as the top performer**, combining the strengths of multiple base learners to achieve 96.49% accuracy. The results highlight the importance of ensemble techniques in medical diagnosis applications where high accuracy and reliability are crucial.

The study also reveals that while hyperparameter tuning can improve performance, some ensemble methods like Random Forest are naturally robust to parameter choices, making them practical for real-world applications.
<span style="display:none">[^1]</span>

<div style="text-align: center">⁂</div>

[^1]: ML_exp_4.pdf