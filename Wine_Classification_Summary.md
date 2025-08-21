# 🍷 Results Summary: Red Wine Quality Classification

## 1. Project Overview
The goal of this project was to classify red wines as **"Good" (quality ≥ 6)** or **"Bad" (quality < 6)** using physicochemical measurements.  

The dataset contained **1,599 samples** with 11 numeric features such as alcohol content, acidity levels, sulphates, and sugar content.  

Five models were evaluated:
- Logistic Regression
- Random Forest
- Support Vector Machine (SVM)
- Tuned Random Forest (with hyperparameter optimization)
- XGBoost

---

## 2. Model Performance Metrics

| Model                  | Precision (Class 0) | Recall (Class 0) | F1 (Class 0) | Precision (Class 1) | Recall (Class 1) | F1 (Class 1) | Accuracy |
|------------------------|--------------------|------------------|--------------|---------------------|------------------|--------------|----------|
| Logistic Regression    | 0.72               | 0.76             | 0.74         | 0.78                | 0.75             | 0.76         | 0.75     |
| Random Forest          | 0.78               | 0.82             | 0.80         | 0.83                | 0.80             | 0.81         | 0.81     |
| SVM                    | 0.71               | 0.40             | 0.52         | 0.62                | 0.86             | 0.72         | 0.65     |
| Tuned Random Forest    | 0.79               | 0.81             | 0.80         | 0.83                | 0.81             | 0.82         | 0.81     |
| XGBoost                | 0.80               | 0.83             | 0.82         | 0.85                | 0.82             | 0.83         | 0.82     |

---

## 3. Observations & Comparisons

### Logistic Regression
- **Accuracy:** 75%
- A balanced baseline model with similar precision and recall for both classes.
- Struggles slightly with capturing non-linear relationships in the data compared to tree-based methods.

### Random Forest
- **Accuracy:** 81%
- Clear improvement over Logistic Regression.
- Good balance between precision and recall; less prone to overfitting.
- Captures non-linearities and feature interactions effectively.

### Support Vector Machine (SVM)
- **Accuracy:** 65%
- High recall for **good wines** (Class 1) at 0.86, meaning it rarely misses a good wine.
- Very low recall for **bad wines** (Class 0) at 0.40, leading to many false positives for good wines.
- Imbalanced precision/recall makes it less practical in this context.

### Tuned Random Forest
- **Accuracy:** 81%
- Similar performance to the baseline Random Forest.
- Minor improvements in recall for Class 0 and Class 1.
- Hyperparameter tuning confirmed that the default RF was already well-suited to this dataset.

### XGBoost
- **Accuracy:** 82% (highest among tested models)
- Best-performing model overall with slightly higher recall for Class 0 compared to others.
- Feature importance rankings similar to Random Forest, with **alcohol** and **sulphates** being top predictors.
- Robust to overfitting and provides smooth ROC curves.

---

## 4. Feature Importance Insights
Across Random Forest and XGBoost:
1. **Alcohol** – Strongest positive predictor of wine quality.
2. **Sulphates** – Strongly correlated with higher quality ratings.
3. **Volatile Acidity** – Negatively impacts wine quality.
4. **Citric Acid** – Positive but smaller contributor.
5. Other features like residual sugar and density had minimal predictive influence.

**Feature Importance Chart:**
![Feature Importance](images/feature_importance_rf.png)
![Feature Importance](images/feature_importance_XGBoost.png)

---

## 5. ROC Curve Analysis
- **XGBoost** and **Tuned Random Forest** achieved the highest ROC-AUC scores, indicating strong discrimination between classes.
- **Logistic Regression** showed moderate curve lift.
- **SVM** performed poorly for Class 0 but very well for Class 1, reflected in its ROC shape.

**ROC Curve:**
![ROC Curve](images/roc_curve_tuned_rf.png)

---

## 6. Key Takeaways
- **Tree-based models outperform linear and kernel-based approaches** on this dataset.
- **XGBoost** offers a small but measurable advantage in recall and overall accuracy.
- **SVM** is not suitable for balanced classification here due to large recall gaps between classes.
- Alcohol content remains the most critical feature for predicting wine quality.

---

## 7. Next Steps
- Deploy the **XGBoost** model in a user-facing application for wine quality prediction.
- Validate on a different dataset (e.g., white wine) to test generalization.
- Explore ensemble stacking of Random Forest and XGBoost to combine their strengths.
- Investigate feature engineering to capture additional interactions between chemical properties.

---

**Author:** _[Dana Moore]_  
**Date:** _[8/18/2025]_
