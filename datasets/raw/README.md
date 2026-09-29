# Raw Datasets Registry

This directory contains the original, unaltered raw sensor telemetry and meteorological datasets used as the primary source data for the **ResQMesh XGBoost Disaster Risk Prediction System**.

---

## 1. Raw Telemetry & Weather Datasets Index

| File / Archive | Size | Format | Primary Agency / Source | Description |
|---|---|---|---|---|
| **`pressure_tel_hr_tamil-nadu-sw-gw_tn_2021_2021.csv`** | 0.89 MB | CSV | Tamil Nadu Surface Water & Ground Water (SW-GW) Dept / India-WRIS | Hourly atmospheric barometric pressure telemetry across Tamil Nadu telemetry stations for calendar year 2021. |
| **`pressure_tel_hr_tamil-nadu-sw-gw_tn_2022_2022.csv`** | 34.74 MB | CSV | Tamil Nadu SW-GW Dept / India-WRIS | Hourly barometric pressure telemetry across Tamil Nadu telemetry stations for calendar year 2022. |
| **`pressure_tel_hr_tamil-nadu-sw-gw_tn_2023_2023.csv`** | 44.89 MB | CSV | Tamil Nadu SW-GW Dept / India-WRIS | Hourly barometric pressure telemetry across Tamil Nadu telemetry stations for calendar year 2023 (including the Dec 2023 Southern TN extreme event). |
| **`pressure_tel_hr_tamil_nadu_sw_gw_tn_2026_2030.csv`** | 38.42 MB | CSV | Tamil Nadu SW-GW Dept / India-WRIS | Standardized telemetry stream records and sensor format projections for Tamil Nadu stations. |
| **`rainfall_tel_hr_tamil_nadu_sw_gw_tn_2026_2030.csv`** | 2.16 MB | CSV | Tamil Nadu SW-GW Dept / India-WRIS | Hourly telemetry rainfall monitoring stream for Tamil Nadu stations. |
| **`wind_speed_manual_twicedaily_tamil_nadu_sw_gw_tn_1970_2025.csv`** | 0.19 MB | CSV | Tamil Nadu SW-GW Dept / India-WRIS | Long-term twice-daily surface wind speed monitoring series (1970–2025). |
| **`wind_speed_manual_twicedaily_tamil_nadu_sw_gw_tn_2026_2030.csv`** | 230 B | CSV | Tamil Nadu SW-GW Dept / India-WRIS | Sensor telemetry station header and schema definition record. |
| **`archive (5).zip`** | 33.79 MB | ZIP (`TNweather_1.8M.csv` - 162.16 MB uncompressed) | Open-Meteo Historical Archive / ERA5 Reanalysis | Continuous hourly weather observations (temperature, relative humidity, dew point, precipitation, surface pressure, cloud cover, wind speed, wind direction) across all 37 districts of Tamil Nadu (~1.88 million rows). |
| **`archive (6).zip`** | 9.21 MB | ZIP (`terrain_dataset.csv` + imagery) | Field Telemetry / Disaster Survey | Multi-modal terrain telemetry containing tri-axial accelerometer (`Accel_X, Y, Z`), gyroscope (`Gyro_X, Y, Z`), vibration sensors, and photographic ground terrain classifications (Rocky, Sandy, Marsh, Waterlogged). |
| **`flood.csv`** | 2.25 MB | CSV | Environmental Disaster Risk Benchmark | Uncompressed 50,000-row tabular benchmark dataset containing 20 physical and anthropogenic flood factors, directly runnable by `notebooks/flood-prediction-model.ipynb`. |

---

## 2. Integrity & Preservation Standards

- **Zero Alteration**: All CSV and ZIP files in this folder are bit-for-bit identical to their source inputs.
- **Header & Column Preservation**: No columns have been renamed, removed, or type-coerced in these raw files.
- **Reproducibility**: Preprocessing scripts under `preprocessing/` read directly from these raw sources to produce the artifacts under `datasets/processed/`.
