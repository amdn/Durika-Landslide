# Analysis of the Cerro Dúrika Mass Wasting Event
### Talamanca Range, PILA, Costa Rica (9.3762°, -83.3009°)

## Executive Summary
This project documents the identification and preliminary analysis of a massive structural slope failure on the northern flank of **Cerro Dúrika**. The event involves a vertical wedge collapse of approximately 220 meters, initiating at the ~3,120m contour and channelizing into the headwaters of the Río Dúrika. 

## The Discovery ("Serendipity via Simulation")
The discovery of this feature was entirely serendipitous. While taking a mental break from software development, I was operating the **F-16 flight simulator** within Google Earth Pro. A "botched" turn during a low-altitude flight over the Talamanca range led me off my intended flight plan, where I noticed a prominent, heart-shaped yellowish-white patch that stood out against the primary forest canopy. 

Subsequent investigation using historical imagery confirmed that this was not a known geographic feature, but a recent and significant mass wasting event.

## Chronology & Evidence
A comparative analysis of multi-temporal satellite and aerial archives establishes a clear window for the event:
* **December 2015:** Baseline imagery shows incipient ~200m "V" surface scoring; primary slope remains intact.
* **April 2025:** Satellite imagery captures the full 220m vertical collapse.
* **March 2026:** Remote sensing discovery (A. Martín de Nicolás); subsequent drone validation (J. Salas) confirms "ground truth."

## Repository Architecture & Data Dictionary
To ensure scientific reproducibility and transparency, this repository maintains the "raw" components used to generate the Figure 1 analysis.

### /data
* **coordinates.csv:** Canonical GPS coordinates (WGS84) for the headscarp, debris toe, and secondary failure points.

### /images/raw
* **Durika_Landslide_Raw_Aerial_Apr-2025.jpg:** High-resolution photographic base layer. JPG format was selected to optimize storage while maintaining visual fidelity of the primary forest canopy.
* **Durika_Landslide_Raw_Elevation_SNIT.png:** 10m contour interval overlay (Source: SNIT). PNG format is utilized here to preserve the alpha channel (transparency) required for precise topographic alignment.

### /docs
* **Durika_Landslide_Fig1.pdf:** The primary rendered analysis. This "binary" asset is composed by layering the elevation PNG over the aerial JPG, gravity-aligned (180° rotation) for an intuitive slope-down view.
* **figure1_sidebar.md:** Raw text of the technical specifications and observations featured in the Figure 1 sidebar.

## Technical Specifications
* **Topographic Baseline:** Derived from 1:50,000 IDECORI Isohypses (SNIT Geoportal).
* **Visualization:** Contours rendered in **RED** over the failure zone illustrate the divergence between the historical stable slope and current observed morphology.

## Future Research
We are currently seeking to collaborate with the geological community for:
1.  **Volumetric quantification** utilizing Structure from Motion (SfM) from recent 4K drone assets.
2.  **Geomorphological mapping** of the debris flow path and downstream impacts.
3.  **Interactive 3D Visualization:** Development of an SPA (Single Page Application) for public data exploration.

## License & Attribution
This work is released under **CC BY 4.0**. 

**Proper Attribution:**
* **Lead Analyst:** Arturo Martin de Nicolás (amdn)
* **Coordination:** Geógrafo José Rivas (Espacio Geográfico)
* **Validation:** Johel Salas (Drone Reconnaissance)
* **Technical Assistant:** Gemini (AI Model)
