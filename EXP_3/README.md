<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# Email Spam Classification using Machine Learning

## Project Overview

This project implements and compares various machine learning algorithms for email spam classification using the Spambase dataset. The goal is to classify emails as either spam or ham (legitimate) based on word frequency features.

## Dataset

**Dataset:** Spambase CSV
**Features:** Email word-count frequencies of the most common words
**Target Variable:** Binary classification (spam/ham)
**Split:** 70% training, 30% testing with stratified sampling

## Algorithms Implemented

### 1. Naive Bayes Classifiers

- **Gaussian Naive Bayes**: Assumes continuous features with Gaussian distribution
- **Multinomial Naive Bayes**: Suitable for discrete count features
- **Bernoulli Naive Bayes**: Designed for binary/boolean features


### 2. K-Nearest Neighbors (KNN)

- **KD-Tree Algorithm**: Efficient for low-dimensional data
- **Ball Tree Algorithm**: Better for high-dimensional data
- **Varying k values**: Tested with k = 1, 3, 5, 7, 9


### 3. Support Vector Machine (SVM)

- **Linear Kernel**: For linearly separable data
- **Polynomial Kernel**: Maps to higher dimensions using polynomial functions
- **RBF (Radial Basis Function)**: Gaussian kernel for non-linear classification
- **Sigmoid Kernel**: Neural network-inspired kernel


## Preprocessing

- **Feature Scaling**:
    - StandardScaler for Gaussian NB
    - MinMaxScaler for Multinomial NB, KNN, and SVM
    - Binarizer for Bernoulli NB
- **Cross-Validation**: 5-fold Stratified K-Fold
- **Hyperparameter Tuning**: GridSearchCV with accuracy scoring


## Results Summary

### Best Performing Models

| Rank | Algorithm | Accuracy | F1-Score | Training Time |
| :-- | :-- | :-- | :-- | :-- |
| 1 | **SVM (RBF)** | **93.15%** | **91.09%** | 0.07s |
| 2 | KNN (k=1) | 90.39% | 87.76% | 0.1s |
| 3 | SVM (Linear) | 90.13% | 86.77% | 0.06s |

### Naive Bayes Comparison

| Variant | Accuracy | Precision | Recall | F1-Score |
| :-- | :-- | :-- | :-- | :-- |
| Multinomial NB | 88.76% | 93.60% | 76.77% | 84.31% |
| Bernoulli NB | 88.67% | 88.69% | 81.68% | 85.03% |
| Gaussian NB | 81.54% | 69.32% | 95.47% | 80.31% |

### KNN Performance by k-Value

| k | Accuracy | Precision | Recall | F1-Score |
| :-- | :-- | :-- | :-- | :-- |
| 1 | 90.39% | 88.06% | 87.47% | 87.76% |
| 3 | 90.11% | 88.11% | 86.59% | 87.34% |
| 5 | 89.87% | 88.59% | 85.32% | 86.90% |
| 7 | 89.65% | 88.38% | 84.93% | 86.60% |

### SVM Kernel Comparison

| Kernel | Best Parameters | Accuracy | F1-Score | Training Time |
| :-- | :-- | :-- | :-- | :-- |
| **RBF** | C=1, γ='scale' | **93.15%** | **91.09%** | 0.07s |
| Linear | C=1 | 90.13% | 86.77% | 0.06s |
| Polynomial | C=1, degree=3, γ='scale' | 85.09% | 77.87% | 0.08s |
| Sigmoid | C=1, γ='scale' | 80.52% | 74.82% | 0.12s |

## Key Findings

1. **Best Overall Performance**: SVM with RBF kernel achieved the highest accuracy (93.15%) and F1-score (91.09%)
2. **Algorithm Efficiency**: KNN with KD-Tree and Ball Tree showed similar performance but KD-Tree was faster
3. **Naive Bayes Trade-offs**: Multinomial NB had the highest precision (93.60%) while Gaussian NB had the highest recall (95.47%)
4. **Optimal k-value**: For KNN, k=1 provided the best performance, suggesting the dataset has well-separated classes

## Technologies Used

- **Python Libraries**: scikit-learn, pandas, numpy, matplotlib, seaborn
- **Preprocessing**: StandardScaler, MinMaxScaler, Binarizer
- **Model Selection**: GridSearchCV, StratifiedKFold
- **Evaluation Metrics**: Accuracy, Precision, Recall, F1-Score, ROC-AUC


## Evaluation Methodology

- **Cross-Validation**: 5-fold stratified cross-validation
- **Hyperparameter Tuning**: Grid search with cross-validation
- **Performance Metrics**: Comprehensive evaluation including confusion matrices and ROC curves
- **Statistical Validation**: Multiple folds ensure robust performance estimates


## Conclusion

The project successfully demonstrates the implementation and comparison of multiple machine learning algorithms for email spam classification. **SVM with RBF kernel emerged as the top performer**, balancing high accuracy with reasonable training time, making it the recommended model for this spam detection task.
<span style="display:none">[^1]</span>

<div style="text-align: center">⁂</div>

[^1]: ML_exp_3.pdf

