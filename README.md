# Tracking Economic Expansion in Portugal using Nighttime Lights (2012 vs 2016)

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Spatial](https://img.shields.io/badge/Domain-Geospatial_Data_Science-success.svg)
![License](https://img.shields.io/badge/License-MIT-lightgrey.svg)

## Project Overview

Nighttime light (NTL) satellite imagery is widely used by economists and data scientists as a highly accurate proxy for urbanization, economic growth, and energy consumption. 

This project maps the regional economic expansion of Portugal over a 4-year period. However, instead of relying on proprietary, black-box platforms like Google Earth Engine, this pipeline was engineered using a **100% open-source, Cloud-Native Geospatial architecture**. By connecting directly to NASA's Global Imagery Browse Services (GIBS) API, the script programmatically fetches, processes, and analyzes high-resolution VIIRS "Black Marble" composites entirely within a local Python environment.

### Why this architecture?
By bypassing Google Earth Engine, this project demonstrates how to build independent, production-ready spatial pipelines that can be deployed on any server without API keys, commercial licensing fees, or cloud-project approvals.

---

## Visual Outputs

*(Add your screenshots here by dragging and dropping them into GitHub, or linking them from a local /images folder)*

### 1. The Interactive Swipe Map (2012 vs 2016)
<img width="935" height="617" alt="Captura de ecrã 2026-04-08 174453" src="https://github.com/user-attachments/assets/43009617-ce0a-4526-b6ca-8ca9cc1c4ed8" />
*Streaming NASA tiles to visually track electrification.*

### 2. Urban Growth Heatmap
<img width="775" height="1191" alt="Captura de ecrã 2026-04-08 174509" src="https://github.com/user-attachments/assets/a226dbf1-8f60-45ee-a665-ffddcc784874" />
*Mathematically isolated zones of rapid infrastructure development.*

### 3. Interactive 3D Topography
<img width="863" height="1199" alt="Captura de ecrã 2026-04-08 174524" src="https://github.com/user-attachments/assets/db25874c-ca41-4f5a-be0a-3b48e3422a25" />
*Light radiance projected onto the Z-axis to visualize urban density.*

### 4. AI-Driven Economic Zones (K-Means Clustering)
<img width="899" height="799" alt="Captura de ecrã 2026-04-08 174535" src="https://github.com/user-attachments/assets/760e3fe5-3def-4d35-a90d-5f76a62db8bf" />
*Unsupervised machine learning segmenting the country into mathematically verified development tiers.*

---

## Key Features & Analytics Modules

1. **Automated Cloud-Native Sourcing:** Bypasses manual GIS downloads by programmatically extracting map tiles via bounding box and stitching them into local Cloud-Optimized GeoTIFFs.
2. **Interactive Temporal Dashboard:** Utilizes `leafmap` to generate a split-panel swipe map, allowing users to visually track electrification between 2012 and 2016.
3. **Urban Growth Heatmap:** Executes pixel-by-pixel raster subtraction (`numpy` + `rasterio`) to mathematically isolate and visualize zones of rapid infrastructure development.
4. **Interactive 3D Topography:** Projects 2D raster arrays into the Z-axis using `plotly`, generating an interactive 3D surface model where the highest peaks represent the densest concentrations of energy consumption.
5. **AI-Driven Economic Zoning:** Deploys Unsupervised Machine Learning (K-Means Clustering) to automatically segment the country into distinct economic development tiers (Stagnant, Developing, Hyper-Growth) based on data variance.

---

## Tech Stack

* **Geospatial Processing:** `leafmap`, `rasterio`
* **Data Mathematics:** `numpy`
* **Visualization:** `matplotlib`, `plotly`
* **Machine Learning:** `scikit-learn` (K-Means)

---

## Installation & Usage

To run this notebook locally, clone the repository and install the required dependencies.

## Pipeline Methodology

* **Data Ingestion:** The script queries the NASA GIBS EPSG:3857 API for the `VIIRS_CityLights_2012` and `VIIRS_Black_Marble` (2016) layers at Zoom Level 8.
* **Cleaning:** A numpy boolean mask is applied to filter out deep oceans and unpopulated forests (pixel intensity < 10), ensuring the math only focuses on human settlements.
* **Difference Calculation:** $\Delta Growth = Raster_{2016} - Raster_{2012}$
* **Visualization Output:** Results are passed to Matplotlib for heatmap generation, Plotly for 3D rendering, and Scikit-Learn for spatial clustering.

## Acknowledgments & Credits

* **NASA EarthData:** For providing open-access to the pre-computed, cloud-free VIIRS Black Marble annual composites.
* **Professor Qiusheng Wu ([GitHub](https://github.com/giswqs))** : A massive thank you for developing the leafmap library, which made building this independent, cloud-native spatial pipeline possible.
