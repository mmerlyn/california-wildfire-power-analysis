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

#### ✅ Primary Dataset

**Purdue University Power Outage Dataset (2000-2016)**

- Source: https://engineering.purdue.edu/LASCI/research-data/outages/outagerisks
- Kaggle: https://www.kaggle.com/datasets/autunno/15-years-of-power-outages
- Coverage: Major U.S. power outages (≥50,000 customers or ≥300 MW loss)
- Features: Duration, customers affected, location, cause, weather, economic data
- Downloaded: `PowerOutages.xlsx` (645 KB)

#### ✅ Supplementary Datasets

**California Wildfire Datasets**

1. **California Wildfires (2000-2022)**: https://www.kaggle.com/datasets/avkashchauhan/california-wildfire-dataset-from-2000-2021
   - Downloaded: `california_wildfire_2000_2022.csv` (54 MB, 1.1M records)

2. **California Fire Incidents (2013-2020)**: https://www.kaggle.com/datasets/ananthu017/california-wildfire-incidents-20132020
   - Downloaded: `california_wildfire_incidents_2013_2020.csv` (948 KB)

3. **1.88M US Wildfires**: https://www.kaggle.com/datasets/rtatman/188-million-us-wildfires
   - Downloaded: `us_wildfires_1.88m.sqlite` (759 MB)

**Additional Wildfire Data**

- `ca_daily_fire_2000_2021-v2.csv` - Enhanced with FRP (fire radiative power) data
- USA-wide datasets for broader context

### Project Structure

```
DataMiningProject/
├── data/
│   ├── raw/                                         # Original downloaded datasets
│   │   ├── PowerOutages.csv                        # Purdue dataset (CSV format)
│   │   ├── PowerOutages.xlsx                       # Purdue dataset (Excel format)
│   │   ├── california_wildfire_2000_2022.csv       # Primary CA wildfire data (2000-2022)
│   │   ├── california_wildfire_incidents_2013_2020.csv  # CA fire incidents
│   │   ├── us_wildfires_1.88m.sqlite               # 1.88M US wildfires database
│   │   └── wildfire_supplementary/                 # Additional wildfire datasets
│   │       ├── ca_daily_fire_2000_2021-v2.csv     # Enhanced CA data (with FRP)
│   │       ├── ca_daily_fire_2000_2021.csv        # CA fires 2000-2021
│   │       └── usa_daily_fire_2000_march25-2022-raw.csv  # Full USA dataset
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
