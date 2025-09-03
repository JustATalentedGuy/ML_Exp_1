<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# Perceptron vs Multilayer Perceptron: A/B Comparison for Handwritten Character Classification

## Project Overview

This project implements and compares two fundamental neural network architectures for handwritten character classification: Single-Layer Perceptron (PLA) and Multilayer Perceptron (MLP). The study demonstrates the significant performance gap between linear and nonlinear models for complex pattern recognition tasks.

## Dataset

**Dataset:** Handwritten character images
**Classes:** 62 different characters (letters and digits)
**Task:** Multi-class classification
**Preprocessing:** Image data preprocessed and feature-extracted for neural network input
**Data Split:** Training and testing sets with stratified sampling

## Models Implemented

### Model A: Single-Layer Perceptron (PLA)

**Architecture:**

- Linear classifier with step activation function
- One-vs-rest approach for multi-class classification
- Decision boundary: w^T x + b = 0

**Implementation Details:**

- **Activation Function:** Step function (sign)
- **Learning Rule:** w_new = w_old + η(y_true - y_pred)x
- **Learning Rate:** 1.0
- **Max Epochs:** 50 (with early stopping)
- **Multi-class Strategy:** One-vs-rest binary classifiers

**Mathematical Foundation:**

```
z = w^T x + b
ŷ = f(z) = {1 if z ≥ 0, 0 if z < 0}
Weight Update: w ← w + η(y - ŷ)x
```


### Model B: Multilayer Perceptron (MLP)

**Architecture:**

- Deep neural network with hidden layers
- Nonlinear activation functions
- Backpropagation training

**Implementation Details:**

- **Library:** scikit-learn MLPClassifier
- **Hidden Layers:** (256, 64) neurons
- **Activation Function:** ReLU
- **Optimizer:** Adam
- **Learning Rate:** 0.001
- **Batch Size:** 64
- **Max Epochs:** 50
- **Early Stopping:** Enabled

**Mathematical Foundation:**

```
z[l] = W[l]a[l-1] + b[l]
a[l] = f[l](z[l])
Loss: L = -1/N Σ Σ y_i,k log(ŷ_i,k)
```


## Hyperparameter Tuning

### MLP Grid Search Parameters

| Parameter | Values Tested |
| :-- | :-- |
| Hidden Layer Sizes | (128,), (256, 64) |
| Activation | ReLU, Tanh |
| Solver | Adam |
| Learning Rate | 0.001, 0.01 |
| Batch Size | 64 |

**Best Configuration:**

- Hidden Layers: (256, 64)
- Activation: ReLU
- Learning Rate: 0.001
- Optimizer: Adam


## Results Summary

### Performance Comparison

| Metric | PLA | MLP |
| :-- | :-- | :-- |
| **Test Accuracy** | **33%** | **86%** |
| Model Complexity | Linear | Nonlinear |
| Training Speed | Fast | Moderate |
| Convergence | Simple | Stable with Adam |
| Interpretability | High | Low |

### Key Performance Insights

1. **Accuracy Gap:** MLP achieved 86% accuracy compared to PLA's 33%, demonstrating a **53 percentage point improvement**
2. **Convergence Behavior:**
    - PLA: Simple linear convergence, limited by linear separability
    - MLP: Smooth convergence with early stopping prevention of overfitting
3. **Training Characteristics:**
    - PLA: Fast training but limited representational power
    - MLP: More computational overhead but superior pattern recognition

## Analysis and Observations

### Why PLA Underperforms

**Linear Limitation:** PLA can only model linearly separable decision boundaries. Handwritten character classification requires capturing complex, nonlinear patterns that cannot be separated by linear hyperplanes.

**Feature Representation:** Raw pixel intensities create high-dimensional, non-linearly separable feature spaces that exceed PLA's modeling capacity.

### MLP Advantages

**Nonlinear Modeling:** Hidden layers with ReLU activations enable approximation of complex, nonlinear functions necessary for image pattern recognition.

**Hierarchical Learning:** Multiple layers allow learning of hierarchical feature representations from low-level edges to high-level character shapes.

### Hyperparameter Impact Analysis

1. **Activation Function:** ReLU provided faster convergence and avoided vanishing gradients compared to sigmoid/tanh
2. **Optimizer Choice:** Adam significantly outperformed SGD with adaptive learning rates and better stability
3. **Architecture Depth:** Moderate depth (256, 64) provided optimal balance between capacity and generalization
4. **Learning Rate:** 0.001 balanced convergence speed with training stability

### Overfitting Mitigation

**Observed Issues:** MLP showed signs of overfitting with excessive hidden units or training epochs

**Mitigation Strategies:**

- Early stopping based on validation performance
- Regularization techniques (L2 penalty)
- Appropriate architecture sizing
- Dropout layers (future enhancement)


## Technical Implementation

### Libraries Used

- **pandas, numpy:** Data manipulation and numerical computations
- **matplotlib, seaborn:** Visualization and plotting
- **scikit-learn:** MLP implementation and evaluation metrics


### Evaluation Methodology

- **Cross-Validation:** 3-fold CV for hyperparameter tuning
- **Performance Metrics:** Accuracy, confusion matrices, ROC curves
- **Model Selection:** GridSearchCV for optimal hyperparameter identification


## Key Learning Outcomes

1. **From-Scratch Implementation:** Successfully implemented PLA without external libraries, demonstrating understanding of fundamental learning algorithms
2. **Architecture Comparison:** Gained practical experience with different neural network architectures and their trade-offs
3. **Performance Analysis:** Understood the theoretical and practical reasons for MLP's superiority over linear models for complex pattern recognition
4. **Hyperparameter Optimization:** Learned systematic approaches to model tuning and validation

## Conclusion

This A/B comparison clearly demonstrates the **fundamental limitation of linear models** for complex pattern recognition tasks. While PLA offers simplicity and interpretability, its 33% accuracy is insufficient for practical handwritten character recognition.

**MLP's 86% accuracy** represents a substantial improvement, achieved through:

- Nonlinear activation functions enabling complex pattern modeling
- Multiple hidden layers for hierarchical feature learning
- Advanced optimization techniques (Adam) for stable training
- Proper regularization to prevent overfitting

The results highlight why **multilayer perceptrons became foundational** to modern deep learning, providing the nonlinear modeling capacity essential for real-world AI applications.
<span style="display:none">[^1]</span>

<div style="text-align: center">⁂</div>

[^1]: ML_exp_5.pdf

