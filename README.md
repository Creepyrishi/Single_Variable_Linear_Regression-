
---

# Single Variable Linear Regression

This README explains the implementation of single variable linear regression using **gradient descent**, **squared error**, and the **cost function**. The code uses `w` (weight) and `b` (bias) to model the relationship `Y = wX + b`.

---

## Table of Contents
1. [Key Components](#key-components)
2. [Hypothesis Function](#hypothesis-function)
3. [Cost Function](#cost-function)
4. [Gradient Descent](#gradient-descent)
5. [Mathematics of Gradient Descent](#mathematics-of-gradient-descent)
6. [Implementation Details](#implementation-details)
7. [Results](#results)

---

## Key Components
- **Input (X)**: Independent variable (e.g., square footage).
- **Output (Y)**: Dependent variable (e.g., house price).
- **Weight (`w`)**: Slope of the line.
- **Bias (`b`)**: Y-intercept.
- **Learning Rate**: Controls step size during gradient descent (`0.02` in code).
- **Iterations**: Number of optimization steps (`500` in code).

---

## Hypothesis Function
The predicted output is calculated as:
```
predicted_Y = w * X + b
```
- `w` and `b` are learned during training.
- Example: If `w = 3` and `b = 7`, the line is `Y = 3X + 7`.

---

## Cost Function (Mean Squared Error)
Measures how well the line fits the data:
```
cost = (1 / (2 * n)) * Σ (predicted_Y - actual_Y)^2
```
- `n`: Number of training examples.
- Squared error penalizes large errors.

---

## Gradient Descent
Optimizes `w` and `b` by minimizing the cost function:

### Steps:
1. **Initialize** `w` and `b` (to `0` in the code).
2. **Compute gradients** (derivatives of the cost with respect to `w` and `b`).
3. **Update parameters**:
   ```
   w = w - learning_rate * (derivative_w / n)
   b = b - learning_rate * (derivative_b / n)
   ```
4. **Repeat** for `500` iterations (as in the code).

---

## Mathematics of Gradient Descent

### Partial Derivatives
1. **Derivative with respect to `w`**:
   ```
   derivative_w = Σ (predicted_Y - actual_Y) * X
   ```
2. **Derivative with respect to `b`**:
   ```
   derivative_b = Σ (predicted_Y - actual_Y)
   ```

### Parameter Updates
- `w` and `b` are updated using:
  ```
  w = w - (learning_rate * average_derivative_w)
  b = b - (learning_rate * average_derivative_b)
  ```
  where `average_derivative_w = derivative_w / n` and `average_derivative_b = derivative_b / n`.

---

## Implementation Details
1. **Dataset**: Generated using `Y = 3X + 7 + noise`.
2. **Code Workflow**:
   - Load data from `linear_regression_dataset.csv`.
   - Initialize `w = 0`, `b = 0`.
   - For each iteration:
     - Compute predictions (`predicted_Y = w * X + b`).
     - Calculate total error and gradients.
     - Update `w` and `b`.
3. **Learning Rate**: `0.02` (controls convergence speed).
4. **Convergence Check**: Print cost every `50` iterations.

---

## Results
After training:
- **Final Weight (`w`)**: ~3.01 (close to the true value `3`).
- **Final Bias (`b`)**: ~6.93 (close to the true value `7`).
- **Cost**: Minimized to a small value (e.g., ~0.25).

Example output during training:
```
Iteration 0: Cost = 342.5212, w = 0.6200, b = 0.1840
Iteration 50: Cost = 0.3837, w = 3.0066, b = 6.2984
Iteration 100: Cost = 0.2565, w = 3.0098, b = 6.8869
...
```

---

**Conclusion**: The code successfully learns the parameters `w` and `b` to fit the line `Y = 3X + 7`, demonstrating the core mechanics of linear regression and gradient descent.