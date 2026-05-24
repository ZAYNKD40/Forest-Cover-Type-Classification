# Forest Cover Type Classification

UCI Forest Cover Type Dataset · Roosevelt National Forest, Colorado

## Overview
Multi-class classification (7 tree species) on 581,012 cartographic samples using 
elevation, terrain, wilderness area, and soil type features. Built a full ML pipeline 
from EDA through model comparison to deep-dive analysis.

## Results

| Model | Test Accuracy |
|---|---|
| XGBoost | **96.1%** |
| Random Forest | 94.6% |
| Logistic Regression | 72.5% |

## Key Findings
- **Elevation alone (67.3% importance) outperforms all 40 soil-type features combined (60.0%)** — geography beats geology
- Spruce/Fir ↔ Lodgepole Pine is the hardest pair (1,411 misclassifications) due to overlapping elevation bands (~2800–3300m)
- Cottonwood/Willow achieves 86% recall despite being only 0.47% of the dataset — its unique riparian fingerprint (low elevation + water proximity) makes it identifiable
- Learning curve shows no plateau at 280K samples — model is data-hungry, not capacity-limited

## Pipeline
1. EDA — class imbalance analysis, elevation distributions, correlation matrix, wilderness area cover mix
2. Preprocessing — 70/15/15 stratified split, StandardScaler for LR only (tree models are scale-invariant)
3. Logistic Regression baseline
4. Random Forest — feature importance via mean decrease in impurity
5. XGBoost primary model — histogram-based training, early stopping
6. Deep-dive — confusion analysis, elevation vs soil ablation study, per-wilderness accuracy, learning curve

## Tech Stack
Python · pandas · scikit-learn · XGBoost · matplotlib · seaborn

## Dataset
[UCI Forest Cover Type](https://archive.ics.uci.edu/dataset/31/covertype) — 581,012 samples, 54 features, 7 classes

## To view html
[View rendered notebook](https://zaynkd40.github.io/Datathon-2026/forest_cover_rendered.html)
