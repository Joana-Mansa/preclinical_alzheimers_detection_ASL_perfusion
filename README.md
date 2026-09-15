# 🧠 Synthetic ASL Perfusion Analysis

A reproducible analysis of **simulated** cerebral blood flow in 80 adults across 24 brain regions. It demonstrates group comparisons, effect sizes, plots and cross-validated classification. No patient MRI data are used.

## Run the notebook

```bash
git clone https://github.com/Joana-Mansa/preclinical_alzheimers_detection_ASL_perfusion.git
cd preclinical_alzheimers_detection_ASL_perfusion
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter lab alzheimer-asl-perfusion.ipynb
```

Or run the complete core analysis without a browser:

```bash
jupyter nbconvert --to notebook --execute alzheimer-asl-perfusion.ipynb --output asl-executed.ipynb
```

The core workflow generates its own data and needs no dataset download. Optional atlas figures require `requirements-atlas.txt`, internet access and `ASL_ENABLE_ATLAS=1` in the notebook process environment.

## What it produces

| Output under `outputs/` | Meaning |
|---|---|
| `subject_data.csv` | Synthetic cohort, seed 42 |
| `statistical_results.csv` | Regional Welch tests and pooled-variance Cohen’s d |
| `metrics.json` | Cross-validation and out-of-fold AUC |
| `fig1_*`, `fig2_*`, `fig3_*` | Simulated group differences and correlations |
| `fig7_classification.png`, `fig8_confusion_matrix.png` | Out-of-fold predictions; coefficients are descriptive full-data estimates |

[Methodology and limitations](docs/methodology.md) · [Verified example results](docs/results.md)

## Interpretation

Group differences are deliberately built into the generator. Perfect or near-perfect separation reflects that design and **does not demonstrate a diagnostic biomarker**. Scaling is fitted within training folds; ROC/confusion plots now use out-of-fold predictions rather than training predictions.

**Joana Owusu-Appiah** · [LinkedIn](https://www.linkedin.com/in/joana-owusu-appiah-msc-8751a9166/) · [Medium](https://joo-mansa.medium.com/)
