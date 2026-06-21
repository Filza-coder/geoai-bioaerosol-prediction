# GeoAI-Based Spatial Prediction of Airborne Pollen and Fungal Spore Concentrations
### NUST H-12 Campus, Islamabad, Pakistan — April 2016

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Filza-coder/geoai-bioaerosol-prediction/blob/main/01_data_preparation.ipynb)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

---

## Overview

This repository contains all data, code, and figures for an aerobiological study
investigating the spatial, temporal, and vertical distribution of airborne pollen
and fungal spore concentrations in an urban campus environment.

**Study period:** April 4–20, 2016 (12 sampling days)  
**Location:** NUST H-12 Campus, Islamabad, Pakistan (33.64°N, 72.98°E)  
**Sampling sites:** 6 stations across the campus (3 height levels: 0.91 m, 7.66 m, 15.3 m)  
**Samples collected:** 144 glass rod samples from a custom-built portable sampler  

**Author:** Fatima Filza Hassan  
**Supervisor:** Dr. Salman Atif, IGIS, NUST  
**Degree:** MSc Remote Sensing and GIS, NUST (2017)

---

## Key Findings

| Finding | Result |
|---------|--------|
| Spatial pollen gradient | 5-fold across 1 km (377–1985 grain/m³) |
| Spatial fungal gradient | 3-fold across 1 km (1166–3234 grain/m³) |
| Dominant fungal genera | Aspergillus (44.7%) + Alternaria (18.1%) = 62.8% of total |
| Top LULC predictor | Natural vegetation → Aspergillus & Alternaria (ρ=0.829, p=0.042) |
| Height effect on pollen | −77% from ground (0.91 m) to rooftop (15.3 m), Cohen's d=1.96 |
| Height effect on fungus | −61% from ground to rooftop, Cohen's d=1.43 |
| Top meteorological driver | cos(WD) for Aspergillus; sin(WD) for Alternaria (SHAP analysis) |
| Sampler cost | US$56 per unit vs US$5,500 for commercial Burkard trap |

---

## Repository Structure

```
geoai-bioaerosol-prediction/
│
├── README.md                          ← You are here
├── requirements.txt                   ← Python dependencies
│
├── data/
│   ├── raw/
│   │   ├── complete data.xlsx         ← Met + total pollen/fungus (64 rows, 6 stations × 12 days)
│   │   ├── species data.xlsx          ← Species-level fungal counts (12 sheets, one per date)
│   │   └── building _height.xlsx      ← Building heights across NUST campus
│   └── shapefiles/
│       ├── Vegetation/                ← Natural grassland and shrubs
│       ├── grasslands/                ← Maintained grass fields
│       ├── barren land/               ← Bare/unpaved surfaces
│       ├── constructed feature/       ← Building footprints
│       ├── tree division/             ← Tree point locations (roadside + grass-field)
│       └── Nust.shp + companions      ← Campus boundary shapefile
│
├── notebooks/
│   ├── 01_data_preparation.ipynb      ← Load, clean, volume conversion, LULC features
│   ├── 02_pearson_correlation_timeseries.ipynb  ← Pearson r + time series figures
│   ├── 03_random_forest_permutation_importance.ipynb  ← RF, OLS, LOO-CV, MDI, PI
│   ├── 04_shap_analysis.ipynb         ← SHAP bar + beeswarm directional analysis
│   ├── 05_lulc_spatial_analysis.ipynb ← Spearman ρ with p-values, scatter plots
│   └── 06_height_gradient_analysis.ipynb  ← Power-law decay, Wilcoxon, Cohen's d
│
├── figures/                           ← All publication-quality figures (PNG, 180 dpi)
│   ├── fig1_correlation_heatmap.png
│   ├── fig2_rf_feature_importance.png
│   ├── fig3_observed_vs_predicted.png
│   ├── fig4_aspergillus_vs_alternaria.png
│   ├── fig5_lulc_spearman.png
│   ├── fig6_lulc_scatter.png
│   ├── fig7_timeseries.png
│   ├── figA_spearman_pvalues.png      ← Updated Spearman with p-values
│   ├── figB_ols_vs_rf.png             ← OLS vs RF comparison
│   ├── figC_permutation_importance.png
│   ├── figD_shap.png
│   ├── figE_ranking_table.png
│   ├── figF_obs_pred_enhanced.png
│   ├── figH1_height_gradient.png
│   ├── figH2_paired_height_daily.png
│   ├── figH3_io_penetration.png
│   └── figH4_height_spearman.png
│
└── docs/
    ├── rotorod.png                    ← Custom portable sampler device photos
    └── sampling_sites.png             ← Field deployment at all 6 sites
```

---

## Quick Start

### Option 1 — Run on Google Colab (recommended, no setup needed)

Click any badge below to open directly in Colab:

| Notebook | Description | Open |
|----------|-------------|------|
| 01 Data Preparation | Load data, volume formula, LULC features | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Filza-coder/geoai-bioaerosol-prediction/blob/main/01_data_preparation.ipynb) |
| 02 Pearson Correlation | Heatmap + time series | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Filza-coder/geoai-bioaerosol-prediction/blob/main/02_pearson_correlation_timeseries.ipynb) |
| 03 Random Forest | LOO-CV, MDI, Permutation importance | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Filza-coder/geoai-bioaerosol-prediction/blob/main/03_random_forest_permutation_importance.ipynb) |
| 04 SHAP Analysis | Directional feature effects | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Filza-coder/geoai-bioaerosol-prediction/blob/main/04_shap_analysis.ipynb) |
| 05 LULC Spatial | Spearman ρ with p-values | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Filza-coder/geoai-bioaerosol-prediction/blob/main/05_lulc_spatial_analysis.ipynb) |
| 06 Height Gradient | Power-law decay, Cohen's d | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Filza-coder/geoai-bioaerosol-prediction/blob/main/06_height_gradient_analysis.ipynb) |

**On Colab, run these two cells first in every notebook:**
```python
# 1. Mount your Google Drive (if data is stored there)
from google.colab import drive
drive.mount('/content/drive')

# 2. Install dependencies
!pip install openpyxl geopandas shapely pyproj scikit-learn shap seaborn -q
```

Then update the file path variables at the top of each notebook to point to
where you uploaded the data folder.

### Option 2 — Run locally

```bash
# Clone the repository
git clone https://github.com/Filza-coder/geoai-bioaerosol-prediction.git
cd geoai-bioaerosol-prediction

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook notebooks/01_data_preparation.ipynb
```

> **Run notebooks in order** (01 → 02 → 03 → ...). Notebook 01 generates
> `df_analysis.csv` and `df_lulc.csv` which are required by all subsequent notebooks.

---

## Data Description

### `complete data.xlsx` — Sheet1
64 rows (6 stations × 12 sampling days). Key columns:

| Column | Description | Units |
|--------|-------------|-------|
| Station | Site ID (1–6) | — |
| Date | Sampling date (April 2016) | — |
| pollen_conc | Total pollen concentration | grain/m³ |
| fungus_conc | Total fungal concentration | grain/m³ |
| GHI | Global Horizontal Irradiance | W/m² |
| Tamb | Ambient temperature | °C |
| RH | Relative humidity | % |
| WS | Wind speed | m/s |
| WD | Wind direction | degrees N |
| BP | Barometric pressure | hPa |
| N_pollen | Raw pollen count from microscopy | count |
| N_fungus | Raw fungal count from microscopy | count |

### `species data.xlsx` — 12 sheets (one per sampling date)
Species-level raw counts for: Aspergillus, Alternaria, Drechslera,
Fusarium, Tetraploa, Yeast cells. Columns: Species | S1 | S2 | S3 | S4 | S5 | S6

### Shapefiles — UTM Zone 43N (EPSG:32643)
All polygon and point layers digitised from the NUST campus:

| Layer | Type | Description |
|-------|------|-------------|
| Vegetation | Polygon | Natural grassland and shrubs |
| grasslands | Polygon | Maintained grass fields |
| barren land | Polygon | Unpaved/bare surfaces |
| Buildingsfinal3 | Polygon | Building footprints |
| alongroadsfinal | Point | Trees along roadsides |
| insidegrasstotal | Point | Trees inside grass areas |

---

## Volume Conversion Formula

The key formula converting raw microscopy counts to grain/m³:

```
V (m³) = Rod_area × D × π × RPM × t_sampled

where:
  Rod_area = 0.0015 m × 0.035 m × 2 rods = 1.05 × 10⁻⁴ m²
  D        = 0.1148 m  (rotor head diameter, derived from N/C data pairs)
  RPM      = 2700
  t_sampled = motor-on minutes per session (13–30 min, set by digital timer)

C (grain/m³) = N / V
```

All six stations share the same timer setting on a given day,
so V is **constant across stations within each date**.
See Notebook 01 for the full derivation and verification.

---

## Analysis Summary

### Part A — Temporal (n=64, meteorological drivers)
- **Pearson correlation** between 7 met variables and 4 bioaerosol targets
- **Random Forest regression** with LOO-CV (n_estimators=500)
- **OLS linear regression** with LOO-CV for comparison
- **MDI feature importance** (all data, 500 trees)
- **Permutation importance** (100 repeats, corrects MDI bias)
- **SHAP** via TreeExplainer (directional feature effects)

### Part B — Spatial (n=6 stations, LULC drivers)
- **Spearman rank correlation** with exact p-values for all 20 pairs
- 200 m buffer LULC features computed from campus shapefiles
- 3 of 20 pairs significant at α=0.05 (reported transparently)

### Part C — Height gradient (n=9–11 paired dates)
- **Power-law decay models** C = a × h⁻ᵇ fitted to 3 height levels
- **Wilcoxon signed-rank test** on date-matched ground vs rooftop pairs
- **Cohen's d** effect sizes (all targets: very large, d > 1.1)
- **Rank-biserial correlation** r_rb
- **I/O penetration ratio** (Station 6 window / Station 5 rooftop)

---

## Figures

| Figure | Description |
|--------|-------------|
| `fig1_correlation_heatmap.png` | Pearson r: met variables vs 4 bioaerosol targets |
| `fig2_rf_feature_importance.png` | RF MDI importance (4 targets, LOO-CV R² shown) |
| `fig3_observed_vs_predicted.png` | RF LOO-CV observed vs predicted |
| `fig4_aspergillus_vs_alternaria.png` | Side-by-side importance: Aspergillus vs Alternaria |
| `fig5_lulc_spearman.png` | LULC Spearman ρ heatmap |
| `fig6_lulc_scatter.png` | LULC vs concentration scatter plots |
| `fig7_timeseries.png` | Daily concentration time series (6 stations) |
| `figA_spearman_pvalues.png` | Spearman ρ with exact p-values (all 20 pairs) |
| `figB_ols_vs_rf.png` | OLS vs RF LOO-CV comparison |
| `figC_permutation_importance.png` | MDI vs permutation importance (4×2 comparison) |
| `figD_shap.png` | SHAP bar + beeswarm (directional effects) |
| `figE_ranking_table.png` | Predictor ranking with MDI/PI agreement indicator |
| `figF_obs_pred_enhanced.png` | OLS + RF obs vs pred, coloured by station |
| `figH1_height_gradient.png` | Box plots + power-law decay at 3 heights |
| `figH2_paired_height_daily.png` | Paired daily concentrations at 3 heights |
| `figH3_io_penetration.png` | I/O ratio over time + mean per species |
| `figH4_height_spearman.png` | Spearman: height vs concentration (all 64 obs) |

---

## Sampling Device

A custom low-cost portable volumetric impaction sampler was designed
for this study — based on the Rotorod principle but fabricated locally
at approximately **US$56 per unit** (98% cost reduction vs Burkard trap).

| Spec | Value |
|------|-------|
| Dimensions | 17 × 12 × 6 cm |
| Weight | 500 g |
| Power | 12V rechargeable battery |
| Motor speed | 2700 rpm |
| Duty cycle | 10% (programmable digital timer) |
| Battery life | 7–8 hours per charge |
| Collection rods | 2 × silicon-gel-coated glass (1.5mm × 35mm) |

Device photos: [`docs/rotorod.png`](docs/rotorod.png)  
Field deployment: [`docs/sampling_sites.png`](docs/sampling_sites.png)

---

## Sampling Sites

| Site | Description | Height | Setting |
|------|-------------|--------|---------|
| 1 | University entrance gate | 0.91 m | Outdoor |
| 2 | Open space near lake | 0.91 m | Outdoor |
| 3 | Near residential apartments | 0.91 m | Outdoor |
| 4 | Construction/grid area | 0.91 m | Outdoor |
| 5 | Rooftop (IGIS building) | **15.3 m** | Outdoor |
| 6 | Indoor window (same building as Site 5) | **7.66 m** | Indoor |

Sites 5 and 6 are co-located on the same building, enabling  
paired within-building height comparisons independent of site differences.

---

## Citation

If you use this data or code, please cite:

```
Hassan, F.F. (2017). Spatial Distribution of Bio-Aerosols and Determinant
Factors in a Built Environment. MSc Thesis, Institute of Geographical
Information Systems (IGIS), NUST, Islamabad, Pakistan.

GitHub repository: https://github.com/Filza-coder/geoai-bioaerosol-prediction
```

---

## License

Data and code are released under the
[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) licence.  
You are free to use, adapt, and redistribute with attribution.

---

## Acknowledgements

- **Supervisor:** Dr. Salman Atif, IGIS, NUST
- **Committee:** Dr. Ejaz Hussain, Lecturer Junaid
- **Species identification:** Dr. Mushtaq Ahmed, Dr. Qasim Hayat,
  Dr. Asad Shabbir, Dr. Noreen Akhter (PMD)
- **Field assistance:** Ayesha Khan, Aqsa Anwar
- **Sampler fabrication:** Mr. Ikram Ahmed
- **Meteorological data:** USPCAS-E, NUST (ESMAP Tier-1 programme)
