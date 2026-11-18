# Machine Learning Foundations

[Source: WORK/KNOWLEDGE/Programming/Machine Learning || Stanford/Module 1.1.pdf]
[Source: WORK/KNOWLEDGE/Programming/Machine Learning || Stanford/Module 1.2.pdf]

Andrew Ng's Stanford Machine Learning course (Coursera) — Module 1.1 (introduction, supervised learning, linear regression model representation) and Module 1.2 (cost function). Pages 1–5 of each read; slide-deck format. Module 1.3.pdf and .docx not read — see cant-move.md.

---

## What Is Machine Learning

- Grew out of work in AI; provides a new capability for computers to learn from data without being explicitly programmed
- Two primary motivating use cases:
  - **Database mining** — large datasets from automation/web (click data, medical records, genomics, engineering sensors)
  - **Applications that can't be hand-programmed** — autonomous systems, handwriting recognition, NLP, computer vision

---

## Types of Machine Learning Problems

### Supervised Learning

- Algorithm is given labeled training data: input-output pairs where the "right answer" is provided for each example
- Two subtypes:
  - **Regression** — predict a real-valued (continuous) output (e.g., house price from square footage)
  - **Classification** — predict a discrete-valued output (e.g., spam vs. not-spam, tumor malignant vs. benign)

### Unsupervised Learning

- No labels provided; algorithm finds structure in the data
- Examples: clustering (market segmentation, news grouping, gene expression), dimensionality reduction

---

## Linear Regression with One Variable (Univariate)

### Notation

| Symbol | Meaning |
|---|---|
| `m` | Number of training examples |
| `x` | Input variable / feature |
| `y` | Output variable / target variable |
| `(x, y)` | One training example |
| `(x⁽ⁱ⁾, y⁽ⁱ⁾)` | i-th training example |

### Learning Algorithm Pipeline

```
Training Set → Learning Algorithm → Hypothesis h
                                         ↑
x (new input) ─────────────────────────→ h → ŷ (predicted output)
```

- The learning algorithm consumes the training set and outputs a hypothesis function `h`
- `h` maps new inputs `x` to estimated outputs `ŷ`

### Hypothesis Function

```
h_θ(x) = θ₀ + θ₁x
```

- `θ₀` = intercept (bias term)
- `θ₁` = slope (weight on feature x)
- This is **univariate linear regression** — linear regression with one variable
- Goal of training: find θ₀ and θ₁ that make h(x) best fit the training data

---

## Cost Function (Mean Squared Error)

- Measures how well the hypothesis fits the training data
- **Squared error cost function:**

```
J(θ₀, θ₁) = (1/2m) × Σᵢ (h_θ(x⁽ⁱ⁾) - y⁽ⁱ⁾)²
```

- Sum of squared differences between predicted and actual values, averaged over training set
- The `1/2` factor is a convenience for the gradient calculation
- Training objective: minimize J(θ₀, θ₁) over parameters θ₀ and θ₁

---

## Relationship to Applied ML (sklearn)

These foundations underlie the sklearn implementations in `engineering/data-science/applied-data-science-python.md`:
- `LinearRegression` minimizes MSE cost function exactly as defined above
- `Ridge` adds L2 penalty term to J; `Lasso` adds L1 penalty
- All supervised learning algorithms follow the same pipeline: training set → fit() → predict(x_new)
- Regression vs. classification distinction maps to `Regressor` vs. `Classifier` class suffixes in sklearn
