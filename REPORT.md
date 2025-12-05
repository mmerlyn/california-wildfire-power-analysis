# Wildfire-Induced Power Outages: A Data Mining Analysis

**CS653 Data Mining Final Project**
**Team:** Merlyn Mercylona, Jeevan Antony, Om Sai Hiremath
**San Diego State University**

---

## Project Overview

Analyzing the relationship between wildfires and power outages in California using data mining techniques to uncover patterns and build predictive models.

**Dataset:** 210 power outages (2000-2016) + 412,000+ wildfire records
**Features Engineered:** 35

---

## Research Questions

1. What temporal patterns exist between wildfire occurrence and power outages?
2. Can we predict power outage severity based on wildfire characteristics?
3. What feature patterns distinguish wildfire-related from non-wildfire outages?
4. How do seasonal factors influence the wildfire-outage relationship?

---

## Data Sources

| Category      | Datasets                                                          |
| ------------- | ----------------------------------------------------------------- |
| Power Outages | Purdue (2000-2016), DOE Grid Disruptions (2000-2014)              |
| Wildfires     | CAL FIRE (2013-2020), FPA FOD (1.88M fires), NASA FIRMS Satellite |

---

## Methodology

- **Association Rules** reveal _what conditions co-occur_ with severe outages
- **Clustering** shows _how outages naturally group_ without predefined labels
- **Classification** answers _"will this be severe?"_ (actionable prediction)
- **Regression** answers _"how long will it last?"_ (R²=0.12 shows duration is inherently unpredictable)
- **Time Series** answers _"when do outages peak?"_ and identifies seasonal preparedness windows

| Technique                   | Purpose                                                                                                                         | Research Question                       |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------- |
| **Association Rule Mining** | Discover co-occurrence patterns between fire conditions and outage characteristics (e.g., "high fire activity → severe outage") | RQ3: Feature patterns                   |
| **Clustering**              | Identify natural groupings of outages to reveal distinct profiles (fire-season vs storm-season outages)                         | RQ3: Feature patterns                   |
| **Classification**          | Predict whether an outage will be high-severity based on fire/weather features — enables proactive resource allocation          | RQ2: Predict severity                   |
| **Regression**              | Attempt to predict outage duration for planning purposes (limited success due to high variance)                                 | RQ2: Predict severity                   |
| **Time Series Analysis**    | Uncover seasonal cycles, trends, and lag effects between fire activity and outages                                              | RQ1 & RQ4: Temporal & seasonal patterns |

---

## Results

### Wildfire vs Non-Wildfire Outages

| Metric             | Wildfire-Related | Non-Wildfire | Difference |
| ------------------ | ---------------- | ------------ | ---------- |
| Mean Duration      | 2,856 min        | 1,576 min    | **+81%**   |
| Customers Affected | 316,401          | 189,362      | **+67%**   |
| 7-day Acres Burned | 181,106          | 17,313       | **+946%**  |

### Classification Performance (Predicting High-Severity)

| Model             | Accuracy  | F1 Score  | ROC-AUC   |
| ----------------- | --------- | --------- | --------- |
| Decision Tree     | 0.786     | 0.690     | 0.735     |
| Random Forest     | 0.738     | 0.560     | 0.753     |
| **SVM (RBF)**     | **0.810** | **0.733** | **0.867** |
| Gradient Boosting | 0.714     | 0.455     | 0.706     |

**Best Model:** SVM with 81% accuracy

### Regression Performance (Predicting Duration)

| Model         | R²    | MAE (log) |
| ------------- | ----- | --------- |
| Random Forest | 0.123 | 1.562     |
| Lasso         | 0.040 | 1.733     |

Duration prediction remains challenging due to high variance.

### Clustering: 3 Distinct Outage Profiles

| Cluster | Season | Fire Activity | Characteristics              |
| ------- | ------ | ------------- | ---------------------------- |
| 0       | Summer | High          | 96% with active fires nearby |
| 1       | Spring | Moderate      | System operability issues    |
| 2       | Winter | Low           | Storm-related, high severity |

### Key Association Rules

| Rule                                         | Confidence | Lift |
| -------------------------------------------- | ---------- | ---- |
| High acres_7day → active fire                | 0.97       | 1.10 |
| Severe weather + Fire season → High severity | 0.72       | 1.98 |

### Temporal Patterns

- **Peak Month:** July (28 outages)
- **Fire Season (Jun-Nov):** 49% of outages
- **Bimodal Pattern:** Summer (wildfires) + Winter (storms)
- **Rolling metrics** (7-day, 30-day) outperform single-day counts

---

## Top Predictive Features

1. **total_frp** - Fire Radiative Power
2. **acres_7day** - 7-day rolling acres burned
3. **fires_30day** - 30-day rolling fire count
4. **max_frp** - Maximum FRP
5. **CAUSE.CATEGORY** - Outage cause

---

## Recommendations

### For Utility Companies

- Implement **rolling fire activity monitoring** (7-day, 30-day metrics)
- Deploy **predictive models** for resource allocation
- Maintain **dual-season preparedness** (fire + storm)
- Integrate **satellite FRP data** for real-time monitoring

### For Future Research

- Expand dataset to include 2017-present (recent major fires)
- Add direct weather variables (wind, humidity, temperature)
- Develop spatial-temporal models with geographic granularity

---

## Limitations

- Small sample size (210 outages)
- Only 7.6% explicitly labeled as wildfire-related
- Data ends in 2016 (missing recent fire seasons)
- Limited direct weather measurements

---

## Conclusion

- **Wildfire activity significantly impacts** power outage severity (+81% duration, +67% customers)
- **Classification models achieve 81% accuracy** in predicting high-severity outages
- **Rolling fire metrics** are stronger predictors than single-day counts
- **Bimodal seasonality** requires year-round preparedness
- **SVM and ensemble methods** provide best predictive performance

---

_CS653 Data Mining | San Diego State University | December 2024_
