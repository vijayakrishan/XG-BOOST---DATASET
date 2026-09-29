# Notebooks Directory

This directory contains Jupyter notebooks documenting exploratory data analysis (EDA), statistical investigations, and machine learning model training workflows for the **ResQMesh Flood Risk Prediction System**.

---

## 1. Notebooks Index

### `flood-prediction-model.ipynb`
- **File Size**: ~2.04 MB
- **Execution State**: Complete with pre-rendered execution outputs, visualizations, and metrics.
- **Workflow Highlights**:
  1. **Dataset Loading**: Ingests `datasets/raw/flood.csv` (supports local relative pathing as well as Kaggle cloud environments).
  2. **Exploratory Data Analysis**: 
     - Summary statistics and distributions across 20 environmental and anthropogenic risk drivers (Monsoon Intensity, Topography Drainage, River Management, Deforestation, Urbanization, Climate Change, Dams Quality, Siltation, Agricultural Practices, Encroachments, Ineffective Planning, Political Factors, Drainage Systems, Coastal Vulnerability, Landslides, Watersheds, Deteriorating Infrastructure, Population Score, Wetland Loss, Inadequate Infrastructure).
     - Pearson and Spearman correlation analysis with `FloodProbability`.
     - Regression scatter plots with regression trendlines.
  3. **Multi-Model Benchmark**:
     - **Decision Tree Regressor**: Baseline non-linear model.
     - **Random Forest Regressor**: 100 estimators, MAE evaluation, ROC-AUC curve analysis ($AUC = 0.88+$), feature importance ranking barplots.
     - **XGBoost Regressor (`XGBRegressor`)**: 500 estimators, learning rate 0.05, max depth 6, subsample 0.8, colsample 0.8. Achieves **MAE = 0.0062** on test partition.
  4. **Interactive Risk Inference**: Defines an operational `predict_flood_risk(features_dict)` scoring function.
  5. **Advanced Spatio-Temporal Extensions**: Prototypes ConvLSTM deep learning weather forecast models and interactive Folium geospatial risk mapping.

---

## 2. Execution Instructions

To run this notebook locally:
```bash
cd notebooks
jupyter notebook flood-prediction-model.ipynb
```
The notebook automatically detects `../datasets/raw/flood.csv` without requiring any manual dataset path configuration.
