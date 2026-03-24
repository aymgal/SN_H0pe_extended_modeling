# SN_H0pe_extended_modeling

Catalogs of cluster members and multiple-image families used to build the strong lensing models of the galaxy cluster PLCK G165.7+67.0 (G165) hosting the gravitationally lensed supernova H0pe.

These data products are published in:

> Galan et al. (2025), *Strong lensing model and dust extinction maps of the host galaxy of type Ia supernova H0pe*, [arXiv:2510.20561](https://arxiv.org/abs/2510.20561)

## Cluster overview

| Property | Value |
|----------|-------|
| Cluster name | PLCK G165.7+67.0 (G165) |
| Cluster redshift | z = 0.348 |
| Approx. coordinates (J2000) | 11:27:15.164 +42:28:29.17 |
| SN H0pe host galaxy | z = 1.78 |

## Model variants

Two lens model variants are provided, distinguished by their lensing constraints:

- **`_plt` (point-like)**: Models built using only point-like lensing constraints across the full field of view.
- **`_ext` (extended)**: Models built using the full surface-brightness extent of Arc 2 (the arc containing SN H0pe), in addition to point-like constraints elsewhere over the field of view.

## Contents

All catalogs are plain ASCII text files with `#`-prefixed header lines describing column names and units. They are generated directly from the [GLEE](https://www.astro.ucla.edu/~kcs/glee/) lens modeling configuration files.

### Deflector catalogs (`glee_model_g165_lenses_*.txt`)

Catalogs of all deflectors (mainly cluster member galaxies) included in the lens models. Each row corresponds to one deflector component. Columns:

| Column | Unit | Description |
|--------|------|-------------|
| `RA_IMG` | deg | Right ascension of the deflector (image plane) |
| `DEC_IMG` | deg | Declination of the deflector (image plane) |
| `RA_SRC` | deg | Right ascension in source plane (`nan` for deflectors) |
| `DEC_SRC` | deg | Declination in source plane (`nan` for deflectors) |
| `REDSHIFT` | — | Redshift of the deflector |
| `REDSHIFT_PRIOR` | — | Prior type applied to the redshift |
| `TYPE` | — | Component type (e.g. `lens`) |
| `PROFILE` | — | Mass profile (e.g. `dpie` for dual pseudo-isothermal ellipsoid, `shear` for external shear) |
| `LABEL` | — | Optional label |

- `glee_model_g165_lenses_plt.txt` — 169 deflector components (point-like model)
- `glee_model_g165_lenses_ext.txt` — 169 deflector components (extended model)

### Source catalogs (`glee_model_g165_sources_*.txt`)

Catalogs of all lensing constraints, i.e. the families of multiply-imaged background sources used to optimize the lens models. Each row corresponds to one image of a background source. Columns:

| Column | Unit | Description |
|--------|------|-------------|
| `RA_IMG` | deg | Right ascension of the image (image plane) |
| `DEC_IMG` | deg | Declination of the image (image plane) |
| `RA_SRC` | deg | Right ascension of the reconstructed source (source plane) |
| `DEC_SRC` | deg | Declination of the reconstructed source (source plane) |
| `REDSHIFT` | — | Redshift of the background source |
| `REDSHIFT_PRIOR` | — | Prior type applied to the redshift (`exact`, `flat`, `link_*`) |
| `TYPE` | — | Constraint type (e.g. `ptl_src` for point-like source) |
| `PROFILE` | — | Source profile |
| `LABEL` | — | Optional label (e.g. family identifier) |

- `glee_model_g165_sources_plt.txt` — 106 image positions from 41 individual point-like sources (point-like constraints only)
- `glee_model_g165_sources_ext.txt` — 84 image positions from 33 individual point-like sources (extended model; Arc 2 surface-brightness extent constraints are encoded separately in the GLEE configuration)

## Usage

The catalog files can be read with `numpy`:

```python
import numpy as np

# Point-like model
lenses_plt  = np.loadtxt("catalogs/glee_model_g165_lenses_plt.txt",  comments="#", dtype=str)
sources_plt = np.loadtxt("catalogs/glee_model_g165_sources_plt.txt", comments="#", dtype=str)

# Extended model
lenses_ext  = np.loadtxt("catalogs/glee_model_g165_lenses_ext.txt",  comments="#", dtype=str)
sources_ext = np.loadtxt("catalogs/glee_model_g165_sources_ext.txt", comments="#", dtype=str)
```

## Citation

If you use these catalogs in your work, please cite:

```
@article{Galan2025,
  author  = {Galan, Aymeric and others},
  title   = {Extended strong lensing model of G165 with SN H0pe},
  journal = {arXiv e-prints},
  year    = {2025},
  eprint  = {2510.20561},
  archivePrefix = {arXiv}
}
```

## License

The data products in this repository are made available under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license.
