# Multi-Layer-Perceptron

# Multi-Layer Perceptron (MLP) for Child Poverty Data Classification

This project implements a Multi-Layer Perceptron (MLP) for classifying child poverty levels based on county-level data. Various preprocessing techniques and model architectures were explored to improve model accuracy and efficiency.

## Motivation

County-level granularity was included to improve the accuracy of models trained on state data. Aggregating data at the state level obscured regional disparities, especially in large states like Texas. Including counties captures local variations and improves model reliability.

## Data Balancing

Data was balanced **before** train-test splitting by:
- Dividing child poverty levels into quartiles.
- Ensuring equal representation across these quartiles.

This approach aimed to create more generalizable and fair training and testing sets.

## Preprocessing and Initial Modeling

### Techniques Used:
- Two-layer perceptron
- Vectorized backpropagation
- Cross-entropy loss
- Glorot initialization
- Minibatching

### Baseline Accuracy:
- **Before normalization/encoding**: ~24%

### After Preprocessing:
- **After normalization**: ~65%
- **After one-hot encoding**: ~67%

> ⚠️ Trade-off: One-hot encoding boosts accuracy but significantly increases runtime (from ~15s to ~60s).

## Model Architectures and Performance

| Model Layers | Accuracy       | Wall Time |
|--------------|----------------|-----------|
| 3 Layers     | 0.7005         | 1m 21s    |
| 4 Layers     | 0.7085         | 1m 35s    |
| 5 Layers     | 0.7004         | 1m 39s    |

- The five-layer model **underperformed** due to overfitting, breaking the increasing accuracy trend.

## Adaptive Learning Techniques

### AdaGrad
- **Accuracy**: 0.7235
- **Epochs**: 100
- **Wall Time**: 3m 28s
- Significant accuracy boost at the cost of increased runtime.

### AdaM
- **Accuracy**: 0.7220
- **Epochs**: 100
- **Wall Time**: 3m
- Provided ~10% gain over the base five-layer model with relatively low overhead.

## Key Takeaways

- More layers don’t always mean better performance—watch for overfitting.
- Preprocessing (normalization, encoding) is critical to achieving high accuracy.
- Adaptive learning methods like AdaGrad and AdaM significantly improve performance, though at a computational cost.
- Trade-off: Time vs. Accuracy—users must choose based on their needs.


