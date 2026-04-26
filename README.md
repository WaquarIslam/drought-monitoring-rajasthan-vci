# 🌾 Drought Monitoring in Rajasthan Using Vegetation Condition Index (VCI)
### Remote Sensing-Based Agricultural Drought Assessment for Early Warning and Food Security Planning

---

## 🔍 Why This Matters

Rajasthan is India's largest state by area and among its most drought-prone, with over **60% of its land classified as arid or semi-arid**. Agricultural drought in Rajasthan does not just affect crop yields — it disrupts rural livelihoods, triggers distress migration, strains food supply chains, and places vulnerable farming households into multi-year poverty traps.

Traditional drought monitoring in India relies heavily on rainfall deficiency thresholds (IMD) and crop-cutting experiments — methods that are slow, spatially coarse, and reactive. **Satellite-derived vegetation indices offer a faster, spatially continuous, and operationally scalable alternative** that can detect drought onset weeks before it appears in administrative reports.

This project develops a VCI-based drought monitoring workflow for Rajasthan — producing district-level drought severity maps that are directly usable by state agriculture departments, disaster management authorities, and food security planners for early response and resource mobilisation.

---

## 📌 Key Outputs

| Output | Description |
|---|---|
| **VCI severity maps** | Spatial classification of drought extent into No Drought / Mild / Moderate / Severe / Extreme categories |
| **District-level summary** | Tabular ranking of districts by drought severity for administrative prioritisation |
| **Seasonal comparison** | Kharif season vegetation stress mapped against baseline variability |
| **IMD alignment** | VCI classes cross-referenced against IMD drought declaration criteria |

> **Headline finding:** *[Insert your result here — e.g. "During the study period, X districts covering approximately Y% of Rajasthan's agricultural area were classified under moderate-to-severe drought, with Z% of that area falling in the highest severity class."]*

---

## 🛰️ Methodology

### What is VCI?
The **Vegetation Condition Index (VCI)** normalises current vegetation greenness (NDVI) against its historical range at a given pixel, isolating the weather-driven component of vegetation stress from structural land cover variation:

```
VCI = 100 × (NDVI_current − NDVI_min) / (NDVI_max − NDVI_min)
```

A VCI of 0 means vegetation is at its historical minimum — extreme stress.  
A VCI of 100 means vegetation is at its historical maximum — optimal conditions.

This makes VCI **directly comparable across different vegetation types and ecological zones** — a critical advantage when monitoring a state as ecologically diverse as Rajasthan, from the Thar Desert in the west to the Aravalli agricultural belt in the east.

### Drought Severity Classification

| VCI Range | Drought Class | Implication for Agriculture |
|---|---|---|
| 0 – 10 | Extreme Drought | Near-total crop failure likely |
| 10 – 20 | Severe Drought | Significant yield loss, livestock stress |
| 20 – 35 | Moderate Drought | Reduced yields, irrigation demand spike |
| 35 – 50 | Mild Drought | Below-average productivity |
| > 50 | No Drought | Normal to good growing conditions |

### Processing Workflow

```
MODIS NDVI (MOD13A1 / 16-day composite)
        ↓
Temporal stack assembly (study period + historical baseline)
        ↓
Per-pixel VCI computation across the seasonal window
        ↓
Drought severity classification (5-class scheme)
        ↓
District-level zonal statistics (% area per class)
        ↓
Severity maps + tabular district rankings
        ↓
Validation against IMD rainfall anomaly records
```

---

## 📂 Repository Contents

```
drought-monitoring-rajasthan-vci/
│
├── Drought_monitoring_Rajasthan.pdf   # Full project report with maps and analysis
├── Waquar_VCI_project.pdf             # Methodology summary and district-level results
├── notebook.ipynb                     # [If applicable] Processing code — VCI computation
│                                      # and classification workflow
└── README.md                          # This file
```

---

## 🗂️ Data Sources

| Dataset | Source | Access |
|---|---|---|
| MODIS MOD13A1 NDVI (500m, 16-day) | NASA LP DAAC | [https://lpdaac.usgs.gov](https://lpdaac.usgs.gov) |
| Administrative boundaries (district) | Survey of India / GADM | [https://gadm.org](https://gadm.org) |
| Rainfall anomaly validation | IMD Gridded Rainfall Data | [https://imdpune.gov.in](https://imdpune.gov.in) |
| Agricultural land mask | ISRO Bhuvan LULC | [https://bhuvan.nrsc.gov.in](https://bhuvan.nrsc.gov.in) |

All datasets used are **freely and publicly available** — the full workflow is reproducible without proprietary data.

---

## 🌐 Relevance to Food Security and Agricultural Disaster Risk

This workflow directly supports decision-making at multiple levels of the food security and DRR system:

**For state agriculture and disaster management departments:**
- Identifies which districts need immediate crop insurance claim processing or input subsidy deployment
- Provides spatial evidence for drought declaration under SDRF/NDRF norms
- Enables objective comparison of severity across districts — replacing subjective field-report aggregation

**For humanitarian and development organisations (FAO, WFP, UNDP, World Bank):**
- Feeds into IPC (Integrated Food Security Phase Classification) evidence base
- Supports WASH and livelihood programme targeting in drought-affected areas
- Provides baseline for multi-year drought trend analysis aligned with CMIP6 projections

**For insurance and index-based agricultural finance (PMFBY, WB Index Insurance):**
- VCI is a validated proxy trigger for parametric crop insurance payouts
- District-level VCI time series enable actuarial drought frequency and severity analysis

**For early warning systems:**
- Near-real-time MODIS composites (16-day) allow drought onset detection 4–6 weeks ahead of administrative declarations
- Scalable methodology applicable to any Indian state or South Asian agricultural system

---

## 🔬 Tools and Technologies

- **Google Earth Engine (GEE)** — cloud-based MODIS data access, temporal stack processing, and zonal statistics
- **ArcGIS / QGIS** — cartographic output and district boundary overlay
- **Python** — numpy, pandas, matplotlib for tabular analysis and charting
- **IMD gridded rainfall data** — validation of VCI against observed precipitation anomalies

---

## 👤 Author

**Waquar Ul Islam**  
MS by Research — Disaster Management, IIT Guwahati (CGPA 9.45)  
PG Diploma in Remote Sensing & GIS — IIRS-ISRO  
GATE Geomatics AIR-185  

🔗 [LinkedIn](https://linkedin.com/in/waquar-ul-islam) · [GitHub](https://github.com/WaquarIslam)  
📧 waquarulislam@gmail.com

---

## 📎 Related Work

This project is part of a broader multi-hazard remote sensing portfolio:

| Repository | Hazard | Method |
|---|---|---|
| [MS-THESIS](https://github.com/WaquarIslam/MS-THESIS) | Urban Flood | Probabilistic risk assessment, SewerGEMS, CMIP6 |
| [Cyclone-Shaheen-Oman-2021](https://github.com/WaquarIslam/Cyclone-Shaheen-Oman-2021-ongoing-project-) | Tropical Cyclone | SAR inundation, IBFWS, MERRA-2 |
| [coastal-inundation-erosion-rs](https://github.com/WaquarIslam/coastal-inundation-erosion-rs) | Coastal Hazard | Shoreline change, SAR |
| [kolahoi-glacier-snow-cover-mapping](https://github.com/WaquarIslam/kolahoi-glacier-snow-cover-mapping) | Cryosphere | Optical RS, snow extent |

---

*Methodology aligned with IMD drought monitoring standards and FAO agricultural drought assessment guidelines.*
