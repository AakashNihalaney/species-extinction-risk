# Predicting Species Extinction Risk Using Environmental and Anthropogenic Indicators

**Virginia Tech | Business Intelligence & Analytics**  
**Team 04:** Shreyas Desai, Aakash Nihalaney, Anrunya Patole, Harsh Sahu

---

## Overview

This project applies machine learning and statistical modeling to predict species extinction risk based on environmental, biological, and anthropogenic variables. Using a synthetically generated but ecologically grounded dataset of 1,885 species records, we built and compared four classification models to identify the most vulnerable species and support conservation prioritization.

---

## Research Question

Which environmental and human-driven factors most significantly predict species extinction risk, and which modeling approach best supports conservation decision-making?

---

## Dataset

- **Size:** 1,885 species records, 14 variables
- **Target variable:** Extinction Risk (binary: 0 = not at risk, 1 = at risk)
- **Generated using:** Generative AI techniques to simulate realistic ecological conditions
- **Tool:** JMP 18.0.2

**Key predictors:**

| Variable | Type |
|---|---|
| Pollution Level (0–100) | Numerical |
| Illegal Wildlife Trade Rate (0–100) | Numerical |
| Food Availability (0–100) | Numerical |
| Human Population Density (People/km²) | Numerical |
| Species Reproduction Rate (Births/year) | Numerical |
| Climate Change Impact (%) | Numerical |
| Protected Area Presence (0/1) | Binary |
| Invasive Species Presence (0/1) | Binary |
| Region | Categorical |

---

## Methods

- **Exploratory Data Analysis** — variable distributions, scatterplot matrix
- **Interdependence Analysis** — PCA (4 components retained, ~65% variance) and clustering (hierarchical + k-means)
- **Dependence Analysis** — logistic regression, decision tree
- **Model Comparison** — logistic regression, neural network, SVM, stacking ensemble evaluated by AUC and lift curves

---

## Key Findings

**Six predictors consistently drove extinction risk across all models:**
Pollution Level, Human Population Density, Illegal Wildlife Trade Rate, Climate Change Impact, Protected Area Presence, and Invasive Species Presence.

**Decision tree thresholds with conservation policy implications:**
- Pollution Level ≥ 66.95 → elevated extinction risk
- Population Density > 35.9 people/km² combined with high pollution → sharply increased risk
- Protected Area Presence = 1 → significant risk reduction

**Model performance (AUC):**

| Model | Training AUC | Validation AUC |
|---|---|---|
| Logistic Regression | 0.722 | 0.696 |
| Neural Network | 0.743 | 0.707 |
| SVM | 0.723 | 0.696 |
| Stacking Ensemble | **0.746** | **0.702** |

The stacking ensemble achieved the best overall performance. The neural network led on validation lift in the top 10% of ranked predictions, making it particularly effective for prioritizing the most at-risk species with limited conservation resources.

---

## Repository Structure

```
species-extinction-risk/
│
├── FinalReport_Team04.pdf          # Full project report
│
├── DataExp_PR2.jrn                 # JMP journal: data exploration
├── Dependence_PR2.jrn              # JMP journal: logistic regression & decision tree
├── Interdependane_PR2.jrn          # JMP journal: PCA and clustering
├── JournalPR3_Team04.jrn           # JMP journal: model comparison (NN, SVM, ensemble)
│
├── Model_Comparison.xlsx           # AUC and lift summary across all models
├── ROC_Lift_LR.xlsx                # ROC and lift data: logistic regression
├── ROC_Lift_NN.xlsx                # ROC and lift data: neural network
├── ROC_Lift_SVM.xlsx               # ROC and lift data: SVM
└── ROC_Lift_Ensemble.xlsx          # ROC and lift data: stacking ensemble
```

> **Note:** The raw JMP data file (`DataFinal_Team04.jmp`) is excluded from this repository as it is a proprietary binary format. The `.jrn` journal files require **JMP 18.0.2** to reproduce the analysis.

---

## Tools & Software

- **JMP 18.0.2** — primary analysis platform (EDA, modeling, clustering, PCA)
- **Microsoft Excel** — ROC/Lift curve visualization and model comparison tables

---

## References

1. Cardillo et al. (2005). Multiple causes of high extinction risk in large mammal species. *Science*, 309(5738), 1239–1241.
2. Purvis et al. (2000). Predicting extinction risk in declining species. *Proceedings of the Royal Society B*, 267(1456), 1947–1952.
3. Böhm et al. (2016). Threats to the world's freshwater biodiversity. *Conservation Letters*, 9(2), 80–89.
4. Davidson et al. (2012). Drivers and hotspots of extinction risk in marine mammals. *Proceedings of the Royal Society B*, 279(1730), 2197–2205.
5. Di Marco et al. (2014). Quantifying the relative importance of global conservation strategies. *Nature Communications*, 5, 1–8.
