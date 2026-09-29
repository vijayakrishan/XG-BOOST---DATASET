# Preprocessing & Training Scripts Directory

This directory contains standalone, reproducible Python scripts responsible for data cleaning, telemetry harmonization, lag feature engineering, event-aware dataset partitioning, model training, and threshold calibration for the **ResQMesh AI System**.

---

## 1. Primary Entry Point: `train_model.py`

- **Purpose**: Self-contained, one-command reproducible training and validation pipeline.
- **Workflow Executed**:
  1. Ingests raw hourly Tamil Nadu weather and telemetry records (`datasets/raw/archive (5).zip`).
  2. Generates multi-scale rolling temporal aggregations (3-hour, 6-hour, 12-hour, 24-hour, and 48-hour precipitation sums, temperature moving averages, pressure delta rates).
  3. Partitions samples by verified disaster events (November 2021 statewide flood vs. unseen December 2023 southern district flood).
  4. Trains the production `XGBClassifier` with calibrated hyperparameters.
  5. Calibrates decision thresholds and exports model JSON, feature schemas, and performance reports.
- **Execution Command**:
  ```bash
  python preprocessing/train_model.py
  ```

---

## 2. Modular Preprocessing & Pipeline Scripts

| Script | Purpose |
|---|---|
| `01_inspect_all.py` | Initial audit and schema inspection across all telemetry CSV and archive sources. |
| `02_quality_check.py` | Missing value audit, timestamp continuity verification, and outlier detection. |
| `03_clean_environment.py` | Null interpolation, timestamp synchronization, and telemetry station filtering. |
| `04_prepare_water_level.py` | River gauge height extraction and warning stage classification. |
| `05_combine_environmental_data.py` | Multi-sensor fusion combining rainfall, atmospheric pressure, and river discharge. |
| `06_prepare_rainfall_features.py` | Rolling precipitation accumulations and rainfall anomaly indexing against IMD normals. |
| `17_prepare_xgboost_data.py` | Tabular feature matrix construction and data scaling. |
| `18_train_xgboost.py` | Initial baseline XGBoost model fitting and validation. |
| `19_evaluate_xgboost.py` | Confusion matrix, ROC curve, and classification report generation. |
| `24_prepare_event_training_data.py` | Ingestion and labeling of the November 2021 disaster event. |
| `25_create_event_aware_split.py` | Strict chronological and geographic event separation to prevent data leakage. |
| `26_train_event_xgboost.py` | GBDT model training on event-aware training partition. |
| `35_prepare_final_training_data.py` | Feature selection and multi-district feature matrix assembly. |
| `36_create_event_aware_split.py` | Validation and test partition extraction for the 2023 disaster event. |
| `37_train_improved_xgboost.py` | Regularized tree training with tuned subsampling and child weights. |
| `44_create_temporal_weather_features.py` | Computation of 52 physical and temporal lag features. |
| `45_train_temporal_xgboost.py` | Temporal feature model training with cross-validation. |
| `50_final_validation.py` | Final evaluation on the unseen December 2023 event and export of production artifacts. |
