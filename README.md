# Weather Radar Data Processing System

A comprehensive Python toolkit for processing weather radar data from VOL files to NetCDF format and generating rainfall estimates for the Kolkata region.

## Overview

This system processes raw radar volume files (.vol) from the India Meteorological Department's Doppler Weather Radar and converts them into standardized NetCDF format for analysis and visualization.

It includes tools for:

- Converting VOL files to NetCDF format
- Processing radar data to extract rainfall estimates
- Creating visualizations and maps
- Generating CSV and JSON outputs for further analysis

---

# System Requirements

- Python 3.8 or higher
- Git
- Windows/Linux/macOS
- At least 4GB RAM (8GB recommended)
- 1GB free disk space

---

# Installation Guide

## 1. Clone the Repository

```bash
git clone https://github.com/AbhinavKumar-Jha/weather-radar-processing.git
cd weather-radar-processing
```

---

## 2. Set Up Python Virtual Environment

### Windows

```bash
python -m venv .venv
.venv\Scripts\activate
```

### Linux/macOS

```bash
python3 -m venv .venv
source .venv/bin/activate
```

---

## 3. Install Dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

If `requirements.txt` is missing:

```bash
pip install numpy pandas xarray netcdf4 matplotlib plotly folium cartopy scipy wradlib
```

---

# Required Dependencies

```txt
numpy>=1.21.0
pandas>=1.3.0
xarray>=0.19.0
netcdf4>=1.5.7
matplotlib>=3.4.0
plotly>=5.0.0
folium>=0.12.0
cartopy>=0.20.0
scipy>=1.7.0
wradlib>=1.19.0
```

---

# Project Structure

```bash
weather-radar-processing/
├── README.md
├── requirements.txt
├── voltonc.py
├── processnc.py
├── findcord.py
├── visualization.py
├── data/
├── output/
└── .venv/
```

---

# Usage Guide

## Step 1: Convert VOL Files to NetCDF

```bash
python voltonc.py
```

### Expected VOL File Naming Convention

- `2025042623000000V.vol`
- `2025042623000000W.vol`
- `2025042623000000dBZ.vol`

### What This Does

- Parses binary VOL radar files
- Extracts reflectivity data
- Converts radar coordinates into geographic coordinates
- Saves processed data as NetCDF

---

## Step 2: Process NetCDF Data

```bash
python processnc.py
```

### What This Does

- Reads NetCDF radar data
- Selects lowest elevation sweep
- Applies Marshall-Palmer Z-R relationship
- Calculates rainfall rates
- Generates CSV and JSON outputs

---

# Configuration

## Radar Location Settings

```python
processor = RadarVolumeProcessor(
    radar_lat=22.5697,
    radar_lon=88.3697,
    max_range_km=250
)
```

---

# Z-R Relationship Options

```python
zr_relation = 'tropical'
```

Available:
- `marshall_palmer`
- `tropical`
- `convective`
- `stratiform`

---

# Output Files

## CSV Files

- Radar rainfall estimation data
- Statistical summaries

## JSON Files

- Structured API-ready weather data
- GeoJSON geographic mapping data

## Visualization Files

- Static weather plots
- Interactive maps
- Weather dashboards

---

# Data Format

## CSV Output

```csv
latitude,longitude,altitude,reflectivity_dbz,rainfall_rate_mm_hr
22.5697,88.3697,45.2,25.3,2.15
```

---

## JSON Output

```json
[
  {
    "latitude": 22.5697,
    "longitude": 88.3697,
    "reflectivity": 25.3,
    "rainfall_rate": 2.15
  }
]
```

---

# Troubleshooting

## Common Issues

### Missing wradlib

```bash
pip install wradlib
```

### NetCDF File Not Found

- Ensure VOL files are present
- Run `voltonc.py` first

### Virtual Environment Not Activated

#### Windows

```bash
.venv\Scripts\activate
```

#### Linux/macOS

```bash
source .venv/bin/activate
```

---

# Data Source

- India Meteorological Department (IMD)
- Kolkata Doppler Weather Radar
- Coverage Radius: 250 KM

---

# Internship Project Information

## Organization

India Meteorological Department (IMD)  
Regional Meteorological Centre (RMC), Kolkata

## Project Name

**Vrishti**

## Internship Duration

May 2025 – June 2025

---


- Abhinav Kumar Jha


---

# Contributions

## Abhinav Kumar Jha

- Radar Data Processing
- Frontend Development
- Reflectivity Mapping
- JSON Formatting
- Visualization Integration
- Backend Support
- API Development
- Database Integration

---

# Future Improvements

- Real-time radar processing
- AI rainfall prediction
- Interactive GIS integration
- Radar animation support
- Cloud deployment

---

# License

This project was developed for educational and research purposes during the internship at IMD RMC Kolkata.

---

# Quick Start

```bash
git clone https://github.com/AbhinavKumar-Jha/weather-radar-processing.git

python -m venv .venv

# Windows
.venv\Scripts\activate

# Linux/macOS
source .venv/bin/activate

pip install -r requirements.txt

python voltonc.py

python processnc.py
```