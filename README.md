# 🌾 Drought Monitoring in Rajasthan Using Vegetation Condition Index (VCI)
### Remote Sensing-Based Agricultural Drought Assessment — IIRS-ISRO Practical Work

---

## 📋 About This Work

This analysis was completed as part of the **Post Graduate Diploma in Natural Hazards and Disaster Risk Management (PGD-NHDRM), 2021–22** at the **Indian Institute of Remote Sensing (IIRS), ISRO**, under the guidance of **Scientist Abhishek Danodia, Agriculture & Soils Department, IIRS**.

The practical applied the Vegetation Condition Index (VCI) to map and compare agricultural drought severity across Rajasthan for the Kharif season (July–September) of **2002 (declared drought year)** against **2003 (near-normal year)** — using a 20-year NDVI baseline dataset provided by IIRS.

This repository documents the methodology, outputs, and district-level results of that analysis. A planned extension of this work — covering 2000–2024 using Google Earth Engine and validated against IMD drought declarations — is noted in the roadmap section below.

---

## 🔍 Why Drought Monitoring Matters

Rajasthan is India's largest state by area and among its most drought-prone, with over **60% of its land classified as arid or semi-arid**. Agricultural drought in Rajasthan does not just affect crop yields — it disrupts rural livelihoods, triggers distress migration, strains food supply chains, and places vulnerable farming households into multi-year poverty traps.

Traditional drought monitoring relies heavily on rainfall deficiency thresholds (IMD) and crop-cutting experiments — methods that are slow, spatially coarse, and reactive. **Satellite-derived vegetation indices offer a faster, spatially continuous alternative** capable of detecting drought onset weeks before it appears in administrative reports. VCI-based monitoring is operationally used by NRSC-ISRO's MNCFC (Mahalanobis National Crop Forecast Centre) and state agriculture departments for kharif crop assessment.

---

## 📌 Key Outputs

| Output | Description |
|---|---|
| **VCI classified maps** | Spatial classification of Rajasthan into No Drought / Moderate Drought / Severe Drought — 6 maps across July, August, September for 2002 and 2003 |
| **District mean VCI table** | Quantitative VCI means for all **33 Rajasthan districts** × 3 months × 2 years — enabling district-level severity ranking |
| **District mean maps** | Choropleth maps showing district-averaged drought class for each month-year combination |
| **Year comparison** | Side-by-side visual contrast of 2002 (drought) vs 2003 (near-normal) vegetation condition |

> **Key finding:** In July 2002, Rajasthan experienced widespread severe drought — particularly in the north and northwest. Districts with the lowest mean VCI scores in July 2002 include **Hanumangarh (11.2)**, **Churu (15.4)**, **Ganganagar (17.8)**, and **Jhunjhunun (12.3)**, indicating extreme vegetation stress. Across all three Kharif months of 2002, **Jhunjhunun recorded the lowest cumulative VCI**, identifying it as the most severely drought-affected district that year. By contrast, **Pratapgarh** in southern Rajasthan showed the least drought impact. The 2003 analysis confirms near-normal conditions across most of the state, validating the 2002 event as an anomalous drought year detectable through VCI.

---

## 🛰️ Methodology

### What is VCI?

The **Vegetation Condition Index (VCI)** normalises current vegetation greenness (NDVI) against its long-term historical range at each pixel, isolating the weather-driven component of vegetation stress from underlying structural differences in land cover:

```
VCI = 100 × (NDVIj − NDVImin) / (NDVImax − NDVImin)
```

Where NDVImax and NDVImin are calculated from the long-term record for the same calendar month, and j is the index of the current month being assessed.

- **VCI → 0:** vegetation at its historical minimum — extreme stress, likely crop failure
- **VCI → 100:** vegetation at its historical maximum — optimal growing conditions

This normalisation makes VCI **comparable across Rajasthan's diverse ecological zones** — from the hyper-arid Thar Desert in the west to the more productive Aravalli belt and southeastern agricultural districts.

### Drought Severity Classification (3-class scheme used in this study)

| VCI Range | Drought Class |
|---|---|
| 0 – 35 | Severe Drought |
| 35 – 50 | Moderate Drought |
| > 50 | No Drought |

### Processing Workflow (tools used: ERDAS IMAGINE + ArcMap)

```
20-year NDVI stack (provided by IIRS, Agriculture & Soils Dept.)
        ↓
ERDAS IMAGINE Model Maker:
  — Stack MAX and Stack MIN computed per month across 20-year baseline
  — VCI formula applied per pixel: (NDVIj − Min) / (Max − Min) × 100
  — Output classified into 3 drought severity classes
        ↓
ArcMap: classified VCI rasters opened and cartographically mapped
        ↓
Zonal Statistics (Spatial Analyst):
  — Rajasthan district boundary shapefile overlaid
  — District mean VCI computed for each month × year combination
        ↓
6 VCI severity maps + 6 district mean maps + full district VCI table
```

---

## 📊 District Mean VCI Table — Full Results (2002 vs 2003)

The table below contains the complete district-level mean VCI values extracted for all 33 Rajasthan districts across both study years. Lower values indicate more severe drought stress.

| District | Jul 2002 | Aug 2002 | Sep 2002 | Jul 2003 | Aug 2003 | Sep 2003 |
|---|---|---|---|---|---|---|
| Jaisalmer | 27.0 | 20.4 | 18.5 | 44.0 | 70.9 | 80.6 |
| Bikaner | 24.3 | 15.7 | 19.1 | 31.1 | 45.5 | 67.3 |
| Ganganagar | 17.8 | 13.0 | 19.8 | 43.2 | 55.6 | 60.6 |
| Hanumangarh | 11.2 | 10.4 | 19.4 | 29.9 | 58.3 | 71.1 |
| Churu | 15.4 | 6.9 | 16.7 | 12.7 | 56.7 | 69.0 |
| Jhunjhunun | 12.3 | 9.3 | 10.4 | 25.6 | 70.5 | 57.2 |
| Sikar | 23.1 | 22.5 | 18.7 | 47.4 | 74.7 | 52.7 |
| Alwar | 22.4 | 37.4 | 51.1 | 53.5 | 80.6 | 66.7 |
| Bharatpur | 19.7 | 44.4 | 80.9 | 48.9 | 80.5 | 56.2 |
| Dhaulpur | 27.2 | 52.6 | 68.9 | 62.4 | 72.4 | 44.7 |
| Jaipur | 20.5 | 30.1 | 40.7 | 61.5 | 79.0 | 71.2 |
| Dausa | 21.1 | 32.4 | 52.2 | 50.7 | 79.6 | 65.2 |
| Karauli | 27.1 | 27.3 | 51.5 | 53.6 | 84.9 | 71.2 |
| Sawai Madhopur | 31.5 | 20.0 | 35.6 | 32.7 | 69.7 | 65.9 |
| Tonk | 23.7 | 23.5 | 31.4 | 56.5 | 81.5 | 81.9 |
| Bundi | 30.1 | 25.8 | 45.2 | 42.4 | 55.8 | 55.5 |
| Kota | 37.6 | 33.1 | 54.6 | 53.1 | 60.7 | 65.0 |
| Baran | 24.8 | 35.1 | 48.9 | 54.6 | 57.1 | 50.3 |
| Jhalawar | 39.3 | 66.5 | 89.5 | 85.4 | 81.9 | 71.0 |
| Chittaurgarh | 31.5 | 58.1 | 69.6 | 70.5 | 76.2 | 54.4 |
| Bhilwara | 20.8 | 41.3 | 45.5 | 65.1 | 72.2 | 64.4 |
| Pratapgarh | 36.9 | 74.3 | 91.4 | 88.2 | 83.1 | 76.9 |
| Udaipur | 36.8 | 54.7 | 74.3 | 81.1 | 72.4 | 66.4 |
| Dungarpur | 35.6 | 54.1 | 72.8 | 91.4 | 89.2 | 66.0 |
| Banswara | 41.1 | 63.1 | 83.3 | 89.0 | 86.1 | 62.0 |
| Ajmer | 16.7 | 23.3 | 26.6 | 60.3 | 82.4 | 65.8 |
| Nagaur | 18.6 | 13.3 | 22.4 | 39.7 | 67.8 | 64.7 |
| Jodhpur | 22.6 | 15.2 | 23.1 | 37.3 | 67.0 | 70.7 |
| Pali | 29.6 | 17.7 | 37.3 | 74.1 | 77.3 | 81.1 |
| Sirohi | 38.7 | 34.1 | 57.3 | 84.8 | 75.9 | 75.2 |
| Jalor | 23.0 | 15.9 | 35.6 | 75.5 | 73.7 | 78.2 |
| Barmer | 26.1 | 17.8 | 25.7 | 52.2 | 71.8 | 78.5 |
| Jalore | 23.0 | 15.9 | 35.6 | 75.5 | 73.7 | 78.2 |

> The spatial pattern is clear: **northern and northwestern Rajasthan (Thar Desert fringe and Shekhawati region) experienced the most intense and persistent drought stress in 2002**, while southern districts (Pratapgarh, Dungarpur, Banswara) showed relative resilience — consistent with their higher rainfall climatology. By 2003, the spatial pattern largely reversed, confirming the 2002 drought as a climatically driven anomaly rather than a structural land degradation signal.

---

## 📂 Repository Contents

```
drought-monitoring-rajasthan-vci/
│
├── Drought_monitoring_Rajasthan.pdf   # Practical report — VCI maps and district analysis
├── Waquar_VCI_project.pdf             # Extended results — district mean maps and table
└── README.md                          # This file
```

---

## 🗂️ Data

| Dataset | Description |
|---|---|
| NDVI 20-year stack | Provided by IIRS Agriculture & Soils Department for the practical exercise |
| Rajasthan district boundaries | Standard administrative shapefile used for zonal statistics in ArcMap |

> **Note on data sourcing:** The NDVI dataset used in this practical was provided by IIRS-ISRO as part of the structured coursework. For the planned GEE extension (see roadmap), MODIS MOD13A1 will be accessed directly from [NASA LP DAAC](https://lpdaac.usgs.gov) — publicly and freely available.

---

## 🔬 Tools Used

| Tool | Purpose |
|---|---|
| **ERDAS IMAGINE** (Model Maker) | VCI formula implementation — batch processing of Stack MAX, Stack MIN, and per-pixel classification across all months |
| **ArcMap** (ArcGIS 10.x) | Cartographic output, district boundary overlay, zonal statistics |

---

## 🌐 Broader Relevance — Why This Method Matters

The VCI approach applied in this practical is operationally relevant across multiple levels of drought response in India and South Asia:

**State agriculture and SDMA departments:**
- District-level VCI maps provide spatial evidence for drought declaration under SDRF/NDRF norms
- Enable objective cross-district severity ranking to guide input subsidy and relief deployment

**National operational monitoring (NRSC-ISRO, MNCFC):**
- VCI is a core index in India's National Agricultural Drought Assessment and Monitoring System (NADAMS)
- This methodology directly mirrors what is applied operationally at national scale

**Humanitarian and development organisations (FAO, WFP, UNDP):**
- District-level VCI data feeds into IPC (Integrated Food Security Phase Classification) evidence gathering
- Used for livelihood and food security programme geographic targeting

**Index-based agricultural insurance (PMFBY):**
- VCI is a validated proxy trigger for parametric crop insurance payouts at district and sub-district level

---

## 🚧 Planned Extension — Upgrading to an Independent Research Project

This IIRS practical covers two years (2002–2003) and three Kharif months. The following extensions are planned to develop this into a full independent drought trend analysis:

- [ ] **Re-implement in Google Earth Engine (GEE)** using MODIS MOD13A1 — self-sourced, reproducible, cloud-based
- [ ] **Extend temporal coverage to 2000–2024** — enabling long-term trend detection across 24 Kharif seasons
- [ ] **Add IMD declared drought year validation** — cross-reference VCI spatial patterns against official state drought declarations
- [ ] **Add crop yield correlation** — compare district VCI to ICRISAT/state agriculture department yield statistics for Kharif crops
- [ ] **Python notebook** — reproduce district mean table and charts in pandas/matplotlib for full reproducibility
- [ ] **Rabi season analysis** — extend beyond Kharif to capture wheat and mustard crop stress in winter months

> When complete, this extension will stand as an independent multi-year drought monitoring study. The IIRS practical (2021) will serve as its documented baseline and methodological precursor.

---

## 👤 Author

**Waquar Ul Islam**
MS by Research — Disaster Management, IIT Guwahati (CGPA 9.45)
PG Diploma in Natural Hazards & DRM (Remote Sensing & GIS) — IIRS-ISRO
GATE Geomatics AIR-185
NASA ARSET: Fundamentals of ML for Earth Science · EO for Humanitarian Applications

🔗 [LinkedIn](https://linkedin.com/in/waquar-ul-islam) · [GitHub](https://github.com/WaquarIslam)
📧 waquarulislam@gmail.com

---

## 📎 Related Work — Multi-Hazard Remote Sensing Portfolio

| Repository | Hazard / Domain | Core Method |
|---|---|---|
| [MS-THESIS](https://github.com/WaquarIslam/MS-THESIS) | Urban Flood | Probabilistic risk assessment, SewerGEMS, CMIP6 |
| [Cyclone-Shaheen-Oman-2021](https://github.com/WaquarIslam/Cyclone-Shaheen-Oman-2021-ongoing-project-) | Tropical Cyclone | SAR inundation, IBFWS, MERRA-2 reanalysis |
| [coastal-inundation-erosion-rs](https://github.com/WaquarIslam/coastal-inundation-erosion-rs) | Coastal Hazard | Sentinel-1 SAR, NDWI change detection, Bangladesh coast |
| [kolahoi-glacier-snow-cover-mapping](https://github.com/WaquarIslam/kolahoi-glacier-snow-cover-mapping) | Cryosphere | Optical RS, NDSI, snow cover extent |

---

*Analysis conducted at IIRS-ISRO (2021–22) using methodology consistent with NRSC-ISRO's National Agricultural Drought Assessment and Monitoring System (NADAMS) and FAO agricultural drought monitoring guidelines.*
