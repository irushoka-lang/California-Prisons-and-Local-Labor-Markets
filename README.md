# ca-prison-commute-analysis
# Spatial Analysis of California State Prison Commute Patterns

## Overview
This repository contains the spatial analysis codebase examining worker commute patterns across 30 California state prison facilities. Using Census LODES (8.0) Origin-Destination data, TIGER/Line block geometries, and HIFLD facility boundaries, this project calculates weighted average commute distances to test policy claims regarding local hiring and economic impacts on host communities.

## Repository Structure
* `data/raw/`: Contains source files (`prison-boundaries-1-geojson.zip`, `tlgdb_2020_a_06_ca.gdb`, and `LODES8/ca/od`).
* `data/data_dictionary.md`: Variable definitions, data types, and source citations.
* `code/`: Contains the Jupyter/Colab notebook reproducing all spatial joins, weighted distance calculations, and figures.
* `outputs/`: Saved figure visualizations (Graph 1 commute distances, Graph 2 box plots) and summary tables.

## Datasets
1. **Prison Boundaries:** `prison-boundaries-1-geojson.zip`
2. **Census Block Geodatabase:** `tlgdb_2020_a_06_ca.gdb` (2020 California TIGER/Line)
3. **Commute & Employment Data:** `LODES8/ca/od` (LEHD LODES 8.0 California OD data)

## Key Methodological Notes
* **Centroid Measurement:** Distance metrics measure straight-line (Euclidean) distances between Census block centroids and do not represent network driving routes.
* **Locality Benchmark:** A 20-mile threshold is established as a proxy for local commutes, based on regional Southern California transportation literature.
* **Mixed-Site Flag:** Census blocks where Public Administration jobs comprise less than 70% of total block employment are flagged as mixed sites (`is_mixed_site = 1`), requiring cautious interpretation due to potential non-prison employment noise.

## How to Reproduce
1. Clone this repository:
   ```bash
   git clone [https://github.com/YOUR_USERNAME/ca-prison-commute-analysis.git](https://github.com/YOUR_USERNAME/ca-prison-commute-analysis.git)
   cd ca-prison-commute-analysis
