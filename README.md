# Climate-Change-Forecasting-Project
This project explores and forecasts climate change patterns over 60 years (1960–2020) using temperature and precipitation data from five major U.S. cities: Boston, Los Angeles, New York, Washington, D.C., and Chicago. It uses Python-based data analysis, visualization, and time series forecasting techniques to extract insights and build a 5-year forecast for average temperature trends.

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
This project aims to detect trends, visualize seasonal patterns, and forecast future temperatures using Facebook Prophet.

## Setup and Requirements

To get started:

**Libraries used**

**pandas** for data manipulation

**seaborn** & **matplotlib** for visualization

**plotly** for interactive charts

**prophet** for time series forecasting

## Installation

pip install pandas seaborn matplotlib plotly prophet

## Steps and Tasks

1. **Importing and Preprocessing**

Import libraries

2. **Load the dataset into a DataFrame**

3. **Convert Date to datetime**

4. **Extract unique city names for iteration.**

5. **Trend Visualization (Line Plot)**

For each city:

Group by year

Plot average, max and min temperature trends

6. **Decade-wise Heatmaps**

Create a Decade column

Group by Decade and Month

7. **Use seaborn.heatmap() to visualize seasonal trends per city**

8. **Yearly Precipitation Trend**

Group by City and Year, calculate the average precipitation.

Plot precipitation trends for each city

Moving Average Trends

Calculate the rolling average of tavg (30-day window)

Plot original vs smoothed temperature lines using plotly

9. **Forecasting Using Prophet**
For each city:

Instantiate the Prophet model

Fit historical data

Generate future dates (5 years)

Forecast and plot predictions

Plot forecast components (trend, seasonality)

## Insights

Average temperatures show an increasing trend across decades.

Precipitation varies across cities but generally remains within a range.

Seasonal variation is visible, with predictable summer peaks and winter lows.

Prophet forecasts suggest a continued warming trend.

## License

This project is released under the MIT License. The dataset is credited to Carnegie Mellon University's KiltHub.

## Author

Ken Obech

## Acknowledgments

Facebook Prophet

Plotly

CMU KiltHub Dataset
