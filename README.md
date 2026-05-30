# IEEE-CIS Fraud Detection — Scalable Classical ML on High-Dimensional Tabular Data

> Comparing linear SVM (via SGD) and Decision Tree models for fraud detection on the IEEE-CIS dataset, with a focus on scalability, interpretability, and hyperparameter optimization.

**Course:** COMP 6831 – Applied Machine Learning (Concordia University, Microprogram in Applied AI)

---

## Overview

Credit card fraud detection is a canonical large-scale, class-imbalanced tabular classification problem. The IEEE-CIS Fraud Detection dataset contains hundreds of features across millions of transactions, which makes naive model choices computationally infeasible.

This project benchmarks two contrasting approaches on the same preprocessing pipeline:

- **Model 1 — Linear SVM via Stochastic Gradient Descent (`SGDClassifier`)**
  Approximates a linear SVM and scales linearly with dataset size, making it tractable for IEEE-CIS where a standard `SVC` would not converge in reasonable time.
- **Model 2 — Decision Tree**
  Provides an interpretable, non-linear baseline capable of capturing complex feature interactions. Evaluated as both an untuned baseline and a tuned model with regularization to control overfitting.

## Approach

1. **Data preprocessing** — handling of missing values, encoding of categorical features, scaling for SVM, and stratified train/validation splits to preserve the original fraud class ratio.
2. **Model 1: Linear SVM (SGD)** — hinge-loss linear classifier trained with stochastic gradient descent for scalability.
3. **Model 2: Decision Tree** — baseline tree, followed by hyperparameter tuning over `max_depth`, `min_samples_split`, and `min_samples_leaf` to mitigate overfitting.
4. **Model comparison** — head-to-head evaluation on the same validation split using AUC, F1, precision, and recall, with discussion of trade-offs between scalability (SVM) and interpretability (tree).

## Results

| Model | AUC | F1 | Precision | Recall | Notes |
|---|---|---|---|---|---|
| Linear SVM (SGD) | 0.974 | 0.23 | 0.67 | 0.50 | Fast to train, struggles with non-linear feature interactions |
| Decision Tree (baseline) | 0.969 | 0.57 | 0.55 | 0.60 | Overfits without regularization |
| Decision Tree (tuned) | 0.974 | 0.57 | 0.67 | 0.50 | Best overall on the validation split |



## Tech Stack

`Python` · `scikit-learn` (`SGDClassifier`, `DecisionTreeClassifier`, `GridSearchCV`) · `pandas` · `NumPy` · `matplotlib` · `Jupyter`

## Repository Structure

```
.
├── notebook/
│   └── fraud_detection.ipynb        # Final analysis notebook
├── report/
│   └── ieee_cis_fraud_report.pdf    # Full written report
├── data/
│   └── README.md                    # Instructions for downloading the dataset from Kaggle
├── requirements.txt
└── README.md
```

## How to Run

```bash
# 1. Clone and enter the repo
git clone https://github.com/ahmad649/ieee-cis-fraud-detection.git
cd ieee-cis-fraud-detection

# 2. Install dependencies
pip install -r requirements.txt

# 3. Download the dataset (see data/README.md) and place under data/

# 4. Launch the notebook
jupyter notebook notebook/fraud_detection.ipynb
```

## Key Takeaways

- For very large tabular datasets, SGD-based linear classifiers offer a practical alternative to kernel SVMs that would not scale.
- Decision Tree performance is highly sensitive to depth and split criteria; even basic regularization yields significant gains.
- Class imbalance handling (stratified splits, class weighting) had a larger impact on F1 than model choice alone.

## Author

Ahmad Hasan — Master of Applied Computer Science + Microprogram in Applied AI, Concordia University
[LinkedIn](https://www.linkedin.com/in/ahmad-hasan-cs/) · [GitHub](https://github.com/ahmad649)

## License

MIT
