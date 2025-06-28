# Climate-Change-Forecasting-Project
This project explores and forecasts climate change patterns over 60 years (1960–2020) using temperature and precipitation data from five major U.S. cities: Boston, Los Angeles, New York, Washington, D.C., and Chicago. It uses Python-based data analysis, visualization, and time series forecasting techniques to extract insights and build a 5-year forecast for average temperature trends using Facebook Prophet.

## Dataset

**Source**: Download here: https://kilthub.cmu.edu/articles/dataset/Compiled_daily_temperature_and_precipitation_data_for_the_U_S_cities/7890488

**Observations**: 111,405

## Features:

**Date** — Observation date

**tmax** — Maximum temperature (F)

**tmin** — Minimum temperature (F)

**prcp** — Daily precipitation (inches)

**tavg** — Average temperature

City, Year, Month

## Objective
- Detect long-term trends and seasonal patterns in temperature and precipitation.
- Visualize key insights using static and interactive plots.
- Forecast future temperature trends using Facebook Prophet.

## Project Structure
- README.md
- ClimateChange(1).ipynb
- ClimateChangeDataset.csv

## Setup and Requirements

To get started:

**Libraries used**

- **pandas** – for data manipulation  
- **seaborn** & **matplotlib** – for static data visualizations  
- **plotly** – for interactive charts  
- **prophet** – for time series forecasting  
- **cmdstanpy** – for backend performance with Prophet (optional but useful)  
- **scipy** – for statistical analysis

Example: Importing the Required Libraries

Below is a code snippet showing how the relevant libraries are used in this project:
# Import the relevant libraries
import os
import subprocess
import cmdstanpy
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
from prophet import Prophet
from prophet.diagnostics import cross_validation
from scipy.stats import zscore
import plotly.express as px
import plotly.graph_objects as go

## Installation

Install Facebook Prophet

## Usage

1. Download the dataset from the [provided link](https://kilthub.cmu.edu/articles/dataset/Compiled_daily_temperature_and_precipitation_data_for_the_U_S_cities/7890488) and save it in the `data/` folder.
2. Launch the notebooks in order for a step-by-step workflow:
   - Data loading & cleaning
   - Exploratory analysis & visualization
   - Forecasting with Prophet

## 📊 Analytical Steps & Visualizations

- **Data Quality Checks:** Duplicate removal, missing value handling.
- **Distributions & Outliers:** Boxplots and histograms for all cities.
- **Correlation Analysis:** Heatmap of feature correlations.
- **Trend Analysis:** Yearly average max/min temperature and precipitation trends per city.
- **Decade-wise Heatmaps:** Monthly average temperatures by decade for each city.
- **Rolling Averages:** 365-day rolling mean temperature trends for smoothing.
- **Pairplots:** Visual comparison of temperature and precipitation variables across cities.
- **Interactive Time Series:** Zoomable, interactive temperature plots by city.
- **Forecasting:** 5-year temperature projections using Facebook Prophet, with components plots.

**Examples of Visualizations and their respective code snippets**
## 📈 Visualizations

### Rolling Average and Anomaly Detection
![Rolling Average and Anomaly Detection](images/Rolling%20Average%20and%20Anomaly%20Detection.png)

The code snippet:
 **Rolling average and anomaly detection**
for city in cities:
    city_data = df[df['City'] == city].set_index('Date').sort_index()
    city_data['tavg_rolling'] = city_data['tavg'].rolling(window=365, min_periods=1).mean()
    plt.figure(figsize=(12,6))
    plt.plot(city_data['tavg'], alpha=0.3, label='Daily Avg Temp')
    plt.plot(city_data['tavg_rolling'], color='red', label='365-day Rolling Avg')
    plt.title(f'Annual Rolling Average Temperature Trend — {city}')
    plt.legend()
    plt.show()
 **Anomaly detection: Z-score (>3 std dev)**
df['tavg_z'] = df.groupby('City')['tavg'].transform(zscore)
anomalies = df[np.abs(df['tavg_z']) > 3]
plt.figure(figsize=(14,6))
sns.scatterplot(data=df, x='Date', y='tavg', hue='City', alpha=0.15, legend=False)
sns.scatterplot(data=anomalies, x='Date', y='tavg', hue='City', marker='X', s=100, legend=False)
plt.title("Temperature Anomalies (>3σ)")
plt.show()

### Decadewise Monthly Average Heatmap
![Decadewise Monthly Average Heatmap](images/Decadewise%20monthly%20average%20heatmap.png)

Example of code snippet:
**Decade-wise monthly average heatmaps**
month_order = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
for city in cities:
    city_data = df[df['City'] == city].copy()
    city_data['Decade'] = (city_data['Year'] // 10) * 10
    avg_by_decade = city_data.groupby(['Decade', 'Month'])['tavg'].mean().reset_index()
    pivot = avg_by_decade.pivot(index='Decade', columns='Month', values='tavg')[month_order]
    plt.figure(figsize=(10,6))
    sns.heatmap(pivot, annot=True, fmt='.1f', cmap='coolwarm', cbar=True)
    plt.title(f'Monthly Average Temperatures by Decade - {city}')
    plt.show()

### Correlation Heatmap Graph
![Correlation Heatmap Graph](images/Correlation%20heatmap%20graph.png)

The code snippet:
# Correlation heatmap
corrmat = df[['tmax','tmin','tavg','prcp']].corr()
plt.figure(figsize=(6,4))
sns.heatmap(corrmat, annot=True, cmap='coolwarm', fmt='.2f')
plt.title('Correlation Matrix of Weather Variables')
plt.show()

### Boxplot of Temperature Distribution per City
![Boxplot of Temperature Distribution per City](images/Boxplot%20of%20distribution%20of%20temperature%20per%20city.png)

The code snippet:
# Boxplot by city
plt.figure(figsize=(10,5))
sns.boxplot(data=df, x='City', y='tavg')
plt.title("Distribution of Average Temperature by City")
plt.show()

## Insights

Average temperatures show an increasing trend across decades especially in summer months. Winters are less cold in recent decades.

Precipitation varies across cities but generally remains within a range.

Seasonal variation is visible, with predictable summer peaks and winter lows.

Prophet forecasts suggest a continued warming trend.

## Contributing

Pull requests and suggestions are welcome! If you find bugs or have enhancement ideas, open an issue or PR.

## License

This project is released under the MIT License. The dataset is credited to Carnegie Mellon University's KiltHub.

## Author

Ken Obech

## Acknowledgments

Facebook Prophet

Plotly

CMU KiltHub Dataset
