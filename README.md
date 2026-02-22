# hydro-jules-spei-hamerstorf-drought-analysis
# Hydro‑JULES SPEI‑6 Drought Analysis: Hamerstorf Site

This repository documents a reproducible workflow for extracting, downscaling, and analyzing **6‑month Standardised Precipitation–Evapotranspiration Index (SPEI‑6)** data for the **Hamerstorf Agricultural Experimental Site** in Lower Saxony, Germany.

The analysis uses the Hydro‑JULES Global High‑Resolution Drought Dataset to derive site‑specific values relevant for agricultural drought assessment.

## Source Information
- **Source:** [CEDA Archive](https://archive.ceda.ac.uk/) (UKCEH / Met Office)
- **Dataset:** Hydro‑JULES Global High‑Resolution Drought Dataset (v1 & v2)
- **CEDA Catalogue Links:**
  - [Version 1 (1901-2019)](https://catalogue.ceda.ac.uk/uuid/ac43da11867243a1bb414e1637802dec/)
  - [Version 2 (up to 2022)](https://catalogue.ceda.ac.uk/uuid/e652f0109f21401680bc3c0ac834a96e/)

## Study Site: Hamerstorf
- **Location:** Lower Saxony, Germany
- **Type:** Agricultural Experimental Plot
- **Relevance:** Focused on long-term research regarding crop water stress, soil moisture dynamics, and drought resilience.

## Dataset Specifications
- **Variable:** SPEI‑6 (6‑month accumulation period)
- **Resolution:** 0.1 degree (~10 km)
- **Temporal Range:** 1981–2022
- **Data Format:** NetCDF (.nc) accessed via Python

## Workflow Summary
The analysis follows these technical steps:

1. **Programmatic Data Access**  
   Automated scraping of the CEDA catalogue using `BeautifulSoup` to extract direct download URLs for the NetCDF files.
   
2. **Spatial Downscaling (Bilinear Interpolation)**  
   The `xarray` library is used to apply bilinear interpolation. This method uses the four nearest grid points to compute the exact SPEI‑6 value for the Hamerstorf coordinates.

3. **Seasonal Focus**  
   Extraction of **September SPEI‑6** values. This specific month represents the cumulative moisture balance from April to September, aligning with the primary German crop growth and irrigation period.

4. **Drought Classification**  
   The years are categorized (dry, wet and normal) based on standard thresholds:
   - **DRY:** SPEI‑6 ≤ −1
   - **NORMAL:** −1 < SPEI‑6 < +1
   - **WET:** SPEI‑6 ≥ +1

## Key Drought Events (2006–2022)
The analysis identifies and visualizes critical periods for the site. These events are illustrated in the generated plots.
