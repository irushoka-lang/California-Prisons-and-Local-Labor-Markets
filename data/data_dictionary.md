data/data_dictionary.md
# Data Dictionary: California Prison Commute Spatial Analysis

This document describes the datasets and key variables used in analyzing commute distances for workers at California state prisons.

---

## 1. Primary Input Datasets

### A. Prison GeoJSON Data
* **Filename / Source:** `prison-boundaries-1-geojson.zip` (HIFLD / California Department of Corrections and Rehabilitation)
* **Description:** Geospatial boundaries and spatial point locations for correctional facilities across California.

### B. California Census Block Geodatabase
* **Filename / Source:** `tlgdb_2020_a_06_ca.gdb` (US Census Bureau TIGER/Line 2020)
* **Description:** Topologically Integrated Geographic Encoding and Referencing (TIGER) geodatabase containing Census block boundaries and centroids for California.

### C. LEHD Origin-Destination Employment Statistics (LODES)
* **Directory / Source:** `LODES8/ca/od` (US Census Bureau LEHD LODES 8.0)
* **Description:** Origin-Destination (OD) job flow data linking home Census blocks (`h_geocode`) to work Census blocks (`w_geocode`).

---

## 2. Key Derived & Analysis Variables

| Variable Name | Data Type | Source | Description & Units |
| :--- | :--- | :--- | :--- |
| `w_geocode` | String (15-digit) | LODES / TIGER | Workplace Census Block GEOID |
| `h_geocode` | String (15-digit) | LODES / TIGER | Home Census Block GEOID |
| `S000` | Integer | LODES WAC / OD | Total number of jobs for the workplace-home Census block pair |
| `CNS20` | Integer | LODES WAC | Public Administration sector jobs in workplace block |
| `CNS07` | Integer | LODES WAC | Trade, Transportation, and Utilities sector jobs in workplace block |
| `distance_miles` | Numeric | Spatial Join | Straight-line distance between work and home block centroids (Miles) |
| `weighted_mean_commute` | Numeric | Calculated | Weighted average commute distance for a prison site (Miles) |
| `is_mixed_site` | Boolean | Calculated | Flag (`1` or `0`) for blocks where Public Administration jobs comprise < 70% of total jobs |
| `pub_admin_pct` | Numeric | LODES WAC | Proportion of total block jobs categorized under Public Administration (%) |
