# Forest-phenology-monitoring-biomass-estimation-and-driving-force-estimation
 (1) Forest phenology monitoring: extract growing season metrics from time‑series data. (2) Biomass estimation: map above‑ground biomass using remote sensing features via machine learning models. (3) Driving force estimation: quantify contributions of climate, and human activities to phenology and biomass using geographical detectors.

Below is a detailed yet data‑free overview of your research, written as a README section for GitHub. It covers the three main parts you described, without revealing any experimental numbers or specific results.

---

## Overview

This project investigates long‑term forest dynamics through three complementary axes: **phenological change trends**, **aboveground carbon storage estimation**, and **driving force analysis**. Using multi‑source remote sensing data (Landsat‑5/8, Sentinel‑2, MOD09A1, HLS S30, ALOS‑2 PALSAR, and GEDI) over a ~35‑year period, we systematically assess how temperate forests respond to environmental and topographical controls.

### 1. Forest Phenological Change Trends

We extracted four key phenological metrics – start of season (SOS), peak of season (POS), end of season (EOS), and length of season (LOS) – from dense time‑series observations. Our analysis reveals that the observed lengthening of the growing season is primarily driven by a significant delay in autumn senescence rather than by an earlier spring green‑up. Among the sensors tested, the MOD09A1 product shows the most robust and statistically significant trends, while Landsat‑5 data exhibit higher inter‑annual variability and non‑significant tendencies. Importantly, we identify systematic offsets (on the order of several weeks) between different sensor families, highlighting the need for careful cross‑calibration when building long‑term phenological records. The peak of season shows the lowest temporal consistency, suggesting that regional carbon cycle changes are more tightly linked to an extended photosynthetic window in autumn than to a consistent spring advancement.

### 2. Forest Aboveground Carbon Storage

#### 2.1 Feature Importance Analysis
Using the Random Forest algorithm, we combined GEDI biomass density, ALOS‑2 PALSAR polarimetric data, SRTM topography, and multi‑spectral optical imagery (Landsat, Sentinel‑2, HLS S30). The feature importance ranking demonstrates that **topographic factors – especially elevation – are the dominant controllers** of aboveground carbon distribution. Among optical inputs, the harmonised HLS S30 dataset consistently outperforms single‑sensor products. Structural and moisture‑sensitive indices (e.g., SIPI, tasseled cap wetness, and tasseled cap distance) show the highest importance, indicating that multi‑source harmonisation effectively mitigates the saturation problems of traditional vegetation indices in dense canopies.

#### 2.2 Biomass Modeling
We evaluated carbon estimation models across three optical sources (Landsat‑8, Sentinel‑2, HLS S30) under different feature importance thresholds. The HLS S30‑based model achieves the best balance between explanatory power and error control, while Sentinel‑2 performance degrades at stricter thresholds. The optimal configuration (using HLS S30 with a moderate importance threshold) effectively removes redundant variables, enhancing computational efficiency without sacrificing accuracy. The harmonised dataset proves superior for reliable forest carbon stock inversion.

#### 2.3 Seasonal Variations in Carbon Stocks
By separating the growing season (April–November) from the non‑growing season, we find that HLSS30‑derived estimates show remarkable **inter‑seasonal consistency** – average carbon densities and spatial variabilities remain nearly identical between the two periods. This demonstrates that the HLSS30 model, which prioritises structural and topographic features over simple greenness indices, successfully isolates the “physical carbon stock” from “seasonal phenological noise.” In contrast, a satellite embedding approach yields systematically lower carbon densities and higher spatial uncertainty, suggesting that traditional embedding methods may underestimate complex canopy structures. The HLSS30 seasonal models thus provide a robust, mutually reinforcing framework for high‑precision carbon monitoring.

### 3. Trend Analysis and Driving Forces

#### 3.1 Spatial‑Temporal Patterns of Change
Significance analysis of forest aboveground carbon evolution from 2017 to 2024 shows that the study area is dominated by **stable** carbon stocks (>95% of the area). Patches of significant decline are slightly more frequent in the non‑growing season, while increase areas are mostly located in the southern region. The satellite embedding data, however, suggests a much higher proportion of significant changes (both increases and decreases), indicating that embedding‑based approaches may be more sensitive to inter‑annual variability but also potentially noisier. Overall, the spatio‑temporal fluctuations of forest carbon remain minimal, with high seasonal consistency.

#### 3.2 Driving Force Analysis (Geodetector)
We applied geographical detector q‑statistics to quantify the influence of environmental variables on forest aboveground carbon storage. **Elevation consistently emerges as the dominant factor**, with the highest q‑values across all seasons and years. Other important drivers include 2‑metre air temperature and shallow soil moisture (0–10 cm). Variables such as aspect and topographic wetness index show negligible independent effects.

Seasonal contrasts are particularly striking for precipitation: its explanatory power is substantially higher during the non‑growing season, suggesting that water availability during dormancy acts as a critical limiting constraint on ecosystem carbon capacity. Similarly, soil organic carbon exerts a stronger influence in the non‑growing season, when biological activity is low. A comparison between HLSS30 and satellite embedding reveals that the embedding approach captures soil carbon and subtle topographic variations more effectively, while both methods agree on the primacy of elevation and temperature as stable, long‑term environmental filters.

---

**Key take‑away:** The combination of harmonised optical time series (HLS S30), active microwave (ALOS‑2 PALSAR), and waveform lidar (GEDI) – together with careful cross‑sensor calibration – enables a robust, phenology‑aware assessment of forest carbon stocks and their driving forces. This workflow provides a transparent, reproducible basis for long‑term forest monitoring and carbon accounting.
