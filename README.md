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

## Contents

### `catalogs/cluster_members_G165.txt`

Catalog of cluster member galaxies used in the strong lensing model.

### `catalogs/multiple_images_G165.txt`

Catalog of multiply-imaged background sources (multiple-image families) used as constraints in the strong lensing model.

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
