# External Datasets & Large Asset Registry

This directory contains external benchmark datasets, climate reference archives, and records from government and open-source meteorological portals used to evaluate, benchmark, and cross-validate the ResQMesh XGBoost Risk Prediction System.

---

## 1. Large File Advisory (GitHub Storage Compliance)

> [!WARNING]
> **Large File Notice**: In accordance with GitHub's 100 MB single-file limit and repository integrity guidelines, files exceeding 100 MB are not stored directly in this Git repository.

### Excluded Large Archive:
| File Name | Size (Bytes) | Size (MB) | Format | Content & Purpose | Recommended External Hosting |
|---|---|---|---|---|---|
| `archive (2).zip` | 225,187,437 bytes | **214.76 MB** | Compressed ZIP | 809 ground & aerial flood scene imagery files (`.jpg`, `.jpeg`, `.webp`, `.png`) used for multi-modal visual flood confirmation | **Kaggle Datasets** / **Hugging Face Hub** |

#### Recommended Hosting and Access:
To access or deploy the flood imagery archive:
1. **Hugging Face Hub**: Host as a dataset repository under `datasets/resqmesh-flood-imagery`.
2. **Kaggle Datasets**: Host as a public/private Kaggle dataset titled `resqmesh-flood-vision-dataset`.
3. **Local Ingestion**: Place the uncompressed archive directly into `datasets/external/flood_images/` when running local computer vision validation pipelines.

---

## 2. Included External Datasets Index

| Archive / Dataset | Compressed Size | Uncompressed Content | Source & Description |
|---|---|---|---|
| **`archive.zip`** | 28.62 MB | `flood.csv` (2.25 MB)<br>`train.csv` (56.39 MB)<br>`test.csv` (34.43 MB)<br>`sample_submission.csv` (8.53 MB) | **Kaggle Playground Series s4e5 (Flood Prediction Dataset)**.<br>Benchmark dataset comprising 20 environmental and infrastructural risk features across 1,117,957 training samples and 50,000 baseline validation samples. |
| **`flood.csv(1).zip`** | 0.66 MB | `flood.csv` (2.25 MB) | **Flood Factor Dataset**.<br>Contains 50,000 observations of 20 flood risk indicators (Monsoon Intensity, Topography Drainage, River Management, Deforestation, Urbanization, etc.) used for baseline regression and feature attribution. |
| **`archive (1).zip`** / **`archive (4).zip`** | 0.15 MB each | `Indian_Climate_Dataset_2024_2025.csv` (0.58 MB) | **Indian Climate Observation Dataset (2024–2025)**.<br>Daily weather, AQI, temperature, precipitation, and atmospheric pressure records across major Indian cities (Chennai, Mumbai, Delhi, Bengaluru, etc.). |
| **`archive (3).zip`** / **`archive (7).zip`** | 0.82 MB each | `flood_risk_dataset_india.csv` (1.77 MB) | **India National Flood Risk Dataset**.<br>Georeferenced environmental dataset with latitude/longitude coordinates, river discharge, elevation, soil classification, land cover, and historical flood occurrence. |
| **`archive (8).zip`** | 0.19 MB | Bundle of `archive (10).zip` + `archive (11).zip` | Combined archive bundle preserving original collection hierarchy. |
| **`archive (9).zip`** | 0.54 MB | `CORRECTED_2023_2026_NEPAL_FLOOD_WEATHER_KAGGLE.csv` (1.54 MB)<br>`nepal_flood_weather_dataset_kaggle_2023_2026.csv` (1.43 MB) | **Department of Hydrology & Meteorology (DHM) Nepal / Kaggle Dataset**.<br>Regional river basin, elevation, precipitation, and soil moisture telemetry (2023–2026). |
| **`archive (10).zip`** | 0.18 MB | `district wise rainfall normal.csv` (0.07 MB)<br>`rainfall in india 1901-2015.csv` (0.50 MB) | **India Meteorological Department (IMD) / Open Government Data (OGD) India**.<br>115-year historical rainfall records (1901–2015) and district-level monthly rainfall normals. |
| **`archive (11).zip`** | 0.01 MB | `Gov. Climate Datasets (Archive) - List.csv`<br>`Gov_Climate_Datasets_Archive.csv` | **Government Climate Data Repositories Archive Index**.<br>Comprehensive index of global government meteorological datasets (NOAA, DOE/ORNL CDIAC, NASA). |
