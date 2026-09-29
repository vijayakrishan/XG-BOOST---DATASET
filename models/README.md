# ResQMesh Trained Models Registry

This directory contains trained machine learning and gradient boosted decision tree (GBDT) model artifacts, feature configurations, and decision thresholds for the **ResQMesh AI Disaster Risk Prediction System**.

---

## 1. Primary Model Architecture: XGBoost Classifier

### Final Validated Model: `resqmesh_final_validated_model.json`
- **Model Framework**: XGBoost (`xgboost.XGBClassifier`)
- **Format**: Native XGBoost JSON Model Format (portable across Python, C++, Java/XGBoost4J)
- **File Size**: ~1.50 MB
- **Hyperparameter Configuration**:
  - `n_estimators`: 700
  - `max_depth`: 5
  - `learning_rate`: 0.03
  - `subsample`: 0.85
  - `colsample_bytree`: 0.85
  - `min_child_weight`: 3
  - `gamma`: 0.1
  - `reg_alpha`: 0.1
  - `reg_lambda`: 1.0
  - `objective`: `binary:logistic`
  - `eval_metric`: `logloss`
  - `tree_method`: `hist`

### Associated Artifacts:
- **`resqmesh_final_validated_features.json`**: Exact ordered list of 52 physical, meteorological, and temporal features ingested by the model.
- **`resqmesh_final_validated_threshold.json`**: Decision threshold configuration calibrated on the development set for optimal operational trade-off between false alarms and disaster misses.

---

## 2. Experimental & Ablation Models

| Model File | Size | Description |
|---|---|---|
| **`resqmesh_improved_event_xgboost.json`** | 404 KB | Event-aware XGBoost baseline trained on initial event boundaries. |
| **`resqmesh_physical_xgboost.json`** | 1.18 MB | Physical-only feature subset model (excluding atmospheric pressure drops). |
| **`resqmesh_no_calendar_xgboost.json`** | 1.24 MB | Non-temporal model explicitly barring month, day, and hour inputs. |
| **`resqmesh_xgboost_model.json`** | 1.14 MB | Early prototype XGBoost model trained on raw hourly telemetry. |
| **`resqmesh_xgboost_features.joblib`** | 271 B | Pickled feature column order for rapid Python inference. |

---

## 3. Operational Risk Thresholds & Inference

The model outputs a continuous disaster risk probability in the range $[0.0, 1.0]$. The system maps this probability into actionable warning levels:

| Risk Level | Probability Range | Action / Alert Status |
|---|---|---|
| **LOW** | $P < 0.25$ | Routine monitoring; standard mesh ping interval. |
| **MODERATE** | $0.25 \le P < 0.50$ | Heightened advisory; pre-position rescue personnel. |
| **HIGH** | $0.50 \le P < 0.75$ | Warning status; emergency response broadcast over LoRa mesh. |
| **EXTREME** | $P \ge 0.75$ | Evacuation protocol; critical siren alert and survivor beacon priority. |
