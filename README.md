# fdr-spatial-correction

**Code for "The Stippled Gridpoints are Statistically Significant: (Mis)uses of False Discovery Rate Correction for Geospatial Data"**

This repository contains the analysis code accompanying the preprint (Schutte et al., 2026, EGUsphere), which examines a specific and counterintuitive failure mode of false discovery rate (FDR) correction when applied to spatially coherent geoscientific data.

The underlying data are hosted on Zenodo (see below).

---

## Why this matters

Peer-reviewed geoscience papers routinely test statistical significance independently at every grid point in a spatial field, but formal correction for multiple testing is applied inconsistently — and even when it is applied, common approaches don't always transfer cleanly to geoscientific data, which is often spatially coherent rather than made up of independent tests.

This work shows two things. First, skipping multiple-testing correction altogether can substantially inflate the number of false positives, as expected. Second, and more surprising: the global false discovery rate (FDR) approach — a method that has itself been recommended in the geoscience literature — can behave counterintuitively when the underlying signal is spatially coherent. Using near-surface air temperature composites following sudden stratospheric warmings as a worked example, the paper shows that **restricting the spatial domain analysed can *increase* the FDR-adjusted significance threshold** — meaning the exact same underlying field can appear more statistically significant purely because of how the domain was chosen, with nothing about the data itself having changed. This traces back to the rank-based structure of the FDR procedure itself.

The practical upshot: multiple-testing correction matters, but applying FDR correction naively can be actively misleading rather than just conservative. The paper closes with concrete recommendations — documenting corrections transparently, interpreting adjusted thresholds cautiously, and considering regional or cluster-based inference as spatially aware alternatives.

---

## What's in this repository

- **`figures.ipynb`** — reproduces all figures in the paper and appendix, including composite anomaly maps and visualisations of FDR correction applied across different spatial domains

---

## Data

The data used by the notebook are hosted on the Zenodo deposit rather than in this repository (total ~7.9 GB, so not practical to keep in git):

- ERA5 2m temperature data (1979–2022, October–April), detrended and deseasonalised, used to compute composite temperature anomalies following sudden stratospheric warming (SSW) events
- A land-sea mask
- Pre-computed bootstrap samples for significance testing, at two spatial resolutions

Download from Zenodo and point the notebook at the local files to reproduce the figures.

---

## Citation

Preprint:

> Schutte, M. K., Olivetti, L., Pons, F. M. E., and Messori, G.: The Stippled Gridpoints are Statistically Significant: (Mis)uses of False Discovery Rate Correction for Geospatial Data, EGUsphere [preprint], https://doi.org/10.5194/egusphere-2026-2203, 2026.

Code and data:

> Schutte, M., Olivetti, L., Pons, F. M. E., & Messori, G. (2026). *Code and data for "The Stippled Gridpoints are Statistically Significant: (Mis)uses of False Discovery Rate Correction for Geospatial Data"* [Data set]. Zenodo. https://doi.org/10.5281/zenodo.20280931

Zenodo deposit: **https://zenodo.org/records/20280931**

Licensed under CC BY 4.0.

---

## Requirements

```bash
pip install -r requirements.txt
```

Core dependencies: `numpy`, `scipy`, `xarray`, `matplotlib` `proplot`

---

## Author

**Michael Konrad Schutte**
PhD Researcher, Department of Earth Sciences, Uppsala University
Stratosphere–troposphere coupling and compound climate extremes

Co-authors: Leonardo Olivetti, Flavio Maria Emanuele Pons, Gabriele Messori

---

## License

CC BY 4.0 — see the Zenodo record for full license details.
