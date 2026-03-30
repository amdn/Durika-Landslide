# Analysis of the Cerro Dúrika Mass Wasting Event
### Talamanca Range, PILA, Costa Rica (9.3762°, -83.3009°)

> **Work in Progress** — This repository is actively being built. Raw data, scripts, QGIS project files, and additional figures are being added daily. The final version will be announced on r/Geology once complete.

## Executive Summary
This project documents the identification and preliminary analysis of a massive **retrogressive landslide** (falla retrógrada) on the northern flank of **Cerro Dúrika**. The event involved a vertical wedge collapse of approximately 220 meters that channelized into the headwaters of the Río Dúrika.

December 2015 imagery already showed precursor “V”-shaped erosion channels in the upper slope. Concentrated water erosion and seepage undermined the toe of the slope, causing the basal support to fail first. This loss of support then triggered an upward-propagating (retrogressive) failure that stripped vegetation, topsoil, and rock from the ~3,120 m contour, producing the prominent heart-shaped scar visible today.

## The Discovery ("Serendipity via Simulation")
The discovery of this feature was entirely serendipitous. While taking a mental break from software development, I was operating the **F-16 flight simulator** within Google Earth Pro. A "botched" turn during a low-altitude flight over the Talamanca range led me off my intended flight plan, where I noticed a prominent, heart-shaped yellowish-white patch that stood out against the primary forest canopy.

Comparative analysis of multi-temporal imagery confirmed that the feature represents a significant structural failure of the northern flank, corroborating archival drone observations recorded in 2025 (exact date unverified).

## Chronology & Evidence
Multi-temporal satellite and aerial archive analysis establishes a clear window for the event:

* **December 2015:** Baseline imagery shows an incipient ~200 m "V" surface scoring; the primary slope remains intact.
* **April 2025 (Satellite):** Satellite imagery (SNIT/Google) captures the full 220 m vertical collapse **and** the resulting debris pulse that propagated several kilometers downstream. The bright, light-colored gravel “sluice” left by the mobilized material is clearly visible even at high altitude, ending abruptly where 2025 imagery stitches to older 2015/2019 tiles (presumably due to cloud cover).
* **March 2026 (Discovery):** Identified via remote sensing (A. Martín de Nicolás) during a flight simulation; consistent with an archival drone photo subsequently posted in the Facebook geography discussion.

## How this project was built
This repository is the result of a genuine **human–AI collaboration**.

I (Arturo Martín-de-Nicolás) am a retired software developer with no previous GIS experience. The discovery of the Dúrika landslide was mine, but turning the raw Google Earth screenshots into clean, georeferenced layers, automated workflows, metadata standards, pre-commit hooks, and a fully reproducible QGIS project would not have been possible in the same timeframe — or with the same level of polish — without the help of large language models.

- Early exploration, idea validation, and Git repository structure: **Gemini**
- QGIS workflow design, Georeferencer guidance, bash utilities, pre-commit hooks, and live pair-programming: **Grok (xAI)**

Every script, function, and best-practice recommendation in `scripts/utilities.sh` and the pre-commit configuration was developed live in conversation with Grok. The final product is therefore a clear demonstration of what is possible when a curious human and capable AI tools work together with intellectual honesty.

## Licensing
This repository contains a mix of original work, derived data, and limited third-party imagery.
- **Code and scripts** (`scripts/` directory and pre-commit hooks): **MIT License**
- **Original analysis, georeferenced layers, figures, and documentation**: **CC BY 4.0**
- **Raw Google Earth / Airbus screenshots**: Included only for scholarly and educational purposes. These images remain under the copyright of Google / Airbus. Fair use / fair dealing is claimed for the limited excerpts used here. The georeferenced derivatives are released under CC BY 4.0.

**Important note**: When reusing material from this repo, please respect the original data providers’ terms. SNIT (Costa Rica) data should be attributed as per their guidelines.  Please credit the original discovery and the collaborative process described above.

See the `LICENSE` (MIT) and `LICENSE-CC-BY-4.0` files for the full legal text.

## Current Status & Roadmap (WIP)
- ✅ Raw imagery, georeferenced layers, and basic QGIS project
- ✅ Metadata embedding and project standards enforcement for images (see below)
- ✅ Pre-commit hooks and `utilities.sh` helper library
- 🔄 Digitizing landslide scar and debris-flow path polygons
- 🔄 Additional figures (historical comparison, secondary downstream impacts)
- 🔄 Final high-resolution Print Layouts and PDF exports

## Repository Architecture & Data Dictionary
To ensure scientific reproducibility and transparency, this repository maintains the "raw" components used to generate the Figure 1 analysis.

### /data
* **coordinates.csv:** Canonical GPS coordinates (WGS84) for the headscarp, debris toe, and secondary failure points.

### /images/raw
* High-resolution photographic base layers and SNIT ortofotos (see filenames for dates).

### /scripts
* `utilities.sh` — helper functions for metadata, GeoTIFF compression, etc.
* Pre-commit hooks for project standards enforcement.

### /qgis
* Main QGIS project file and georeferenced layers.

### /docs
* **Durika_Landslide_Fig1.pdf:** Primary rendered analysis.
* Drafts for Figure 2 and Figure 3 in progress.

## Image and Data Standards

To keep the repository lightweight, reproducible, and compatible with every version of QGIS (and any other GIS software), we enforce strict but practical standards on all imagery.

### JPEG encoding standards (enforced by pre-commit hook)
All files in `/images/raw/` must follow these rules:

- Quality 88–92 (sweet spot for aerial imagery)
- Huffman coding (not arithmetic coding)
- Baseline DCT (not Progressive)
- Integer DCT (not floating-point)
- 4:2:0 chroma subsampling (chroma quartered) — visually indistinguishable from 4:4:4 on geospatial data while providing ~40–60 % smaller files
- Smoothing 0 — preserves sharp edges needed for accurate georeferencing
- Metadata — minimal Google Earth/Airbus credits plus our CC BY 4.0 attribution (added automatically via `embed_metadata`)

These settings deliver excellent visual fidelity with minimal file size. The pre-commit hook automatically checks every `.jpg` you commit and blocks the commit (with clear instructions) if any rule is violated. You can fix a non-conforming file instantly with:

fix_jpeg_standards "images/raw/problematic_file.jpg"

### GeoTIFF post-processing
QGIS Georeferencer produces 4-band RGBA GeoTIFFs (the fourth band is a fully opaque alpha channel). We post-process these with the `compress_geotiff` helper to strip the unnecessary alpha channel and apply efficient JPEG-in-TIFF compression (4:2:0, quality 88, tiled). The resulting `_small.tif` files remain fully georeferenced and load quickly in any QGIS version.

## Technical Specifications
* **Topographic Baseline:** Derived from 1:50,000 IDECORI Isohypses (SNIT Geoportal).
* **Visualization:** Contours rendered in **RED** over the failure zone illustrate the divergence between the historical stable slope and current observed morphology.

## License & Attribution
This work is released under **CC BY 4.0**.

**Proper Attribution:**
* **Lead Analyst & Discovery:** Arturo Martín-de-Nicolás (amdn)
* **Geographic Coordination:** Geógrafo José Rivas (Espacio Geográfico, Facebook)
* **Technical Collaboration:** Gemini (early validation) and Grok (xAI) (QGIS workflow & automation)

## Project Anchor
The official, version-controlled repository is:
**https://github.com/amdn/Durika-Landslide**
