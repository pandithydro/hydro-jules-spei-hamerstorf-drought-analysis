# hydro-jules-spei-hamerstorf-drought-analysis
================================================================================
HYDRO‑JULES SPEI‑6 DROUGHT ANALYSIS FOR THE HAMERSTORF AGRICULTURAL SITE (1981–2022)
================================================================================

PROJECT OVERVIEW

This repository documents a reproducible workflow for extracting, downscaling, and analyzing 6‑month Standardised Precipitation–Evapotranspiration Index (SPEI‑6) data for the Hamerstorf Agricultural Experimental Site in Lower Saxony, Germany.

The analysis uses the Hydro‑JULES Global High‑Resolution Drought Dataset (via CEDA) and applies bilinear interpolation to derive site‑specific SPEI‑6 values relevant for agricultural drought assessment.

STUDY SITE
Name: Hamerstorf Agricultural Experimental Plot
Location: Lower Saxony, Germany
Relevance: Long‑term agricultural research site focused on crop water stress,
soil moisture dynamics, and drought resilience.

DATASET SPECIFICATIONS

Dataset: Hydro‑JULES Global High‑Resolution Drought Dataset (v1 & v2)
Provider: CEDA Archive (UKCEH / Met Office)
Resolution: 0.1 degree (~10 km)
Variable: SPEI‑6 (6‑month SPEI)
Temporal Range: 1981–2022

CEDA Catalogue Links:

https://catalogue.ceda.ac.uk/uuid/ac43da11867243a1bb414e1637802dec/

https://catalogue.ceda.ac.uk/uuid/e652f0109f21401680bc3c0ac834a96e/

WORKFLOW SUMMARY
Programmatic Data Access:
The CEDA catalogue page was scraped using BeautifulSoup to extract the direct download URL for the SPEI‑6 NetCDF file.

Data Loading:
The extracted URL was loaded into Python using the xarray library.

Spatial Downscaling (Bilinear Interpolation):
Bilinear interpolation was applied to compute SPEI‑6 at the exact Hamerstorf plot coordinates.

Seasonal Focus (September SPEI‑6):
Only SPEI‑6 values for the month of September were extracted. September SPEI‑6
represents the cumulative moisture balance from April to September, which aligns
with the main crop growth and irrigation period at the site.

Drought Classification (Dry / Normal / Wet):
September SPEI‑6 values were categorized using the following thresholds:

Dry:    SPEI‑6 <= -1
Normal: -1 < SPEI‑6 < +1
Wet:    SPEI‑6 >= +1

Visualization (2006–2022):
A focused analysis was conducted for the period 2006–2022, capturing key drought
events as shown in the plots
