# Dry years had more synchronous flowering and less stable populations of generalist pollinators in a bee diversity hotspot of the southwest USA

Data and analysis code for the manuscript submitted to *Ecology* (Report).

**Authors:** M. Dylan Taylor, Manogya Chandar, Jade McLellan, Emerson Martin, Melanie R. Kazenel, Karen Wright, Terry Griswold, Kenneth D. Whitney, and Jennifer A. Rudgers

**Corresponding author:** M. Dylan Taylor (mattdtaylor12@gmail.com)

---

## Overview

This repository contains the R Markdown analysis and the processed data needed to reproduce the results, figures, and supplementary analyses for the manuscript. Using two decades of co-located flowering-phenology and bee-abundance data from three semiarid ecosystems at the Sevilleta LTER (central New Mexico, USA), we ask:

1. Which climate variables best predict co-flowering synchrony, and are the predictors consistent among ecosystems?
2. Does the temporal stability of specialist vs. generalist bee abundance track co-flowering synchrony?
3. Has co-flowering synchrony changed over time, and are trends consistent among ecosystems?

## Repository structure

```
sevilleta-coflowering-synchrony/
├── README.md
├── LICENSE                # MIT (code); data licensed CC-BY 4.0 (see below)
├── CITATION.cff
├── .gitignore
├── code/
│   └── synchrony_july2026.Rmd    # full analysis: synchrony metric, climate models, bee stability, figures
└── data/
    ├── processed/         # derived data read by the analysis (included here)
    └── raw/               # raw SEV-LTER inputs — download from EDI (see data/raw/README.md)
```

## Data provenance

**Processed data (included in `data/processed/`)**

| File | Description |
|---|---|
| `plant_plant_overlapthru2024.csv` | Pairwise co-flowering overlap (coefficient of overlapping, Δ) among animal-pollinated plant species, by transect and year |
| `plant_overlap_climate_filtered.csv` | Transect-level mean co-flowering synchrony merged with climate predictors |
| `animal_poll_floral_async.csv` | Animal-pollinated floral asynchrony summary used in the stability analysis |
| `bee_tally.csv` | Bee species tallies by transect, month, and year |
| `lhtraits_2023-08-29_forpub.csv` | Bee life-history traits (floral specialization / diet breadth) |
| `climatebyyear_updated.csv` | Seasonal precipitation and growing-degree-days by station and year |
| `precipitation_CV.csv` | Coefficient of variation of daily precipitation by station and year |
| `pdo.timeseries.ersstv5.csv` | Annual Pacific Decadal Oscillation index (derived from NOAA/NCEI ERSSTv5) |

**Raw data (NOT re-archived here — cite and download from EDI)**

The raw Sevilleta LTER bee, plant-phenology, and meteorological data are permanently archived in the Environmental Data Initiative (EDI) repository and should be cited as data packages, not re-hosted. To reproduce the upstream synchrony calculation, download these into `data/raw/` (see `data/raw/README.md`):

- Bee abundance data — `SEVBeeData2002-2019_revised2023-07-19.csv` (EDI; *Wright et al.*, add DOI)
- Plant phenology data — `sev137_plant_phenology.2023.csv` (EDI; *McLellan et al.*, add DOI)
- Meteorological data — SEV-LTER met stations (EDI; *Moore & Winter*, add DOI)

> The chunks that compute the pairwise synchrony metric from raw phenology are set `eval = FALSE`; the downstream models and figures run from the processed files above.

## Reproducing the analysis

Requires **R** (≥ 4.3) and the packages below. Open `code/synchrony_july2026.Rmd` in RStudio and knit, or run `rmarkdown::render("code/synchrony_july2026.Rmd")` with the working directory set so the `data/processed/` files are on the read paths.

**Packages:** Directional, MuMIn, broom, car, codyn, cowplot, data.table, dplyr, emmeans, furrr, future, ggplot2, ggpubr, ggthemes, lmerTest, nlme, piecewiseSEM, plm, purrr, readr, reshape2, scales, sfsmisc, tidyr, vegan, visreg.

Key versions used: R Core Team (2026); nlme 3.1-162 (Pinheiro et al. 2023); MuMIn 1.48.4 (Bartoń 2024); emmeans 1.10.5 (Lenth 2024); Directional 7.3 (Tsagris et al. 2026).

## Archiving / DOI

This repository is mirrored to Zenodo for a citable DOI. On release, cite the Zenodo record (DOI to be added here).

## License

Code is released under the MIT License (see `LICENSE`). Data files in `data/processed/` are released under CC-BY 4.0. Raw SEV-LTER data retain their EDI licensing and should be cited from EDI.

## Citation

If you use these materials, please cite the manuscript (in review) and this archive. See `CITATION.cff`.
