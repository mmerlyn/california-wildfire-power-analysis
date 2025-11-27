# Wildfire-Induced Power Outages: A Data Mining Analysis

## CS653 Data Mining Final Project

### Project Overview

This project analyzes the relationship between wildfires and power outages in California, with a focus on the San Diego area (SDG&E service territory). Using data mining techniques, we explore patterns, correlations, and predictive models for wildfire-related power disruptions.

### Research Questions

1. What temporal patterns exist between wildfire occurrence and power outages?
2. Can we predict power outage severity based on wildfire characteristics and weather conditions?
3. What are the common feature patterns in wildfire-related vs. non-wildfire outages?
4. How do seasonal and climatic factors influence the wildfire-outage relationship?

### Datasets

#### ✅ Power Outage Datasets

**Purdue University Power Outage Dataset (2000-2016)**

- Source: https://engineering.purdue.edu/LASCI/research-data/outages/outagerisks
- Kaggle: https://www.kaggle.com/datasets/autunno/15-years-of-power-outages
- Coverage: Major U.S. power outages (≥50,000 customers or ≥300 MW loss)
- Features: Duration, customers affected, location, cause, weather, economic data
- Downloaded: `purdue_power_outages_2000_2016.xlsx` (645 KB)

**DOE Grid Disruption Events (2000-2014)**

- Source: Department of Energy
- Coverage: Grid disruption events with geographic areas and NERC regions
- Downloaded: `doe_grid_disruptions_2000_2014.csv` (262 KB)

#### ✅ Wildfire Datasets

**CAL FIRE Incidents (2013-2020)**

- Source: https://www.kaggle.com/datasets/ananthu017/california-wildfire-incidents-20132020
- Features: Acres burned, location, dates, structures affected
- Downloaded: `calfire_incidents_2013_2020.csv` (948 KB)

**1.88M US Wildfires (FPA FOD)**

- Source: https://www.kaggle.com/datasets/rtatman/188-million-us-wildfires
- Coverage: 1.88 million US wildfires (1992-2015)
- Features: Detailed fire records with county FIPS codes, cause, size class
- Downloaded: `us_wildfires_1.88m_fpa_fod.sqlite` (759 MB)

**NASA FIRMS Satellite Fire Detections**

- Source: NASA Fire Information for Resource Management System
- Coverage: Satellite-detected fire hotspots (2000-2022)
- Downloaded in `nasa_firms_wildfire_data/`:
  - `california_fires_2000_2021_basic.csv` - CA fires (lat, lon, date, confidence)
  - `california_fires_2000_2021_with_frp.csv` - CA fires with Fire Radiative Power
  - `california_fires_2000_2022_extended.csv` - CA fires through March 2022
  - `usa_fires_2000_2022_raw.csv` - Full USA fire detections

### Project Structure

```
wildfire-power-analysis/
├── data/
│   ├── raw/                                         # Original downloaded datasets
│   │   ├── purdue_power_outages_2000_2016.xlsx     # Purdue power outage dataset
│   │   ├── doe_grid_disruptions_2000_2014.csv     # DOE grid disruption events
│   │   ├── calfire_incidents_2013_2020.csv        # CAL FIRE incidents
│   │   ├── us_wildfires_1.88m_fpa_fod.sqlite      # 1.88M US wildfires database
│   │   └── nasa_firms_wildfire_data/              # NASA FIRMS satellite data
│   │       ├── california_fires_2000_2021_basic.csv
│   │       ├── california_fires_2000_2021_with_frp.csv
│   │       ├── california_fires_2000_2022_extended.csv
│   │       └── usa_fires_2000_2022_raw.csv
│   └── processed/                                   # Cleaned and merged datasets
├── notebooks/                                       # Jupyter notebooks for analysis
├── scripts/                                         # Python scripts for data processing
├── outputs/
│   ├── figures/                                     # Visualizations and plots
│   └── models/                                      # Trained models and results
├── README.md
└── requirements.txt
```

### Methodology

#### 1. Data Collection & Preprocessing

- Download and consolidate datasets
- Filter for California records
- Handle missing values and outliers
- Standardize date/time formats and geographic coordinates

#### 2. Feature Engineering

- **Temporal Features**: Month, season, year, day of week, wildfire season indicator
- **Geographic Features**: Distance to nearest active fire, county-level aggregations
- **Wildfire Features**: Acres burned, fire duration, number of concurrent fires
- **Weather Features**: Temperature, wind speed, precipitation, drought index
- **Outage Features**: Duration categories, customer impact levels

#### 3. Data Mining Techniques

- **Association Rule Mining**: Discover patterns between wildfire conditions and outage characteristics
- **Clustering**: Group similar outage events (K-means, DBSCAN, Hierarchical)
- **Classification**: Predict outage severity (Decision Trees, Random Forest, SVM)
- **Time Series Analysis**: Seasonal patterns and trend analysis
- **Regression**: Predict outage duration and customer impact

#### 4. Evaluation Metrics

- Classification: Accuracy, Precision, Recall, F1-Score, ROC-AUC
- Clustering: Silhouette Score, Davies-Bouldin Index
- Regression: MAE, RMSE, R²
- Association Rules: Support, Confidence, Lift

### References

1. Purdue University LASCI Research Data on Power Outages
2. NOAA National Centers for Environmental Information
3. CAL FIRE Incident Database
4. NASA FIRMS (Fire Information for Resource Management System)

### Contributors

- Merlyn Mercylona, Jeevan Antony, Om Sai Hiremath
- Course: CS653 Data Mining
- Institution: San Diego State University

### License

See LICENSE file for details
