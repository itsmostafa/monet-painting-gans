# Model Performance Metrics

## Cell 60

**Context:** 5.1 Define Hyperparameter Grid

```
Hyperparameter Grid for Logistic Regression:
======================================================================
  C           : [0.001, 0.01, 0.1, 1, 10, 100, 1000]
  penalty     : ['l1', 'l2']
  solver      : ['liblinear']
  max_iter    : [10000]

Total hyperparameter combinations: 14
======================================================================

Logistic Regression initialized with:
  - random_state: 42
  - class_weight: 'balanced' (automatic adjustment for class imbalance)

Cross-validation strategy:
  - Method: StratifiedKFold
  - Number of folds: 5
  - Shuffle: True
  - Maintains class proportions in each fold
======================================================================

```

## Cell 63

**Context:** 5.5 Evaluate on Training Set (Cross-Validation)

```
======================================================================
CROSS-VALIDATION PERFORMANCE (Training Set)
======================================================================

Cross-validation results (5-fold):
  Accuracy:  0.7412 ± 0.0798
  Precision: 0.7668 ± 0.0781
  Recall:    0.6837 ± 0.1080
  F1-Score:  0.7210 ± 0.0896
  ROC-AUC:   0.8258 ± 0.0655

✓ Cross-validation evaluation complete
======================================================================

```

## Cell 65

**Context:** 5.6 Evaluate on Test Set

```
======================================================================
TEST SET PERFORMANCE (Held-Out Data)
======================================================================

Test set performance metrics:
  Accuracy:  0.7812
  Precision: 0.8000
  Recall:    0.7500
  F1-Score:  0.7742
  ROC-AUC:   0.8828

Classification Report:
======================================================================
               precision    recall  f1-score   support

No Gallstones       0.76      0.81      0.79        32
   Gallstones       0.80      0.75      0.77        32

     accuracy                           0.78        64
    macro avg       0.78      0.78      0.78        64
 weighted avg       0.78      0.78      0.78        64

======================================================================
✓ Test set evaluation complete
======================================================================

```

## Cell 67

**Context:** 5.7 Confusion Matrix

```

Confusion Matrix Breakdown:
  True Negatives (TN):  26 - Correctly predicted No Gallstones
  False Positives (FP): 6 - Incorrectly predicted Gallstones
  False Negatives (FN): 8 - Missed Gallstones cases
  True Positives (TP):  24 - Correctly predicted Gallstones

✓ Confusion matrix generated
======================================================================

```

## Cell 75

**Context:** 5.11 Save results in a dictionary for later comparison

```
======================================================================
SECTION 5 COMPLETE - Logistic Regression Model
======================================================================

✓ Model Training Summary:
  - Best hyperparameters: C=1, penalty=l2
  - Total combinations tested: 14
  - Cross-validation folds: 5

✓ Performance Metrics:
  - CV ROC-AUC:    0.8258
  - Test ROC-AUC:  0.8828
  - Test Accuracy: 0.7812
  - Test F1-Score: 0.7742

✓ Feature Importance:
  - Top positive predictor: C-Reactive Protein (CRP)
  - Top negative predictor: Gender

✓ Results saved in 'lr_results' dictionary
  - Keys: ['model', 'y_pred', 'y_pred_proba', 'cv_score', 'test_accuracy', 'test_precision', 'test_recall', 'test_f1', 'test_roc_auc', 'coefficients', 'confusion_matrix']

======================================================================
READY FOR NEXT MODEL (Section 6: Random Forest)
======================================================================

```

## Cell 82

**Context:** 6.5 Evaluate on Training Set (Cross-Validation)

```

======================================================================
CROSS-VALIDATION PERFORMANCE (Training Set)
======================================================================
Accuracy:  0.7569 ± 0.0708
Precision: 0.7607 ± 0.0785
Recall:    0.7465 ± 0.0722
F1-Score:  0.7526 ± 0.0701
ROC-AUC:   0.8503 ± 0.0481

```

## Cell 84

**Context:** 6.6 Evaluate on Test Set

```

======================================================================
TEST SET PERFORMANCE (Held-Out Data)
======================================================================
Accuracy:  0.7812
Precision: 0.8000
Recall:    0.7500
F1-Score:  0.7742
ROC-AUC:   0.8721

Classification Report:
               precision    recall  f1-score   support

No Gallstones       0.76      0.81      0.79        32
   Gallstones       0.80      0.75      0.77        32

     accuracy                           0.78        64
    macro avg       0.78      0.78      0.78        64
 weighted avg       0.78      0.78      0.78        64


```

