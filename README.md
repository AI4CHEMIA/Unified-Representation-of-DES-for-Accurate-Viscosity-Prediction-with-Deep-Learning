
# Viscosity-Prediction-for-Deep-Eutectic-Solvents

This repository contains the complete workflow for viscosity prediction in deep eutectic solvents (DESs), integrating systematic data preprocessing, molecular descriptor generation (Mordred–RDKit), and advanced machine learning models. The pipeline spans dataset curation, feature engineering, model training (MLP, Random Forest, XGBoost, and Evidential Deep Learning), and evaluation with cross-validation and uncertainty quantification. It provides a reproducible framework for developing accurate and interpretable property prediction models in complex solvent systems. 

# ✨ Overview
Dataset: 2,229 experimental viscosity records for 183 DES systems (from Yu et al., 2022).
Descriptors: 3,761 molecular features generated using Mordred–RDKit from SMILES retrieved via PubChem PUG REST and CACTUS services.
Final Feature Set: 102 curated descriptors + auxiliary fields after cleaning, outlier removal, and feature selection.

Models:
MLP: Nonlinear regression with dropout, weight decay, and Optuna-based hyperparameter tuning.
DL: Evidential Deep Learning for joint viscosity prediction and uncertainty quantification (Normal–Inverse–Gamma output).
Baselines: Random Forest and XGBoost.
Evaluation: Cross-validation with metrics including R², RMSE, MAE, AARD, and Max ARD.

# 📂 Repository Structure
├── data/                  # Input dataset (curated and raw) \
├── preprocessing/         # Scripts for descriptor generation and feature selection\
├── models/                # MLP, EDL, RF, XGBoost implementations\
├── results/               # Training curves, SHAP analysis, evaluation outputs\
├── figures/               # Framework diagrams and plots\

# ⚙️ Methodology Pipeline
Data Augmentation:
Retrieve SMILES → RDKit 3D structure → Mordred descriptors (3,761).
Merge with raw data (109 columns → 3,761 features).

Preprocessing & Feature Selection:
Cleaning: remove constants/duplicates, impute gaps.
Outlier removal: 20 extreme viscosity points.
Reduction: variance/correlation filters.
Selection: ensemble ranking (RF, F-score, MI, SHAP).
Final: 102 descriptors across constitutional, topological, charge, autocorrelation, VSA, and physicochemical categories.

Modeling:
MLP with ReLU, dropout, Adam, Bayesian tuning.
EDL with evidential outputs (μ, ν, α, β).
RF/XGBoost as deterministic baselines.

Evaluation Metrics:
R², RMSE, MAE, AARD, Max ARD. 
