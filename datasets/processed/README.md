# Processed & Cleaned Datasets Registry

This directory contains cleaned, feature-engineered, and event-partitioned datasets produced by the preprocessing pipeline for training and validating the **ResQMesh XGBoost Risk Prediction System**.

---

## 1. Processed Datasets Index

| Dataset File | Size | Role in Pipeline | Description |
|---|---|---|---|
| **`tamil_nadu_flood_events.csv`** | 18 KB | Disaster Catalog | Ground truth flood disaster event catalog spanning Tamil Nadu (including Nov 2021 statewide flood and Dec 2023 southern district deluge). |
| **`tamil_nadu_district_rainfall_normals.csv`** | 360 B | Baseline Normals | IMD-derived long-term monthly rainfall baseline normals for all Tamil Nadu districts used to calculate precipitation anomalies. |
| **`tamil_nadu_historical_rainfall_summary.csv`** | 256 B | Baseline Summary | Statistical summary of historical rainfall distributions across Tamil Nadu. |
| **`train_event_aware.csv`** | 3.11 MB | Training Data | Event-aware training split constructed from the November 2021 statewide flood event (10,944 samples: 2,736 flood, 8,208 normal). |
| **`test_event_aware.csv`** | 0.34 MB | Unseen Testing | Out-of-event test split constructed strictly from the unseen December 2023 southern districts flood event (1,152 samples: 288 flood, 864 normal). |
| **`event_aware_train.csv`** / **`event_aware_test.csv`** | 2.57 MB / 0.27 MB | Training & Testing | Intermediate event-aware feature sets with standardized temporal lag windows. |
| **`flood_weather_matched.csv`** | 0.86 MB | Environmental Alignment | Hourly weather sensor observations timestamp-matched to verified flood occurrence windows. |
| **`environmental_combined.csv`** | 1.06 MB | Multi-Sensor Fusion | Harmonized environmental telemetry combining rainfall, temperature, barometric pressure, and water level measurements. |
| **`water_level_labeled.csv`** | 0.49 MB | River Telemetry | River gauge height and discharge measurements labeled with critical warning threshold crossings. |
| **`water_level_target_ready.csv`** | 0.46 MB | River Target Set | Filtered river gauge dataset formatted for downstream binary hazard classification. |
| **`future_risk_dataset.csv`** | 0.64 MB | Forecasting Set | Forward-looking risk evaluation partition for multi-hour lead-time flood prediction. |
| **`prototype_training_dataset.csv`** | 0.50 MB | Prototype Baseline | Early prototype training matrix used for initial hyperparameter exploration. |
| **`xgboost_train.csv`** | 0.32 MB | XGBoost Training | Feature-selected tabular training matrix containing calibrated features ready for `XGBClassifier`. |
| **`xgboost_test.csv`** | 0.06 MB | XGBoost Test | Feature-selected tabular test matrix for validation and confusion matrix generation. |
| **`feature_group_comparison.csv`** | 491 B | Ablation Study | Comparative experimental results across raw environmental, temporal lag, and hybrid feature groupings. |
| **`resqmesh_final_validation_results.csv`** | 508 B | Threshold Calibration | Comprehensive precision, recall, F1, and balanced accuracy scores across multiple decision thresholds. |
| **`resqmesh_final_unseen_test_results.csv`** | 272 B | Evaluation Metrics | Final performance scores on the strictly unseen 2023 disaster event (`ROC-AUC = 90.77%`). |

---

## 2. Event-Aware Splitting Methodology

To prevent data leakage and artificial temporal memorization, datasets are split by **distinct meteorological disaster events** rather than random shuffling:
- **Development Event (Train/Val)**: November 6–8, 2021 (Tamil Nadu statewide depression and flood).
- **Unseen Test Event (Evaluation)**: December 18–20, 2023 (Historic southern Tamil Nadu cloudburst and river surge across Thoothukudi, Tirunelveli, Tenkasi, and Kanyakumari).
