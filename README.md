# Florida Red Tide Precursor Detection
**Author:** Trish Lueck | St. Petersburg, FL  
**Status:** Initial development complete March 2026

## Overview
Early warning system for *Karenia brevis* harmful algal blooms in Tampa Bay 
using compound multi-parameter precursor signal detection on publicly available 
NOAA buoy data. 

## Key Results
- 4.9x discrimination ratio between pre-bloom and normal conditions
- Precursor signal detects bloom conditions **6–8 weeks before onset**
- Validated against 3 independent bloom events (2020, 2021, 2022)
- 2021 severe bloom linked to Piney Point anthropogenic nutrient loading — 
  highlights limitations of climatological signals alone for anomalous discharge events

## Data Sources
- NOAA CO-OPS API — Buoy 8726520, St. Petersburg FL (2020–2024)
- FWC HAB Monitoring Database — *Karenia brevis* bloom event records

## Methods
- 32,681 hourly observations across 4 environmental parameters
- 72-hour rolling averages: water temperature, air temperature, 
  barometric pressure, wind speed
- Compound threshold detector:
  - Water temp ≥ 28°C
  - Wind speed < 3.5 m/s  
  - Barometric pressure 1015–1020 mb
- Isolation Forest anomaly detection (scikit-learn)

## Repository Contents
- `noaa_buoy_exploration.ipynb` — full analysis notebook, fully reproducible
- `README.md` — this file

## How to Run
```bash
git clone https://github.com/trish-labs/florida-hab-detection.git
cd florida-hab-detection
python -m venv env
env\Scripts\activate
pip install numpy pandas matplotlib jupyterlab scikit-learn requests
jupyter lab
```
Open `noaa_buoy_exploration.ipynb` and run all cells.

## Future Work
- Incorporate nutrient loading data (nitrogen/phosphorus) from USGS and 
  Tampa Bay Estuary Program
- Multi-station sensor fusion across Tampa Bay buoy network
- Wildlife telemetry cross-validation using sea turtle and manatee 
  stranding records from FWC
- Extend historical record to capture additional bloom cycles

## Anomaly Worth Investigating
A strong compound precursor signal cluster appeared in **late summer 2023** 
with no corresponding recorded bloom event. This may indicate an unreported 
bloom, primed-but-untriggered conditions, or altered bay chemistry following 
the 2021 Piney Point discharge. Cross-referencing FWC HAB database underway.
