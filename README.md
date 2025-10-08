# German EU Parliament Election Analysis (2019) - Data Science 1 Mini Project

## 📋 Project Overview
This project analyzes and visualizes voting patterns in the 2019 European Parliament Election across Germany at the NUTS-3 regional level. Using geospatial data and electoral statistics, the analysis maps party vote shares and identifies regional political preferences across 401 German administrative districts.

## 👥 Author
- **Name:** Nahian Ibnat
- **Course:** Data Science 1
- **Institution:** CEU (Central European University) - MA EDP
- **Semester:** Fall 2025


## 📁 Repository Structure
```
Ibnat_miniproject/
├── Code/
│   ├── Party_Vote.R                  # Main R script with complete analysis
│   ├── Vote.Rmd                      # R Markdown version (if applicable)
│   └── Vote.html                     # Rendered HTML output
├── Data/
│   └── eu_ned_ep.csv                 # Raw electoral data (Harvard Dataverse)
├── Output/
│   ├── map_afd.png                   # Visualization: AFD vote share
│   ├── map_major_parties.png         # Visualization: Panel map of major parties
│   └── map_winners.png               # Visualization: Winning party by region
├── LICENSE                           # License file
├── Project.pdf                       # Project documentation
└── README.md                         # Project documentation (this file)
```

## 🔧 Technologies Used
- **R** (version 4.x recommended)
- **Key Libraries:**
  - `tidyverse` - Data manipulation and visualization (ggplot2, dplyr, readr, tidyr)
  - `sf` - Spatial features for geospatial analysis
  - `giscoR` - Eurostat GISCO geographic data API
  - `viridis` - Colorblind-friendly color palettes
  - `pacman` - Package management

## 📊 Dataset

### Electoral Data
- **Name:** European National Election Dataset (EU NED) - European Parliament
- **Source:** [Harvard Dataverse](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/IQRYP5)
- **Description:** Comprehensive electoral returns for European Parliament elections
- **Coverage:** Germany, 2019 EP Election, NUTS-3 level
- **Key Variables:**
  - `country_code` - Country identifier (DE for Germany)
  - `year` - Election year (2019)
  - `nutslevel` - Geographic aggregation level (3)
  - `nuts2016` - NUTS region code
  - `party_abbreviation` - Political party code
  - `partyvote` - Votes received by party
  - `totalvote` - Total votes cast in region

### Geographic Data
- **Source:** Eurostat GISCO (Geographic Information System of the Commission)
- **Level:** NUTS-3 (Nomenclature of Territorial Units for Statistics)
- **Regions:** 401 administrative districts in Germany
- **Projection:** EPSG:3035 (Lambert Azimuthal Equal-Area)
- **Year:** 2016 boundaries

## 🚀 Getting Started

### Prerequisites
- R (version 4.0 or higher)
- RStudio (recommended for interactive development)
- Internet connection (for downloading geographic data via giscoR)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/Nahian2400062/Ibnat_miniproject.git
cd Ibnat_miniproject
```

2. Install required R packages (automated environment setup):
```r
# The script automatically installs packages using pacman
# Just run the script and dependencies will be installed

# Or install manually:
if (!require("pacman")) install.packages("pacman")
pacman::p_load(tidyverse, sf, giscoR, readr, tidyr, ggplot2, viridis)
```

3. **Update the working directory** in `Code/Party_Vote.R` (line 6):
```r
setwd("YOUR/PATH/TO/Ibnat_miniproject")
```

### Running the Project

**One-Step Execution (Fully Automated):**
```r
# Open R or RStudio in the project directory
source("Code/Party_Vote.R")
```

This single command will:
- ✅ Install all required packages
- ✅ Download NUTS-3 geographic boundaries for Germany
- ✅ Load and process electoral data from Data/ folder
- ✅ Calculate vote share percentages
- ✅ Generate three comprehensive visualization maps
- ✅ Save outputs to Output/ folder
- ✅ Display all plots automatically

**Output files** are saved in the `Output/` directory:
- `map_afd.png` - AFD vote share choropleth
- `map_major_parties.png` - Five-party panel comparison
- `map_winners.png` - Electoral geography winner map

## 📈 Analysis Workflow

### 1. **Environment Setup**
   - Clear workspace and set working directory
   - Load required packages using `pacman`
   - Configure automatic package installation

### 2. **Geographic Data Acquisition**
   - Download NUTS-3 boundaries for Germany from Eurostat GISCO
   - Use 2016 administrative boundaries for consistency with electoral data
   - Apply EPSG:3035 projection (standard for European mapping)
   - Verify spatial features with geometry plot

### 3. **Electoral Data Processing**
   - Import EU NED dataset from Harvard Dataverse
   - Filter for Germany (country_code == "DE")
   - Filter for 2019 EP election
   - Filter for NUTS-3 level aggregation
   - Calculate vote share percentages: `(partyvote / totalvote) × 100`
   - Clean and standardize party abbreviations

### 4. **Data Integration**
   - Join electoral data with geographic boundaries
   - Match on NUTS_ID codes
   - Create unified spatial dataframe for mapping

### 5. **Visualization Creation**

   **Map 1: AFD Regional Strongholds**
   - Choropleth map of Alternative für Deutschland (AFD) vote share
   - Viridis color scale (colorblind-friendly)
   - Highlights regional variation in right-wing populist support
   
   **Map 2: Major Party Comparison (Panel Map)**
   - Faceted comparison of five major parties:
     - **CDU** - Christian Democratic Union
     - **CSU** - Christian Social Union (Bavaria)
     - **SPD** - Social Democratic Party
     - **GRÜNE** - Alliance 90/The Greens
     - **AFD** - Alternative für Deutschland
   - Fixed scales for direct comparison
   - Reveals distinct regional patterns for each party
   
   **Map 3: Electoral Geography (Winner Map)**
   - Categorical map showing which party won each NUTS-3 region
   - Custom color scheme aligned with party branding:
     - CDU: Black
     - CSU: Blue
     - SPD: Red
     - GRÜNE: Green
     - AFD: Light Blue
   - Shows clear geographic clustering of party support

## 📊 Analysis Summary

### Descriptive Statistics
The analysis includes:
- **401 NUTS-3 regions** analyzed across Germany
- **Vote share calculations** for all parties
- **Regional comparison** across five major parties
- **Winner identification** for each administrative district

### Key Analytical Techniques
- **Spatial joins** merging electoral and geographic data
- **Grouped aggregations** finding maximum vote share per region
- **Faceted visualizations** for multi-party comparison
- **Choropleth mapping** showing continuous vote share data
- **Categorical mapping** displaying discrete winner categories


## 🔍 Key Insights

Based on the 2019 EU Parliament Election in Germany:

### Regional Political Patterns
- **AFD Support:** Concentrated in eastern German states (former East Germany)
- **CSU Dominance:** Exclusive to Bavaria (constitutional restriction)
- **SPD Traditional Base:** Urban industrial regions and northern Germany
- **GRÜNE Strength:** University cities and urban areas
- **CDU Breadth:** Widespread support across western and southern regions

### Electoral Geography
- Clear **East-West divide** in voting behavior
- **Urban-rural split** particularly visible in Green party support
- **Regional party systems:** Bavaria (CSU) vs. rest of Germany (CDU)
- **Persistence of historical patterns:** Post-reunification political geography still evident

## 🔍 Future Work

### Visualization Enhancements
- **Interactive maps:** Shiny dashboard with hover information
- **Animation:** Show electoral change over time
- **Bivariate mapping:** Combine vote share with demographic variables
- **Cartogram:** Area-adjusted maps based on population

### Comparative Research
- **Cross-country comparison:** Extend analysis to other EU member states
- **Multi-level analysis:** Compare NUTS-1, NUTS-2, and NUTS-3 patterns
- **National elections:** Compare EP results with Bundestag elections

## 🛠️ Troubleshooting

**Common Issues:**

1. **Working Directory Error:**
   ```r
   # Update the path on line 6 of Code/Party_Vote.R
   setwd("YOUR/ACTUAL/PATH")
   ```

2. **Package Installation Issues:**
   ```r
   # Install packages manually if pacman fails
   install.packages(c("tidyverse", "sf", "giscoR", "viridis"))
   ```

3. **giscoR Download Failure:**
   ```r
   # Try clearing cache and re-downloading
   giscoR::gisco_get_nuts(country = "DE", resolution = "3", 
                          year = "2016", update_cache = TRUE)
   ```

4. **Projection/CRS Warnings:**
   - These are normal when working with spatial data
   - EPSG:3035 is the correct projection for European analysis

5. **Memory Issues:**
   - NUTS-3 level data can be memory-intensive
   - Close other applications if R crashes
   - Consider using NUTS-2 (fewer regions) for testing

## 📚 References & Data Sources

### Primary Data
- **Schmitt, Hermann; Braun, Daniela; Popa, Sebastian Adriean; Teperoglou, Eftichia, 2021**, "European Parliament Election Study 2019, Voter Study", Harvard Dataverse, V1. [DOI: 10.7910/DVN/IQRYP5](https://doi.org/10.7910/DVN/IQRYP5)

### Geographic Data
- **Eurostat GISCO** - Geographic Information System of the Commission
- NUTS (Nomenclature of Territorial Units for Statistics) 2016 boundaries

### Methodological Resources
- Color accessibility: [Coblis Color Blindness Simulator](https://www.color-blindness.com/coblis-color-blindness-simulator/)
- NUTS-3 GDP tutorial: [YouTube](https://youtu.be/thAB4IzplQA)

## 📝 Citation

When using this analysis or code, please cite:

```bibtex
@misc{nahian2025german,
  author = {Nahian},
  title = {German EU Parliament Election Analysis 2019: Regional Voting Patterns at NUTS-3 Level},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/Nahian2400062/Ibnat_miniproject}
}
```

And cite the original data source (Schmitt et al., 2021).

## 📜 License
This project is created for educational purposes as part of the Data Science 1 course at CEU.

## 📧 Contact
- **GitHub:** [@Nahian2400062](https://github.com/Nahian2400062)
- **Institution:** Central European University (CEU)
- **Program:** MA in Economic Data and Policy (EDP)

## 🙏 Acknowledgments
- **Harvard Dataverse** for hosting the EU NED dataset
- **Eurostat GISCO** for providing high-quality geographic data
- **Data Science 1** course instructors and teaching assistants at CEU
- R community for excellent spatial analysis packages (sf, giscoR)
- Viridis developers for colorblind-friendly palettes

---
*Project completed as part of CEU's Data Science 1 course, Fall 2025 semester.*
