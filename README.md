# SN_H0pe_extended_modeling

Catalogs of cluster members and multiple-image families used to build the strong lensing models of the galaxy cluster G165 (SGAS J105039.6+001730) hosting the gravitationally lensed supernova H0pe.

These data products are published in:

> Galan et al. (2025), *Extended strong lensing model of G165 with SN H0pe*, [arXiv:2510.20561](https://arxiv.org/abs/2510.20561)

## Cluster overview

| Property | Value |
|----------|-------|
| Cluster name | G165 (SGAS J105039.6+001730) |
| Cluster redshift | z = 0.351 |
| Cluster center (J2000) | RA = 162.665°, Dec = +0.292° |
| SN H0pe host galaxy | z = 1.783 |

## Contents

### `catalogs/cluster_members_G165.txt`

Catalog of cluster member galaxies used in the strong lensing model. Contains 130 members within ~3.5 arcmin of the cluster center, selected from HST/ACS (F814W) and HST/WFC3 (F160W) imaging.

**Columns:**

| Column | Description |
|--------|-------------|
| `ID` | Galaxy identifier |
| `RA` | Right ascension [degrees, J2000] |
| `Dec` | Declination [degrees, J2000] |
| `z_spec` | Spectroscopic redshift (−1 if not available) |
| `z_phot` | Photometric redshift (−1 if not available) |
| `F814W` | HST/ACS F814W AB magnitude |
| `F160W` | HST/WFC3 F160W AB magnitude |
| `Type` | Redshift type: `BCG`, `spec`, or `phot` |

### `catalogs/multiple_images_G165.txt`

Catalog of multiply-imaged background sources (multiple-image families) used as constraints in the strong lensing model. Contains 45 images in 15 families, identified from JWST and HST imaging.

**Columns:**

| Column | Description |
|--------|-------------|
| `Family` | Image family (system) number |
| `Image` | Image label (Family.N) |
| `RA` | Right ascension of the lensed image [degrees, J2000] |
| `Dec` | Declination of the lensed image [degrees, J2000] |
| `z_spec` | Spectroscopic redshift of the source (−1 if not available) |
| `z_phot` | Photometric redshift of the source (−1 if not available) |
| `Type` | Redshift type: `spectroscopic` or `photometric` |
| `Notes` | Additional notes |

**Family 1** corresponds to the SN H0pe host galaxy system (the "Quyllur" arc) at z = 1.783. The supernova itself was discovered in three of the four images of this arc (see [arXiv:2310.03075](https://arxiv.org/abs/2310.03075) and [arXiv:2309.07491](https://arxiv.org/abs/2309.07491)).

## Usage

The catalog files are plain ASCII text files with `#`-prefixed comment lines. They can be read with standard tools:

```python
import numpy as np

# Read cluster members
members = np.genfromtxt("catalogs/cluster_members_G165.txt",
                        names=True, comments="#", dtype=None, encoding="utf-8")

# Read multiple images
images = np.genfromtxt("catalogs/multiple_images_G165.txt",
                       names=True, comments="#", dtype=None, encoding="utf-8")
```

or with [astropy](https://www.astropy.org/):

```python
from astropy.io import ascii

members = ascii.read("catalogs/cluster_members_G165.txt", comment="#")
images  = ascii.read("catalogs/multiple_images_G165.txt",  comment="#")
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
