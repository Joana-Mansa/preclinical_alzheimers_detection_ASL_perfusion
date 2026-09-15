# Methodology and limitations

The notebook uses a fixed seed to generate 80 synthetic records with 24 regional features. Amyloid group membership directly changes the simulated feature means. Demographic fields and perfusion values are simulated, not measurements from a clinical cohort.

Regional differences use two-sided Welch t-tests and Cohen’s d with sample-size-weighted pooled variance. P-values are exploratory and unadjusted for multiple regional comparisons. A nonsignificant demographic comparison is not evidence of equivalence or matching.

Five shuffled stratified folds evaluate a pipeline containing StandardScaler and logistic regression. The scaler is fitted only on training subjects. Out-of-fold probabilities produce the ROC and confusion matrix at threshold 0.5. The displayed coefficient plot comes from a separate fit on the full synthetic cohort and is descriptive.

The original notebook scaled before cross-validation and plotted training-set predictions. These have been corrected; old executed outputs were cleared. Current reproducibility evidence is recorded in `results.md`.

Optional Harvard–Oxford plots average left/right synthetic features for mapped bilateral cortical labels. The mapping is illustrative and incomplete; hippocampal and cerebellar features are excluded rather than relabelled as cortical structures. These are not subject-level MRI images or validated anatomical measurements.

To investigate real perfusion data, a separate study would need data access, validated preprocessing, defined reference labels, confounder handling and independent evaluation. The synthetic scores do not answer those questions.
