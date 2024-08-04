
# Covid Dataset Analysis

## Overview

This repository contains an analysis of Covid-19 data from Turkey, Germany, and Afghanistan. The analysis includes various statistical tests and visualizations to examine trends, distributions, and correlations within the dataset.

## Dataset

The dataset used for this analysis is from Kaggle and can be found [here](https://www.kaggle.com/datasets/niketchauhan/covid-19-time-series-data). 

### Columns

- `Date`: Date of the observation
- `Country`: Country name
- `Confirmed`: Number of confirmed Covid-19 cases
- `Deaths`: Number of deaths due to Covid-19
- `Recovered`: Number of recovered Covid-19 patients
- `Active`: Number of active Covid-19 cases
- `Population`: Population of the country

## Requirements

To run the analysis, you need the following Python libraries:
- pandas
- numpy
- scipy
- statsmodels
- matplotlib
- seaborn

Install the dependencies using pip:
```bash
pip install pandas numpy scipy statsmodels matplotlib seaborn
```
### Data Sources

- **Turkey Confirmed Cases**: Time series data for confirmed Covid-19 cases in Turkey.
- **Germany Deaths**: Time series data for deaths due to Covid-19 in Germany.
- **Afghanistan Deaths**: Time series data for deaths due to Covid-19 in Afghanistan.




## Visualizations

1. **Time Series Plots**
   - Plots for confirmed cases and deaths for Turkey and Germany.
   - Trends over time for Turkey's confirmed cases and Germany's death rates.
![download](https://github.com/user-attachments/assets/703deb09-ddb1-4f8a-9103-d842703bd75b)
![download](https://github.com/user-attachments/assets/edb996cf-127e-45ca-a7bf-26db01c5c563)
   
2. **Top 10 Countries by Deaths**
   - Bar chart showing the top 10 countries with the highest number of deaths.
![download](https://github.com/user-attachments/assets/8e3a2274-8df5-4341-96e6-c990694d9a33)

3. **Heatmaps**
   - Heatmaps visualizing the correlation between confirmed cases, deaths, and recoveries.
![download](https://github.com/user-attachments/assets/998ff7a5-d88c-4b11-a5ea-7a3e45ace584)

4. **Time Series of Confirmed Cases and Death Rates**
   - Time series plots showing Turkey's confirmed cases and Germany's death rates.
![download](https://github.com/user-attachments/assets/b62d75ff-61a2-4f4d-97f2-19c73a377c27)
![download](https://github.com/user-attachments/assets/6b9851b0-05ec-4b15-b8ab-cdd822acccb8)

## Statistical Tests

### Normality Tests

The following tests were used to determine if the data follows a normal distribution:

- **Shapiro-Wilk Test**
  - Confirmed in Turkey: 
    - Statistic: 0.90197
    - p-value: 2.9998e-12
  - Recovered in Germany: 
    - Statistic: 0.87371
    - p-value: 3.9712e-14
  - Deaths in Afghanistan: 
    - Statistic: 0.78331
    - p-value: 1.2502e-18

- **D'Agostino's K^2 Test**
  - Confirmed in Turkey: 
    - Statistic: 383.80718
    - p-value: 1.2502e-18
  - Deaths in China: 
    - Statistic: 9833.40907
    - p-value: 1.2502e-18
  - Recovered in Afghanistan: 
    - Statistic: 2231.08919
    - p-value: 1.2502e-18

- **Anderson-Darling Test**
  - Confirmed Cases:
    - At 15%: 22932.159 > 0.576 (Reject H0 - Not normal distribution)
    - At 10%: 22932.159 > 0.656 (Reject H0 - Not normal distribution)
    - At 5%: 22932.159 > 0.787 (Reject H0 - Not normal distribution)
    - At 2.5%: 22932.159 > 0.918 (Reject H0 - Not normal distribution)
    - At 1%: 22932.159 > 1.092 (Reject H0 - Not normal distribution)

Since most of the Confirmed, Deaths, and Recovered columns are not normally distributed, non-parametric tests were used.

### Non-Parametric Tests

- **Mann-Whitney U Test**
  - Confirmed vs Recovered: p-value = 7.0891e-265
  - Turkey vs Afghanistan (Confirmed): p-value = 2.9969e-39
  - Recovered vs Deaths: p-value = 0.0

- **Wilcoxon Signed-Rank Test**
  - Turkey vs Afghanistan (Confirmed): p-value = 2.9969e-39

- **Kruskal-Wallis H Test**
  - Result: p-value = NaN

- **Friedman Test**
  - Deaths of Turkey, Germany, and Afghanistan: p-value = 9.9389e-97

### Correlation Tests

- **Pearson Correlation**
  - Deaths vs Confirmed in Turkey:
    - Coefficient: 0.99667
    - p-value: 8.3457e-294

- **Spearman Correlation**
  - Deaths vs Confirmed in Turkey:
    - Coefficient: 0.99875
    - p-value: 0.0

### Time Series Analysis

- **Augmented Dickey-Fuller (ADF) Test**
  - Turkey Confirmed:
    - ADF Statistic: 0.1334
    - p-value: 0.9683
    - Critical Values: {'1%': -3.4559, '5%': -2.8728, '10%': -2.5728}
  - Germany Deaths:
    - ADF Statistic: -1.5973
    - p-value: 0.4849
    - Critical Values: {'1%': -3.4565, '5%': -2.8730, '10%': -2.5729}

- **KPSS Test**
  - Turkey Confirmed:
    - KPSS Statistic: 2.5097
    - p-value: 0.01
    - Critical Values: {'10%': 0.347, '5%': 0.463, '2.5%': 0.574, '1%': 0.739}
  - Germany Deaths:
    - KPSS Statistic: 2.1885
    - p-value: 0.01
    - Critical Values: {'10%': 0.347, '5%': 0.463, '2.5%': 0.574, '1%': 0.739}
    - 
## Conclusions

1. **Normality Tests**:
   - All tested series (Confirmed, Deaths, and Recovered) significantly deviate from normal distribution as indicated by the Shapiro-Wilk, D'Agostino's K^2, and Anderson-Darling tests.

2. **Non-Parametric Tests**:
   - Mann-Whitney U Tests reveal significant differences between various groups.
   - Wilcoxon Signed-Rank Test indicates significant differences between Turkey and Afghanistan's confirmed cases.
   - Friedman Test shows strong evidence of differences in death rates across Turkey, Germany, and Afghanistan.
   - The Kruskal-Wallis H Test could not be computed due to data issues.

3. **Correlation Tests**:
   - Pearson and Spearman correlation coefficients suggest a very strong positive correlation between deaths and confirmed cases in Turkey, indicating that as the number of confirmed cases rises, the number of deaths tends to rise as well.

4. **Time Series Analysis**:
   - ADF and KPSS tests for stationarity indicate that the time series data for Turkey's confirmed cases and Germany's deaths are not stationary, which may require further differencing or transformation to model effectively.



