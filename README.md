# NYC Taxi Trip Duration - Exploratory Data Analysis 🚕

A comprehensive exploratory data analysis of New York City taxi trip data, focusing on understanding trip patterns, temporal trends, and the relationships between various features that influence trip duration.

[![Python](https://img.shields.io/badge/Python-3.13-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Latest-green.svg)](https://pandas.pydata.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)

---

## 📊 Project Overview

This project performs an in-depth exploratory data analysis on the NYC Taxi Trip Duration dataset from Kaggle. The analysis uncovers valuable insights into taxi trip patterns, temporal trends, and geographical distributions across New York City.

### Dataset Information
- **Source**: [Kaggle - NYC Taxi Trip Duration](https://www.kaggle.com/datasets/yasserh/nyc-taxi-trip-duration)
- **Records**: 1,458,644 taxi trips
- **Original Features**: 11 columns
- **Engineered Features**: 11 additional columns
- **Time Period**: 2016 (January - June)

---

## 🎯 Key Features Analyzed

### Original Dataset Features

| Feature | Description |
|---------|-------------|
| `id` | Unique identifier for each trip |
| `vendor_id` | Code indicating the provider (1 or 2) |
| `pickup_datetime` | Date and time when meter was engaged |
| `dropoff_datetime` | Date and time when meter was disengaged |
| `passenger_count` | Number of passengers in vehicle |
| `pickup_longitude` | Longitude coordinate of pickup location |
| `pickup_latitude` | Latitude coordinate of pickup location |
| `dropoff_longitude` | Longitude coordinate of dropoff location |
| `dropoff_latitude` | Latitude coordinate of dropoff location |
| `store_and_fwd_flag` | Trip record storage flag (Y/N) |
| `trip_duration` | **Target Variable** - Duration in seconds |

### Engineered Features

The analysis includes sophisticated feature engineering to extract temporal and spatial insights:

**Temporal Features:**
- `pickup_day` / `dropoff_day` - Day name (Monday-Sunday)
- `pickup_day_no` / `dropoff_day_no` - Day number (0-6)
- `pickup_hour` / `dropoff_hour` - Hour of day (0-23)
- `pickup_month` / `dropoff_month` - Month number (1-12)
- `pickup_timeofday` / `dropoff_timeofday` - Time period categories:
  - **Morning** (6:00 AM - 11:59 AM)
  - **Afternoon** (12:00 PM - 3:59 PM)
  - **Evening** (4:00 PM - 9:59 PM)
  - **Late Night** (10:00 PM - 5:59 AM)

**Spatial Features:**
- `distance` - Great circle distance in kilometers (calculated using geopy)

---

## 🔍 Analysis Sections

### 1. Data Quality Assessment
- ✅ **No missing values** detected across all features
- Dataset shape: 1,458,644 rows × 11 columns
- Data type validation and conversion
- Unique value counts per feature
- Statistical summary of numerical features

### 2. Feature Engineering
- **DateTime Conversion**: Transformed pickup and dropoff timestamps from object to datetime64 format
- **Temporal Extraction**: Created day, hour, and month features for both pickup and dropoff times
- **Time Categorization**: Implemented custom function to categorize trips into time-of-day segments
- **Distance Calculation**: Utilized geopy's great_circle method to compute trip distances from coordinates

### 3. Univariate Analysis

#### Vendor Distribution
- Analysis of trip distribution across 2 vendors
- Vendor performance metrics

#### Passenger Count Patterns
- Distribution ranges from 0 to 9 passengers
- Insights into anomalies (0 passenger trips)
- Most common passenger counts

#### Store and Forward Flag
- Analysis of trips stored in vehicle memory
- Connection reliability patterns

#### Trip Duration Distribution
- Statistical analysis of trip durations
- Identification of outliers and extreme values
- Duration trends and patterns

#### Day of Week Analysis
- **Pickup Day Distribution**: Weekday vs. weekend patterns
- **Dropoff Day Distribution**: Temporal consistency check
- Peak demand days identification

#### Time of Day Patterns
- **Peak Hours**: Evening shows highest trip volume
- **Distribution across time periods**:
  - Morning trips
  - Afternoon trips
  - Evening trips (busiest)
  - Late night trips

#### Monthly Trends
- Trip volume analysis across months (January - June 2016)
- Seasonal patterns and variations

### 4. Bivariate Analysis

#### Distance vs. Trip Duration
- Correlation analysis between distance and duration
- Identification of anomalies:
  - Zero-distance trips with high duration
  - Unusual trip patterns
- Scatter plot visualization of relationship

---

## 🛠️ Technologies & Libraries

```python
# Core Data Analysis
import numpy as np
import pandas as pd

# Visualization
import matplotlib.pyplot as plt
import seaborn as sns

# Geospatial Calculations
from geopy.distance import great_circle

# Data Acquisition
import kagglehub

# Utilities
import datetime as dt
import warnings
```

---

## 📁 Project Structure

```
EDA-NYC_Taxi_Trip/
│
├── data/
│   └── raw/
│       └── NYC.csv                 # Raw dataset
│
├── notebook/
│   └── eda_nyc_taxi_trip.ipynb    # Main analysis notebook
│
├── README.md                       # Project documentation
│
└── requirements.txt                # Python dependencies
```

---

## 🚀 Getting Started

### Prerequisites
```bash
Python 3.13 or higher
Jupyter Notebook or JupyterLab
```

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/upadhayshubham/EDA-NYC_Taxi_Trip.git
cd EDA-NYC_Taxi_Trip
```

2. **Install required packages**
```bash
pip install numpy pandas matplotlib seaborn kagglehub geopy
```

3. **Download the dataset**
The notebook automatically downloads the dataset using kagglehub:
```python
import kagglehub
path = kagglehub.dataset_download("yasserh/nyc-taxi-trip-duration")
```

4. **Launch Jupyter Notebook**
```bash
jupyter notebook notebook/eda_nyc_taxi_trip.ipynb
```

---

## 📈 Key Insights

### 🕐 Temporal Insights
- **Busiest Time**: Evening hours dominate taxi demand
- **Day Patterns**: Weekday patterns differ from weekend usage
- **Monthly Trends**: Identifiable seasonal variations across the analyzed period

### 👥 Passenger Insights
- **Solo Riders**: Single-passenger trips are most common
- **Group Travel**: Limited trips with 7+ passengers
- **Anomalies**: Some trips recorded with 0 passengers (potential data entry errors)

### 📍 Distance & Duration
- **Correlation**: Positive relationship between distance and duration observed
- **Anomalies Detected**: Zero-distance trips with significant durations
- **Pickup/Dropoff Coordinates**: Mostly concentrated in NYC geographical bounds

### 🚖 Vendor Performance
- Two main vendors operate in the dataset
- Relatively balanced distribution between vendors

---

## 🎨 Visualizations

The analysis includes multiple visualization types:
- 📊 Count plots for categorical distributions
- 📈 Scatter plots for relationship analysis
- 📉 Distribution plots for continuous variables
- 🗓️ Time series visualizations for temporal patterns

---

## 🔮 Future Enhancements

- [ ] Implement outlier detection and treatment strategies
- [ ] Add geospatial heatmaps for popular pickup/dropoff zones
- [ ] Perform correlation analysis between all features
- [ ] Create interactive visualizations using Plotly
- [ ] Develop predictive models for trip duration
- [ ] Analyze traffic patterns by hour and day combinations
- [ ] Investigate weather impact on trip patterns
- [ ] Create dashboard for real-time insights

---

## 📝 Findings Summary

### Data Quality
- Clean dataset with no missing values
- Anomalies identified in passenger count and distance calculations
- Consistent temporal data across pickup and dropoff times

### Feature Engineering Success
- Successfully created 11 new meaningful features
- Time-based categorization provides actionable insights
- Distance calculation enables spatial analysis

### Pattern Discovery
- Clear temporal patterns in taxi usage
- Evening hours show peak demand
- Distance and duration show expected positive correlation
- Identified edge cases requiring further investigation

---

## 👤 Author

**Shubham Upadhay**
- GitHub: [@upadhayshubham](https://github.com/upadhayshubham)
- Project Link: [EDA-NYC_Taxi_Trip](https://github.com/upadhayshubham/EDA-NYC_Taxi_Trip)

---

## 🙏 Acknowledgments

- Dataset provided by [Kaggle](https://www.kaggle.com/datasets/yasserh/nyc-taxi-trip-duration)
- NYC Taxi and Limousine Commission for original data collection
- Seaborn and Matplotlib communities for visualization tools
- Geopy library for distance calculations

---

## 📄 License

This project is open source and available for educational purposes.

---

## 📧 Contact

For questions, suggestions, or collaboration opportunities, feel free to reach out through GitHub issues or pull requests.

---

<div align="center">

### ⭐ If you found this analysis helpful, please consider giving it a star!

**Made with 🎯 for Data Science Learning**

</div>
