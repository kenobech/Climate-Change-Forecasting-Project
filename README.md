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

**pandas** for data manipulation

**seaborn** & **matplotlib** for visualization

**plotly** for interactive charts

**prophet** for time series forecasting

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
