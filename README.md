# drought-monitoring-rajasthan-vci
# Drought Monitoring — Rajasthan using Vegetation Condition Index (VCI)

## What this project does
Detects and maps agricultural drought severity across Rajasthan using the Vegetation Condition Index (VCI) derived from MODIS satellite data. Drought extents are classified into severity categories aligned with IMD drought monitoring standards.

## Key result
[Add one sentence here: e.g. "Identified X% of Rajasthan agricultural area under moderate-to-severe drought conditions during the study period."]

## Methods
- Satellite data: MODIS NDVI (MOD13A1)
- Index: Vegetation Condition Index (VCI = (NDVI - NDVImin)/(NDVImax - NDVImin))
- Classification: IMD drought severity classes
- Tools: Google Earth Engine / ArcGIS / Python

## Data sources
- MODIS Terra vegetation indices: https://lpdaac.usgs.gov/

## Files
- `Drought_monitoring_Rajasthan.pdf` — full project report
- `Waquar_VCI_project.pdf` — methodology and results summary
