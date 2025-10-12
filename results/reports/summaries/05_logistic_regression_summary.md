# Logistic Regression Model Training Summary

**Source:** Section 5.8 - Save Results and Summary
**Notebook:** gallstone_analysis.ipynb

## Overview

Logistic Regression model trained with hyperparameter tuning using Grid Search Cross-Validation.

## Hyperparameter Tuning

**Method:** GridSearchCV with 5-fold cross-validation

### Search Space
- **Parameter Combinations Tested:** 14
- **Cross-validation Folds:** 5
- **Total Model Fits:** 70

### Best Hyperparameters
- **C (Regularization Strength):** 1
- **Penalty:** L2 (Ridge Regression)

## Performance Metrics

### Cross-Validation Performance
- **Mean ROC-AUC:** 0.8258 ± std

### Test Set Performance
| Metric | Score |
|--------|-------|
| **ROC-AUC** | 0.8828 |
| **Accuracy** | 0.7812 (78.12%) |
| **Precision** | 0.7857 (78.57%) |
| **Recall** | 0.7500 (75.00%) |
| **F1-Score** | 0.7742 (77.42%) |

## Feature Importance Analysis

### Top Predictors

**Strongest Positive Predictor:**
- **C-Reactive Protein (CRP)**
  - Higher CRP levels associated with increased gallstone risk
  - Suggests inflammatory component in gallstone disease

**Strongest Negative Predictor:**
- **Gender**
  - Specific gender associated with lower gallstone risk
  - Aligns with epidemiological findings

## Model Interpretation

### Performance Assessment
- **Excellent Discrimination:** ROC-AUC of 0.8828 indicates strong ability to distinguish between classes
- **Balanced Performance:** Similar precision and recall suggest no significant bias toward either class
- **Generalization:** CV score (0.8258) vs. test score (0.8828) shows good generalization

### Clinical Relevance
- **High Precision (78.57%):** When model predicts gallstones, it's correct ~79% of the time
- **Good Recall (75.00%):** Model identifies 75% of actual gallstone cases
- **Balanced F1-Score (77.42%):** Good balance between precision and recall

## Saved Results

Results stored in `lr_results` dictionary with the following keys:

- `model`: Trained Logistic Regression model
- `y_pred`: Binary predictions on test set
- `y_pred_proba`: Probability predictions on test set
- `cv_score`: Cross-validation ROC-AUC scores
- `test_accuracy`: Test set accuracy
- `test_precision`: Test set precision
- `test_recall`: Test set recall
- `test_f1`: Test set F1-score
- `test_roc_auc`: Test set ROC-AUC
- `coefficients`: Feature coefficients (importance)
- `confusion_matrix`: Confusion matrix for test predictions

## Key Strengths

✅ **Strong Predictive Performance:** ROC-AUC > 0.88
✅ **Good Generalization:** Consistent CV and test performance
✅ **Interpretable Model:** Clear feature coefficients
✅ **Balanced Metrics:** No significant precision-recall tradeoff
✅ **Clinically Relevant:** CRP and gender as top predictors align with medical knowledge

## Limitations

⚠️ **Linear Assumption:** Assumes linear relationship between features and log-odds
⚠️ **Feature Independence:** May miss complex feature interactions
⚠️ **Sample Size:** Limited by 319 samples (255 training)

## Conclusion

Logistic Regression provides a strong baseline with excellent discrimination (ROC-AUC = 0.8828) and interpretable results. The model successfully identifies key risk factors (CRP, gender) and demonstrates good clinical utility.
