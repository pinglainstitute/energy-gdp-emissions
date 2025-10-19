# Energy, GDP and Carbon Emissions for US, China, India

Project looking at forecasting models incorporating multiple 
related data sets.

### Resources

* [Overleaf Paper Draft](https://www.overleaf.com/project/67a5fa2578743cc4a6c2bd95)
 
* [Our World in Data Energy]( https://github.com/owid/energy-data)

* [Our World in Data CO2](https://github.com/owid/co2-data)

* New IEA report with links to a lot of data [Electricity 2025](https://www.iea.org/reports/electricity-2025)

python version = 3.10.0

required libraries to install = [requirements.txt](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/requirements.txt)

# Experiments
Our experiments are conducted over multiple stages, you can go
through each of the notebooks. Or go straight to the markdown
file that contains [result not added yet](example)

## Step 0: Data Preparation
Since there are resources from two different repo and files, data were pre-processed to be used for our experiments.

The available energy data was from the year 1965, also with time lag = 4, the start year for the data was changed to 1969. There were two preprocessing techniques:

Merging and excluding duplicates

Applying time lags for Auto-Regressive models train

### Code
* [Step 0 Data Preparation](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/00_Data_Preparation.ipynb)

### Results
There are multiple DataFrames created to serve any possible experiment purposes [data folder](https://github.com/pinglainstitute/energy-gdp-emissions/tree/main/data)

* `lag_df.csv` could not be uploaded due to the size limit of github. However, this can be created by running the code.

## Step 1-1: Data Analysis
Last 9 years of data was split for test and only the train data was analysed for the target variable (CO2).

### Code
* [Step 1-1 Data Analysis](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/01_01_Data_Analysis.ipynb)

### Results

* [Corr Coef table for CO2 vs GDP and Energy](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_01_results/lag_corr_table_co2_vs_features.md)

With lag correlation for target on GDP and Energy,

the minimum correlation coefficient is ~ 0.846 for all the features for all three countries.

the maximum std for energy - co2 for the US is 0.43.

The high correlation coefficient and low variability shows the reliability of the features and their consistency.
* ! `R2` and `Granger causality` were tested but should be considered to be added in the paper

### Plots

* [Heatmap for lag correlation on CO2 for 3 countries](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_01_results/corr_co2_vs_lagged_features_combined.png)

## Step 1-2: Feature Selection
Proportions of resources are included, Herfindahl-Hirschmann Index and its lags are added to the features.

Herfindahl-Hirschmann Index

This has a range (0, 1). Value close to 1 indicates high level of concentration of one resource/category. Value close to 0 indicates that the resources are diversifed.

* `hhi_detailed`: HHI of total energy for all energy resources. Decrease in the value indicates that the country's attempts to diversify the energy resources.

* `hhi_fossil`: HHI of total fossil-resource energy. Since there are different intensities on different resources and it helps to distinguish different-resource-heavy nations.

### Code

* [Step 1-2 Feature Selection](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/01_02_Feature_Selection.ipynb)

### Results

New dataframe [train_3_hhi_detail_fossil.csv](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/train_3_hhi_detail_fossil.csv) was created to add HHI values and their lags

Correlation results

* [Corr coef CO2 vs features in total](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/hhi_correlation_total.md)

* [Corr coef Co2 vs features for each country](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/hhi_correlation_by_country.md)

The negative correlation coefficients imply though there was a decrease in HHI (diverification in resources), CO2 emission increased. Which means the energy consumption kept increasing along with resource diversification.

In the notebook, additional experiments, targetting on CO2 per capita and Carbon intensity (based on kaya indentity) were tested. However, the results had bias. Also, even if the results were acceptable, since the main target should be CO2, an additional forecast would be required. This will lead to an error propagation

### Plots

* [Energy mix trends (%)](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/energy_mix_trends.png)

* [Heatmap of CO2 vs Energy mix % in total](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/hhi_correlation_energy_prop_total.png)

* [Heatmap of CO2 vs Energy mix % by country](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/hhi_correlation_energy_prop_by_country.png)

 US: There are negative corr coef of coal and gas, positive corr coef of nulcear on CO2, which means US has shifted from coal-> gas but generally shifting from fossil -> nuclear. 

 China & India: These two countries showed similar trend. They have been shfting from coal (their dominant in the past) to other renewables alongside high CO2 emission.

* [Heatmaps of CO2 vs HHI Energy in total](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/hhi_heatmaps_total.png)

* [Heatmaps of CO2 vs HHI Energy by country](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/hhi_heatmaps_by_country.png)

The negative corr coef along with the increase in CO2 emission imply that population needs to be considered since the increase in HHI would have a possibility of decrease in CO2 per capita.

! After experimenting co2_per_capita and co2_intensity as a target in the notebook, HHI has meaningful correlations for each country but HHI for India has a strongly negative corr coeff. (probably due to the economic development)

## Step 1-3: Feature Normalisation and its Correlations

Due to the merits on Stationarity and Normalisation on scale, the actual values (lags) of features were normalised into percent change from the previous year.

The Correlations of the pct_change features (lags) with CO2 were calculated and represented as tables and heatmaps.

The first years of each feature's pct_change lag4 are set to 0 due to the lack of previous data.

### Code

* [Step 1-3 Correlations pct change](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/01_03_Feature_pct_change.ipynb)

### Results

* [Correlations of pct change in production features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/production_correlation.md)

* [Correlations of pct change in consumption features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/consumption_correlation.md)

* [Correlations of pct change in share features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/share_correlation.md)

### Plots

* [Heatmaps of pct change in production features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/production_heatmap.png)

* [Heatmaps of pct change in consumption features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/consumption_heatmap.png)

* [Heatmaps of pct change in share features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/share_heatmap.png)

## Step 2
Experiments run on ARIMA and ARIMAX models.

ARIMA methods were tested with Auto ARIMA (tested on fixing or freeing differencing order), Manual ARIMA, Baseline ARIMA (1, 1, 1).

### Code
* [Step 2-1 Autoregressive](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/02_01_AutoRegressive.ipynb)

### Results
* [ARIMA summary result](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/02_01_results/arima_method_summary.md)

The Best order for the US was (0, 1, 0) Auto ARIMA with fixing d order

The Best order for China was (0, 2, 0) Auto ARIMA with fixing d order

The Best order for India was (1, 1, 1) Baseline ARIMA

### Plots
* [Forecast on test data](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/02_01_results/arima_optimal_forecasts.png)


