# Road Corridor Building Density and Accessibility Analysis

## Project Overview
This project analyses the spatial relationship between the road network and building
footprints in a residential area in the Netherlands (approximately Tilburg region),
using OpenStreetMap (OSM) data. The analysis quantifies building accessibility to
roads by classifying every building based on its distance to the nearest road segment.

---

## Study Area
- **Location:** Netherlands (approx. Tilburg region)
- **Coordinate Reference System:** EPSG:28992 — Amersfoort / RD New (metric)
- **Source Data CRS:** EPSG:4326 (WGS 84)
- **Road features:** 43
- **Building footprints:** 561

---

## Analysis Steps

### 1. Reprojection
Both input layers were reprojected from EPSG:4326 to EPSG:28992 (RD New) to enable
accurate metric distance calculations.

### 2. Multi-Ring Road Buffers
Three concentric buffer rings (50 m, 100 m, 150 m) were generated around all road
segments to visualise proximity corridors.

### 3. Distance to Nearest Road & Accessibility Classification
Each building was assigned to its nearest road segment using the Distance to Nearest
Hub algorithm. Buildings were then classified into four categories:

| Class                 | Distance Threshold | Count | Share  |
|-----------------------|--------------------|-------|--------|
| Directly Accessible   | <= 50 m            | 109   | 19.4%  |
| Moderately Accessible | 51-100 m           | 69    | 12.3%  |
| Accessible            | 101-200 m          | 168   | 29.9%  |
| Isolated              | > 200 m            | 215   | 38.3%  |

---

## Output Files

| File                          | Type    | Description                                       |
|-------------------------------|---------|---------------------------------------------------|
| `buildings_28992.gpkg`        | Vector  | Building polygons reprojected to EPSG:28992        |
| `roads_28992.gpkg`            | Vector  | Road lines reprojected to EPSG:28992               |
| `road_buffers_multiring.gpkg` | Vector  | Multi-ring buffers (50/100/150 m) per road segment |
| `buildings_classified.gpkg`   | Vector  | Buildings with AccessClass and HubDist fields      |
| `Road_Corridor_Analysis.qgz`  | Project | QGIS project file (all layers, styles, CRS)       |
| `README.md`                   | Text    | This documentation file                           |

---

## Symbology
- **Buildings Classified:** Categorised by AccessClass
  - Green  — Directly Accessible (<= 50 m)
  - Orange — Moderately Accessible (51-100 m)
  - Blue   — Accessible (101-200 m)
  - Red    — Isolated (> 200 m)
- **Road Buffers:** Semi-transparent concentric rings at 50/100/150 m
- **Roads:** Dark solid lines (EPSG:28992)

---

## Key Finding
Of the 561 buildings, 38.3% are Isolated (>200 m from any road), while only 19.4%
are Directly Accessible (<= 50 m), suggesting a dispersed settlement pattern with
significant gaps in road coverage across the study area.

---

## Tools & Environment
- **Software:** QGIS 3.x
- **CRS (Analysis):** EPSG:28992 — Amersfoort / RD New
- **Data Source:** OpenStreetMap (OSM)
- **Analysis Date:** 2026-05-07

---

## Reproducibility Notes
- All source layers and outputs are stored in this folder.
- The .qgz project uses relative paths — the folder can be moved as a unit.
- Re-run the analysis by executing the PyQGIS steps in order with the MCP server.
