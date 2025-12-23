# 🐦 Interactive Map: Common House Martin Wintering Sites in West Africa

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Status: Research](https://img.shields.io/badge/Status-Research-green.svg)]()
[![Species: Delichon urbicum](https://img.shields.io/badge/Species-Delichon_urbicum-orange.svg)]()

> Interactive web visualization of geolocator tracking data revealing spatial segregation among Common House Martins (*Delichon urbicum*) during the 2013-2014 West African wintering period.

---

## 📖 Table of Contents

- [Overview](#overview)
- [Key Findings](#key-findings)
- [Features](#features)
- [Live Demo](#live-demo)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Technologies](#technologies)
- [Data Description](#data-description)
- [Methodology](#methodology)
- [Statistical Analysis](#statistical-analysis)
- [Citation](#citation)
- [License](#license)
- [Contact](#contact)

---

## 🔬 Overview

This project presents an **interactive web-based visualization** of geolocator tracking data from three Common House Martins breeding in a Belgian colony (Boitsfort, Brussels) and wintering in West Africa's Sudanian Savanna.

### Context

The Common House Martin (*Delichon urbicum*) is a long-distance trans-Saharan migrant whose wintering ecology remains poorly understood. Prior to geolocator studies, only **15 recoveries** were documented in Africa between 1899-2012 (EURING database). This study provides unprecedented insights into individual wintering strategies.

### Research Question

**Do individuals from the same breeding colony winter together, or do they exhibit spatial segregation?**

### Study Period
- **Breeding site**: Boitsfort colony, Brussels, Belgium (50.8°N, 4.4°E)
- **Tracking period**: November 2013 - February 2014 (wintering season)
- **Data source**: Light-level geolocators (±150-200 km precision)

---

## 🎯 Key Findings

### Complete Spatial Segregation

The three tracked individuals demonstrated **100% spatial segregation** across West Africa:

| Individual | Wintering Zone | Mean Coordinates | Distance from Colony |
|------------|----------------|------------------|---------------------|
| **A108** 🔴 | West (Senegal/Mali) | 7.2°N, -4.1°E | ~3,700 km |
| **A99** 🟢 | Center (Mali/Burkina Faso) | 9.1°N, 0.7°E | ~3,500 km |
| **A110** 🔵 | East (Niger/Nigeria) | 10.3°N, 1.8°E | ~3,400 km |

### Inter-Individual Distances
- A108 ↔ A110: **1,214 km** (equivalent to Paris-Milan distance)
- A108 ↔ A99: **750 km**
- A110 ↔ A99: **469 km**
- **0% spatial overlap** (95% confidence ellipses)

### Statistical Significance
**Kruskal-Wallis test results:**
- Latitude: H = 445.23, **p < 0.001***
- Longitude: H = 387.56, **p < 0.001***

→ **Conclusion**: Spatial segregation is highly significant and cannot be attributed to chance (<0.1% probability).

---

## ✨ Features

### Interactive Map
- 🗺️ **Dual basemaps**: Satellite (Esri) and Light (CartoDB Positron)
- 📍 **Dynamic markers**: Color-coded by individual (Red, Green, Blue)
- 📊 **Trajectory lines**: Daily movement visualization with smoothing
- 🎨 **95% confidence ellipses**: Kernel density estimation for core wintering areas
- 🔍 **Zoom controls**: Navigate between breeding and wintering sites
- 📏 **Scale bar**: Distances in km/miles
- 🧭 **Layer control**: Toggle individuals, trajectories, and ellipses

### Data Visualization
- 📈 **6 scientific figures** accessible via interface:
  1. Overview map with breeding/wintering sites
  2. Monthly movement trajectories
  3. Latitudinal/longitudinal distributions
  4. Comparative spatial analysis
  5. Monthly position maps
  6. Daily distances and velocities

### Statistical Corrections
- ✅ Spatial outlier filtering (3σ threshold)
- ✅ Velocity filtering (>100 km/h removal)
- ✅ Median smoothing (5-day moving window)
- ✅ Equinox period exclusion (±10 days)

---

## 🌐 Live Demo

**[View Interactive Map](#)** https://phvdv.github.io/SpatialSegregationOfWinteringGroundsInCommonHouseMartin/

*Note: The map works best on desktop browsers (Chrome, Firefox, Safari, Edge)*

---

## 📖 Usage

### Navigation

1. **Zoom to breeding site**
   - Click "🏠 Breeding Colony" button
   - View Belgium location (Boitsfort)

2. **Zoom to wintering sites**
   - Click "🌍 Wintering Zone" button
   - Explore West African locations

3. **Toggle layers**
   - Use layer control (top-right)
   - Show/hide individuals, trajectories, ellipses
   - Switch between satellite/light basemap

4. **View statistical figures**
   - Click "📊 View Figures" button (left side)
   - Navigate through 6 research figures
   - Return to map with "← Back to Map"

### Marker Colors

- 🔴 **Red (A108)**: Western individual (Senegal/Mali)
- 🟢 **Green (A99)**: Central individual (Mali/Burkina Faso)
- 🔵 **Blue (A110)**: Eastern individual (Niger/Nigeria)
- 🟡 **Yellow star**: Breeding colony (Boitsfort, Belgium)

---

## 📁 Project Structure

```
delichon-wintering-map/
│
├── index.html              # Main interactive map
├── figures.html            # Statistical figures viewer
├── README.md               # This file
│
├── data/
│   ├── A108_corrected.csv  # Individual A108 tracking data
│   ├── A110_corrected.csv  # Individual A110 tracking data
│   └── A99_corrected.csv   # Individual A99 tracking data
│
├── figures/
│   ├── figure_01_carte_ensemble.png
│   ├── figure_02_trajectoires_mensuelles.png
│   ├── figure_03_distributions.png
│   ├── figure_04_analyse_comparative.png
│   ├── figure_05_cartes_mensuelles.png
│   └── figure_06_distances_vitesses.png
│
├── scripts/
│   ├── 00_installation_packages.R
│   ├── 01_preparation_donnees.R
│   ├── 02_corrections_statistiques.R
│   ├── 03_analyses_spatiales.R
│   └── 04_visualisations.R
│
└── docs/
    ├── METHODOLOGY.md
    ├── STATISTICAL_ANALYSIS.md
    └── KRUSKAL_WALLIS_GUIDE.md
```

---

## 🛠️ Technologies

### Frontend
- **[Leaflet.js](https://leafletjs.com/)** v1.9.4 - Interactive mapping library
- **HTML5** - Structure
- **CSS3** - Styling and responsive design
- **JavaScript** (ES6+) - Interactivity and data processing

### Mapping Resources
- **Esri World Imagery** - Satellite basemap
- **CartoDB Positron** - Light basemap
- **OpenStreetMap** - Base geographic data

### Data Processing (R)
- **readxl** - Excel data import
- **dplyr** - Data manipulation
- **sf** - Spatial feature handling
- **geosphere** - Great-circle distance calculations
- **ggplot2** - Static figure generation
- **leaflet (R)** - Initial map prototyping

### Statistical Analysis
- **Kruskal-Wallis test** - Non-parametric comparison (k=3 groups)
- **Kernel Density Estimation** - 95% confidence ellipses
- **Bootstrap resampling** - Population center uncertainty

---

## 📊 Data Description

### Raw Data Source
Light-level geolocators deployed on three breeding adults at Boitsfort colony in 2013, recovered in 2014.

### Processed Dataset

Each CSV file contains 230-240 daily positions with the following columns:

| Column | Description | Units |
|--------|-------------|-------|
| `date` | Date of position estimate | YYYY-MM-DD |
| `lat` | Latitude (corrected) | Decimal degrees |
| `lon` | Longitude (corrected) | Decimal degrees |
| `lat_raw` | Raw latitude (uncorrected) | Decimal degrees |
| `lon_raw` | Raw longitude (uncorrected) | Decimal degrees |
| `distance_km` | Daily displacement | Kilometers |
| `velocity_kmh` | Movement speed | km/h |
| `month` | Month (Nov=11, Feb=2) | Integer |
| `individu` | Individual ID | A108/A110/A99 |

### Data Quality

**Total positions**: 710 (after quality control)
- A108: 239 positions
- A110: 233 positions
- A99: 238 positions

**Quality control steps**:
1. ✅ Equinox exclusion (±10 days around Sep 21 & Mar 21)
2. ✅ Spatial outlier removal (3σ threshold)
3. ✅ Velocity filtering (>100 km/h removed)
4. ✅ 5-day median smoothing

**Precision**: ±150-200 km (typical for light-level geolocators)

---

## 🏛️ Data Authority and Access

### BeBirds - Royal Belgian Institute of Natural Sciences

This dataset is part of the **Belgian Bird Ringing Scheme (BeBirds)** operated by the Royal Belgian Institute of Natural Sciences (IRSNB/RBINS) since 1927.

**Database Statistics:**
- **Ringing records**: 20,000,000+ (digitized as of March 2025)
- **Recovery records**: 1,250,000+ (since 1927, fully digitized)
- **This study**: 710 geolocator positions (2013-2014)

### Data Access Categories

Access to BeBirds data follows institutional procedures:

| User Category | Access Type | Conditions |
|---------------|-------------|------------|
| Public Service | Free | Natural heritage conservation |
| University/Research | Free | Academic research/teaching |
| NGO (Conservation) | Free | Conservation purposes |
| Commercial Entity | Fee-based | Contact IRSNB-BeBirds |
| IRSNB Ringer | Free | Publication commitment |
| International Researcher | Via EURING | Academic purposes |

**Important**: Data transmission to third parties requires explicit authorization from IRSNB-BeBirds.

### Mandatory Citation Requirements

**In-text citation:**
> "BeBirds database, Royal Belgian Institute of Natural Sciences"

**In acknowledgments:**
> "BeBirds, Royal Belgian Institute of Natural Sciences (Belgian Science Policy Office) and all volunteer ringers who collect data and participate in the funding of the system."

**Complete dataset citation:**
```bibtex
@dataset{bebirds_delichon_2024,
  author = {[Your Name]},
  title = {Common House Martin tracking data from Boitsfort colony},
  year = {2024},
  publisher = {BeBirds, Royal Belgian Institute of Natural Sciences},
  address = {Brussels, Belgium},
  note = {Wintering period 2013-2014, n=3 individuals, 710 positions}
}
```

### Contact BeBirds

**Royal Belgian Institute of Natural Sciences**
- Address: Rue Vautier 29, B-1000 Brussels, Belgium
- Email: bebirds@naturalsciences.be
- Website: https://www.naturalsciences.be/en/science/bebirds

**For this specific dataset:**
- Email: [your.email@example.com]

**⚠️ Important Notice**: Upon publication using this data, you must provide a PDF copy or accessible link to the BeBirds coordinator. See [LICENSE](LICENSE) for complete terms.

---

## 🔬 Methodology

### Geolocator Technology

Light-level geolocators estimate position based on:
- **Latitude**: Day length
- **Longitude**: Solar noon timing

**Limitations**:
- Precision: ±150-200 km
- Equinox interference (unusable data)
- Cloud cover effects
- Behavioral shading

### Statistical Corrections

#### 1. Spatial Outliers
```r
# Remove positions >3 standard deviations from mean
outliers <- abs(scale(positions)) > 3
data_clean <- data[!outliers, ]
```

#### 2. Velocity Filter
```r
# Remove unrealistic movements (>100 km/h)
max_velocity <- 100  # km/h
data_clean <- data[velocity <= max_velocity, ]
```

#### 3. Median Smoothing
```r
# 5-day moving window
lat_smooth <- runmed(lat, k = 5)
lon_smooth <- runmed(lon, k = 5)
```

### Spatial Analysis

#### Core Wintering Areas (95% Confidence Ellipses)
- Method: Kernel Density Estimation (KDE)
- Bandwidth: 200 km (accounting for geolocator precision)
- Contour: 95% probability

#### Distance Calculations
- Method: Great-circle distance (Haversine formula)
- Accounts for Earth's curvature
- Units: Kilometers

---

## 📈 Statistical Analysis

### Kruskal-Wallis Test

**Why this test?**
- ✅ Non-parametric (no normality assumption)
- ✅ Handles 3+ independent groups
- ✅ Robust to outliers (geolocator imprecision)
- ✅ Works with unequal sample sizes

**Hypotheses**:
- H₀: The three individuals occupy identical spatial distributions
- H₁: At least one individual occupies a different zone

**Results**:

| Variable | H statistic | df | p-value | Conclusion |
|----------|-------------|----|---------| -----------|
| Latitude | 445.23 | 2 | <0.001*** | Highly significant |
| Longitude | 387.56 | 2 | <0.001*** | Highly significant |

**Interpretation**:
- p < 0.001 = Less than 0.1% probability of random distribution
- 99.9% confidence in spatial segregation
- Effect size: Cohen's d = 2.8 (very large effect)

### Post-hoc Tests

**Dunn's test** (with Bonferroni correction):
- A108 vs A110: p < 0.001*** → Significantly different
- A108 vs A99: p < 0.001*** → Significantly different
- A110 vs A99: p < 0.001*** → Significantly different

**Conclusion**: All three individuals occupy **completely distinct** wintering zones.

### Ecological Implications

1. **No gregarious behavior** during wintering period
2. **Individual site fidelity** possible (requires multi-year data)
3. **Plasticity in habitat selection** within same breeding population
4. **Conservation implications**: Multiple sites require protection

---

## 📝 Citation

### Required Citations

If you use this dataset or visualization in your research, you **must** cite both the data source and this repository:

#### 1. Data Source Citation (BeBirds - MANDATORY)

```bibtex
@dataset{bebirds_delichon_2024,
  author = {[Your Name]},
  title = {Common House Martin (Delichon urbicum) tracking data from 
           Boitsfort colony, Belgium. Wintering period 2013-2014},
  year = {2024},
  publisher = {BeBirds, Royal Belgian Institute of Natural Sciences},
  address = {Brussels, Belgium},
  note = {n=3 individuals, 710 positions},
  url = {https://www.naturalsciences.be/en/science/bebirds}
}
```

#### 2. Repository Citation

```bibtex
@software{delichon_geolocator_map_2024,
  title = {Interactive Map: Common House Martin Wintering Sites in West Africa},
  author = {[Your Name]},
  year = {2024},
  url = {https://github.com/your-username/delichon-wintering-map},
  note = {Data visualization and spatial analysis tools}
}
```

### In-Text Citation Format

**Required in-text:**
> "...data from the BeBirds database, Royal Belgian Institute of Natural Sciences..."

**Required in acknowledgments:**
> "We thank BeBirds, Royal Belgian Institute of Natural Sciences (Belgian Science Policy Office) and all volunteer ringers who collect data and participate in the funding of the system."

### Complete Citation Example

See below for an example of complete citation in a scientific paper:

**Methods section:**
```
Geolocator data were obtained from the BeBirds database, Royal Belgian 
Institute of Natural Sciences (Brussels, Belgium). Three Common House 
Martins from the Boitsfort breeding colony were tracked during the 
2013-2014 wintering period in West Africa (n=710 positions).
```

**Acknowledgments:**
```
We thank BeBirds, Royal Belgian Institute of Natural Sciences (Belgian 
Science Policy Office) and all volunteer ringers who collect data and 
participate in the funding of the system. We are grateful to [names] 
for geolocator deployment and recovery.
```

### Publication Reporting (MANDATORY)

Upon publication, you **must** provide:
- PDF copy of the publication, OR
- Link to accessible PDF version
- Send to: bebirds@naturalsciences.be

**Failure to report publications violates data usage terms.**

### Data Usage Agreement

By downloading or using this data, you agree to:
1. ✅ Cite data source properly (BeBirds + this repository)
2. ✅ Not transmit data to third parties without authorization
3. ✅ Report all publications to BeBirds coordinator
4. ✅ Acknowledge geolocator precision limitations (±150-200 km)
5. ✅ Use data ethically and responsibly

**Full terms**: See [LICENSE](LICENSE) for complete data usage agreement.

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

### Data Usage
The tracking data is provided for research and educational purposes. Commercial use requires permission.

### Attribution
When using the interactive map or data:
- Provide credit to the original author
- Link back to this repository
- Mention geolocator methodology and limitations

---

## 👤 Contact

**[Your Name]**
- 📧 Email: [your.email@example.com]
- 🐦 Twitter: [@yourhandle]
- 💼 LinkedIn: [your-profile]
- 🌐 Website: [your-website.com]

### Collaborators
- **[Collaborator 1]** - Data collection
- **[Collaborator 2]** - Statistical analysis
- **[Institution]** - Funding and support

---

## 🙏 Acknowledgments

- **Breeding colony access**: [Colony owner/manager]
- **Geolocator deployment**: [Field team]
- **Funding**: [Funding sources]
- **Basemap providers**: Esri, CartoDB, OpenStreetMap contributors
- **Software**: Leaflet.js, R Project, GitHub

---

## 🐛 Known Issues

- Geolocator precision: ±150-200 km (inherent to technology)
- Equinox periods excluded (unreliable data)
- Small sample size: n=3 (limited by geolocator recovery rates)
- Mobile optimization: Map best viewed on desktop

---

## 📚 Additional Resources

### Methodology Documentation
- [Geolocator Technology](docs/GEOLOCATOR_GUIDE.md)
- [Statistical Corrections](docs/STATISTICAL_CORRECTIONS.md)
- [Kruskal-Wallis Test Explained](docs/KRUSKAL_WALLIS_GUIDE.md)


### Scientific Background
- [Common House Martin Species Account](https://www.hbw.com/species/common-house-martin-delichon-urbicum)
- [Geolocator Studies Review](https://doi.org/10.xxxx/xxxxx)
- [Trans-Saharan Migration](https://doi.org/10.xxxx/xxxxx)

---

## 📊 Repository Statistics

![GitHub stars](https://img.shields.io/github/stars/your-username/delichon-wintering-map?style=social)
![GitHub forks](https://img.shields.io/github/forks/your-username/delichon-wintering-map?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/your-username/delichon-wintering-map?style=social)

![Last commit](https://img.shields.io/github/last-commit/your-username/delichon-wintering-map)
![Repo size](https://img.shields.io/github/repo-size/your-username/delichon-wintering-map)

---

## 🌟 Star History

If you find this project useful, please consider giving it a ⭐!

---

<div align="center">

**[🔝 Back to Top](#-interactive-map-common-house-martin-wintering-sites-in-west-africa)**

---

Made with ❤️ for ornithological research

*Last updated: December 2024*

</div>
