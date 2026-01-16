# Preclinical Alzheimer's Detection Using ASL Perfusion MRI

**CBF Biomarkers in Amyloid-Positive Cognitively Normal Adults**

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

Alzheimer's disease (AD) pathology begins **15–20 years before clinical symptoms**. During this "preclinical" phase, individuals accumulate amyloid-β plaques while remaining cognitively normal. This project demonstrates how **Arterial Spin Labeling (ASL) MRI** can serve as a non-invasive biomarker for detecting preclinical AD by measuring regional cerebral blood flow (CBF) differences between amyloid-positive and amyloid-negative cognitively normal adults.

### Why ASL-MRI?

| Modality | Invasiveness | Cost | Radiation | Availability |
|----------|--------------|------|-----------|--------------|
| Amyloid PET | Low | High | Yes | Limited |
| CSF Biomarkers | High | Moderate | No | Moderate |
| **ASL-MRI** | **None** | **Low** | **No** | **Wide** |

ASL-MRI offers a compelling alternative for large-scale screening and longitudinal monitoring.

## Hypothesis

Amyloid-positive individuals show reduced CBF in AD-signature regions:
- Posterior cingulate cortex (PCC)
- Precuneus
- Hippocampus
- Medial temporal lobe

These regions overlap with the default mode network and show the earliest AD pathology.

## Methods

### Dataset

**Synthetic cohort** of 80 cognitively normal older adults (age 55–85) with:
- Demographics (age, sex, education)
- Amyloid PET status (SUVR values)
- Regional CBF values from 24 brain regions
- Cognitive scores (MMSE, MoCA, CDR = 0)

CBF patterns are modeled based on published literature (Binnewijzend 2013, Mattsson 2014, Michels 2016). This synthetic dataset is designed to demonstrate the analysis pipeline and expected patterns; real-world data will exhibit greater variability and more modest effect sizes.

### Analysis Pipeline

1. **Group Comparison**: Welch's t-tests comparing CBF between Aβ+ and Aβ- groups
2. **Effect Size Calculation**: Cohen's d for each brain region
3. **Classification**: Logistic regression using AD-signature region CBF
4. **Visualization**: Brain surface maps, statistical plots, ROC curves

## Results

### Key Findings

Amyloid-positive subjects show significant hypoperfusion in:

| Region | CBF Reduction | Cohen's d |
|--------|---------------|-----------|
| Precuneus | ~18% | 2.61 |
| Hippocampus | ~20% | 2.30 |
| Posterior Cingulate | ~17% | 2.28 |

### Classification Performance

- ROC-AUC: 1.000
- Cross-validation AUC: 1.000 ± 0.000

> ⚠️ **Important Note on Performance**: The perfect classification performance is a direct result of using synthetic data with clearly defined group differences. In real clinical settings, expect substantially lower performance due to biological variability, imaging noise, comorbidities, and the subtle nature of preclinical changes. Published studies using real ASL data typically report AUC values in the 0.70–0.85 range for similar classification tasks.

## Installation

```bash
# Clone the repository
git clone https://github.com/Joana-Mansa/preclinical_alzheimers_detection_ASL_perfusion.git
cd preclinical_alzheimers_detection_ASL_perfusion

# Install dependencies
pip install nibabel nilearn matplotlib seaborn pandas numpy scipy scikit-learn
```

## Usage

Run the Jupyter notebook:

```bash
jupyter notebook alzheimer-asl-perfusion.ipynb
```

Or execute all cells to generate:
- Statistical analysis results (`outputs/statistical_results.csv`)
- Subject-level data (`outputs/subject_data.csv`)
- Visualization figures (`outputs/fig*.png`)

## Project Structure

```
├── alzheimer-asl-perfusion.ipynb    # Main analysis notebook
├── README.md
└── outputs/
    ├── subject_data.csv             # Simulated subject data
    ├── statistical_results.csv      # Regional CBF statistics
    ├── fig1_cbf_by_amyloid.png      # Group comparison plots
    ├── fig2_effect_sizes.png        # Cohen's d by region
    ├── fig4_brain_slices.png        # Anatomical visualization
    ├── fig5_glass_brain.png         # Glass brain projection
    ├── fig6_surface_map.png         # Cortical surface maps
    ├── fig7_classification.png      # ROC curve
    └── fig8_confusion_matrix.png    # Classification results
```

## Clinical Implications

ASL-MRI offers potential as a non-invasive screening tool for:
- Identifying individuals at elevated AD risk
- Enriching clinical trials with preclinical AD subjects
- Monitoring disease-modifying therapy response
- Complementing amyloid PET in multimodal assessment

## References

1. Binnewijzend MAA et al. (2013). Cerebral blood flow measured with 3D pCASL MR imaging in Alzheimer disease and MCI. *Radiology*, 267(1), 221-230.

2. Mattsson N et al. (2014). Association of brain amyloid-β with cerebral perfusion and structure in Alzheimer's disease and MCI. *Brain*, 137(5), 1550-1561.

3. Mutsaerts HJMM et al. (2020). ExploreASL: An image processing pipeline for multi-center ASL perfusion MRI studies. *NeuroImage*, 219, 117031.

## Author

**Joana Owusu-Appiah**  
MSc Medical Imaging and Applications | Erasmus Mundus Scholar  
[LinkedIn](https://www.linkedin.com/in/joana-owusu-appiah-8751a9166/) · [Medium](https://joo-mansa.medium.com/) · [ORCID](https://orcid.org/0009-0002-5498-7608)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

*This analysis demonstrates ASL-MRI methodology for preclinical AD research, relevant to multimodal biomarker development programs such as AMYPAD.*
