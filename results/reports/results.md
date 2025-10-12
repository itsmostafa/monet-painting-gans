# Gallstone Disease Prediction: Analysis Summary

## Problem Addressed
- Goal: predict binary gallstone status (0 = no, 1 = yes) for 319 patients described by 38 clinical, laboratory, and body-composition variables.
- Challenges tackled in the notebook: verify data integrity, understand feature distributions/correlations, control multicollinearity, and build models that generalize beyond the training samples.
- Data preparation steps: stratified 80/20 train-test split (255 train / 64 test) to keep the near-even class balance (≈50/50), and StandardScaler fitted on the training data to avoid leakage.

## Machine Learning Approaches
- **Exploratory analysis:** visualized class balance, demographic trends, correlations, and ran significance tests; confirmed the dataset is balanced and identified several significant predictors.
- **Feature selection:** applied ANOVA F-test, Mutual Information, and Random Forest–based Recursive Feature Elimination. A consensus of these methods highlighted 19 high-signal attributes (e.g., C-Reactive Protein, Vitamin D, AST, ECW, HDL, Hemoglobin, Visceral Fat Area) while retaining the full 38-feature set for model comparison.
- **Modeling workflow:** used StratifiedKFold (5-fold) throughout, optimized each model with respect to ROC-AUC, and evaluated both cross-validation and held-out test performance.
  - Logistic Regression (baseline): balanced class weights, grid search over `C` and penalty type, trained on scaled features.
  - Random Forest (ensemble): randomized search across depth, tree count, sampling, and class-weight options, using the same scaled feature set.

## Results
### Logistic Regression (Baseline)
- 5-fold CV (training set): Accuracy 0.741 ± 0.080, Precision 0.767 ± 0.078, Recall 0.684 ± 0.108, F1 0.721 ± 0.090, ROC-AUC 0.826 ± 0.066.
- Held-out test (64 patients): Accuracy 0.781, Precision 0.800, Recall 0.750, F1 0.774, ROC-AUC 0.883.
- Feature signals: strongest positive coefficients for C-Reactive Protein (odds ratio ≈4.63), Intracellular Water, Hyperlipidemia, Age, and Total Body Fat Ratio; strongest negative coefficients for Gender, Bone Mass, AST, Vitamin D, and ECF/TBW.

### Random Forest (Tuned Ensemble)
- 5-fold CV (training set): Accuracy 0.757 ± 0.071, Precision 0.761 ± 0.079, Recall 0.747 ± 0.072, F1 0.753 ± 0.070, ROC-AUC 0.850 ± 0.048 (best average ROC-AUC among the tested models).
- Held-out test (64 patients): Accuracy 0.781, Precision 0.800, Recall 0.750, F1 0.774, ROC-AUC 0.872.
- Feature importance: top contributors include C-Reactive Protein, Vitamin D, ECF/TBW, Extracellular Water, AST, Visceral Muscle Area, Obesity percentage, Creatinine, GFR, ALP, and Lean Mass—closely aligning with the consensus-selected set.

## Key Takeaways
- Both tuned models achieve similar accuracy on the held-out set, but Logistic Regression edges ahead on ROC-AUC (0.883 vs 0.872), suggesting its probabilistic calibration suits this dataset slightly better.
- Random Forest shows stronger cross-validation ROC-AUC, indicating better averaged learning over folds and robustness to feature interactions.
- Consistent high-importance features (CRP, Vitamin D, AST, fluid balance metrics, visceral fat measures, hematological markers) merit clinical focus and could guide streamlined future data collection or diagnostic rules.
- The notebook leaves room to compare the full vs. reduced feature sets; the consensus list of 19 attributes provides a substantial dimensionality reduction (50%) without discarding the variables driving model performance.
