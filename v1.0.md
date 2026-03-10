# HHVI–TPV (Urban Climate) Reproducibility Repository

This Zenodo repository provides the reproducibility materials for the manuscript submitted to *Urban Climate* and is referenced in the Data and Code Availability statement.

It accompanies the manuscript:

**Thermal–Psychosocial Vulnerability and Urban Heat Risk in Inner-City Guangzhou, China**  
**Authors:** Xiaoyi Su; Yong Sun  
**Journal:** *Urban Climate* (submitted)

It documents:

- **(i)** the city-wide quantitative workflow (HHVI construction, diagnostics, robustness tests, temporal comparison, and TPV overlap analysis), and  
- **(ii)** the qualitative coding scheme used to operationalise the TPV lens, together with illustrative coded excerpts provided for transparency and methodological auditability.

> **Note**  
> TPV is used as a *lens* in the manuscript. Materials in this repository operationalise the TPV lens for analysis and do **not** constitute a standalone theoretical framework.

---

## How to cite

If you use or adapt materials from this repository, please cite:

Su, X., & Sun, Y. (2026). *HHVI–TPV reproducibility materials for "Thermal–Psychosocial Vulnerability and Urban Heat Risk in Inner-City Guangzhou, China"* (Urban Climate, submitted). Zenodo.  
https://doi.org/10.5281/zenodo.18299360

---

## Quick start (reproducibility workflow)

1. Scripts in `1_Code/` reproduce the core quantitative workflows defined in Appendix Table S0 (A; E; G; G-R robustness; H). Additional diagnostics (B–D, F) are documented through deposited outputs and Appendix tables.

   Diagnostic analyses corresponding to Experiments **B–D and F** are archived as final output tables (CSV) rather than executable scripts.  
   The repository provides scripts necessary to reproduce the **main analytical pipeline** of the study, while diagnostic tables are included as deposited outputs for transparency.

2. All scripts are executed in **Google Earth Engine (JavaScript)**.

3. Exported outputs in `2_Data/` provide the numerical outputs used for reporting (see Appendix Table S0 for file-to-result anchors).

This workflow reproduces all quantitative outputs reported in the manuscript and appendices.

---

## Repository structure

```text
HHVI-TPV_UrbanClimate_Reproducibility/
├── README.md
├── LICENSE.txt
├── Supplementary_Material_(File_S9).pdf
│
├── 1_Code/
│   ├── HHVI_2023_Main.js
│   ├── HHVI_TemporalChange.js
│   ├── HHVI_SummaryStats_2019_2023.js
│   ├── HHVI2023_TPVOverlap_CAV2.js
│   └── HHVI2023_TPVOverlap_CAV2-robustness.js
│
├── 2_Data/
│   ├── HHVI_2023_main_30m_Guangzhou.tif
│   ├── HHVI_2023_coverage_30m_Guangzhou.tif
│   ├── Guangzhou_HHVI_2019_30m.tif
│   ├── Guangzhou_HHVI_2023_30m.tif
│   ├── Guangzhou_dHHVI_2019_2023_30m.tif
│   ├── HHVI_SummaryStats_2019_2023.csv
│   ├── Guangzhou_TPVOverlap_2023_stack.tif
│   ├── Guangzhou_TPVOverlap_2023_Summary.csv
│   ├── HHVI2023_WeightSensitivity_SOR.csv
│   ├── HHVI2023_SmoothSensitivity_stats.csv
│   ├── HHVI2023_CAV3_CorrelationTest.csv
│   ├── HHVI_LCZ_zonal_2023_stratified.csv
│   ├── HHVI_LCZ_pixels_2023_stratified.csv
│   └── TPVOverlap_Robustness.csv
│
├── 3_Documentation/
│   ├── 1-Reproducibility_Index.pdf
│   ├── 2-Quantitative_Appendix.pdf
│   └── 3-Qualitative_Appendix.pdf
│
└── 4_Qualitative_materials/
    ├── TPV Coding Scheme for Qualitative Analysis.pdf
    └── Example_Coded_Excerpts (TPV Qualitative Analysis).pdf 
```
---

## Authoritative data declaration (final vs. intermediate outputs)

To avoid ambiguity where multiple HHVI rasters exist for 2023, we explicitly define their analytical roles:

### Final HHVI surface used for manuscript figures

**HHVI_2023_main_30m_Guangzhou.tif**  
→ Used to generate **Figure 2a** (2023 HHVI spatial distribution) and all cartographic representations of baseline structural vulnerability.

### Intermediate HHVI surface used exclusively for temporal diagnostics and ΔHHVI construction

**Guangzhou_HHVI_2023_30m.tif**  
→ Used only for temporal diagnostics and ΔHHVI computation (**HHVI_2023 − HHVI_2019**) in **Methods 2.2.4** and **Results 3.1.3**.  
This surface is not used for any standalone spatial interpretation or cartographic output.

Both files are retained for transparency and full reproducibility of the analytical workflow.

---

## What is included (and what is not)

### Included

**Quantitative materials (Appendix Tables S0–S6)**  
Reproducibility index, parameter tables, diagnostics, robustness tests, temporal diagnostics, TPV overlap summaries, and final exported outputs used in the manuscript.

**Qualitative materials (Appendix Q; Appendix Tables S7–S12)**  
TPV coding scheme, qualitative reproducibility documentation, and illustrative coded excerpts provided for transparency and auditability.  
These materials support qualitative methods and results but do not constitute a separate qualitative dataset.

**Supplementary Material (File S9) (sensitivity and diagnostic details)**  
`Supplementary_Material_(File_S9).pdf` provides extended sensitivity and diagnostic results for governance discourse clustering referenced in the manuscript but not reproduced in the main text or appendices.

### Numerical outputs statement

Reported numerical values are taken directly from archived outputs deposited in this repository, with no post-export rescaling. Figures are provided for visual inspection only.

### Not included

- Raw third-party source rasters (e.g. Landsat, WorldPop, WSF), which are accessed via Google Earth Engine and fully documented in Appendix tables.  
- NVivo project files or software screenshots.  
- Any analyses beyond those reported in the manuscript and appendices.

---

## Technical environment (quantitative)

- **Platform:** Google Earth Engine (GEE)  
- **Spatial resolution:** 30 m  
- **Coordinate reference system:** EPSG:32649  
- **Study extent:** Guangzhou administrative boundary  

All GeoTIFF outputs are provided in **EPSG:32649 at 30 m resolution** and represent final analytical layers used for reporting, unless explicitly stated as intermediate diagnostic products.

---

## Key modelling rule

HHVI is constructed using coverage-adjusted aggregation.

- The main HHVI surface (2023) applies an adaptive denominator with **coverage ≥ 0.60**.  
- Temporal diagnostics (2019–2023) are computed on a **locked effective domain** defined by coverage ≥ 0.60.  
- For ΔHHVI (**HHVI_2023 − HHVI_2019**), statistics are derived on the **common support domain** where both years satisfy this threshold, ensuring spatial comparability of temporal differences (see Appendix Table S5).

All core diagnostics are conducted on **unsmoothed HHVI surfaces**; spatial smoothing is applied exclusively for visualisation or explicitly defined robustness tests.

---

## Summary statistics note

Summary statistics were computed on the final exported HHVI rasters only.  
For temporal change (ΔHHVI), statistics are calculated on the common support domain where both years satisfy coverage ≥ 0.60, consistent with **Appendix Table S5** and **Figure S6**.  
The use of `bestEffort` in `reduceRegion` was enabled for computational stability during large-area reductions and does not affect HHVI values or reported results (see Appendix Table S5).

---

## Mapping between manuscript and repository materials (document anchors)

### Script → Output → Manuscript mapping

The table below provides a one-to-one mapping between executable scripts, archived outputs, and their exact anchors in the manuscript.

| Script | Key output | Manuscript section |
|--------|------------|--------------------|
| `HHVI_2023_Main.js` | `HHVI_2023_main_30m_Guangzhou.tif` (Figure 2a) | Methods 2.2.2; Results 3.1.1 |
| `HHVI_TemporalChange.js` | `Guangzhou_dHHVI_2019_2023_30m.tif` (Figure 3) | Methods 2.2.4; Results 3.1.3 |
| `HHVI_SummaryStats_2019_2023.js` | `HHVI_SummaryStats_2019_2023.csv` | Appendix Table S5 |
| `HHVI2023_TPVOverlap_CAV2.js` | `Guangzhou_TPVOverlap_2023_stack.tif` | Methods 2.5; Results 3.3; Appendix (Table S6) |
| `HHVI2023_TPVOverlap_CAV2.js` | `Guangzhou_TPVOverlap_2023_Summary.csv` | Appendix (Table S6) |
| `HHVI2023_TPVOverlap_CAV2-robustness.js` | `TPVOverlap_Robustness.csv` | Appendix (Table S6, Block B) |

> **Note**  
> ΔHHVI statistics reported in the manuscript are derived on the common support domain (coverage ≥ 0.60 in both years), as documented in Appendix Table S5.

---

## Methods 2.2 (Quantitative: HHVI modelling)

→ `3_Documentation/2-Quantitative_Appendix.pdf`

- Tables **S1–S2**: inputs, preprocessing, indicator definitions, weights  
- Table **S3**, Figures **S3–S5**: diagnostics and robustness  
- Tables **S4a–S4c**: LCZ-based plausibility check (ANOVA/Tukey)  
- Tables **S5a**, Figure **S6**: temporal diagnostics  

---

## Methods 2.3 (Qualitative: TPV emotional–discursive analysis)

- **Coding scheme:**  
  `4_Qualitative_materials/TPV Coding Scheme for Qualitative Analysis.pdf`

- **Illustrative excerpts:**  
  `4_Qualitative_materials/Example_Coded_Excerpts (TPV Qualitative Analysis).pdf`

- **Reproducibility documentation:**  
  `3_Documentation/3-Qualitative_Appendix.pdf`

---

## Methods 2.4 + Results 3.3 (Embedded case: Shipaicun)

The embedded case is an **analytically embedded anchoring case used for cross-scalar anchoring** and does not constitute a separate deposited corpus.

Repository support is provided through shared outputs only:

- HHVI baseline surface: `2_Data/HHVI_2023_main_30m_Guangzhou.tif`  
- TPV overlap: Appendix **Table S6** in `3_Documentation/2-Quantitative_Appendix.pdf`  
- Case boundary & boundary specifications: Appendix **Table S12** and **Table Q7** in `3_Documentation/3-Qualitative_Appendix.pdf`

---

## License

This repository is released under the license stated in `LICENSE.txt` (**CC BY 4.0**).

---

## Contact

For questions regarding the repository materials:

- **Xiaoyi Su (corresponding author):** suxiaoyigz@gmail.com  
- **Yong Sun:** sunyong88.gz@gmail.com

---
