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

Due to the benefits of stationarity and normalisation on scale for time series, the actual values (lags) of features were normalised into percent change from the previous year.

The Correlations of the pct_change features (lags) with CO2 were calculated and represented as tables and heatmaps.

The first years of each feature's pct_change lag4 are set to 0 due to the lack of previous data.

### Code

* [Step 1-3 Correlations pct change](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/01_03_Feature_pct_change.ipynb)

### Results

* [Correlations of pct change in production features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/production_correlation.md)

* [Correlations of pct change in consumption features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/consumption_correlation.md)

* [Correlations of pct change in share features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/share_correlation.md)

From the result of share features, nuclear energy share is the most consistent feature in CO2 reduction. US (-0.57, -0.6), China (-0.25, -0.28) except lag4, and India (-0.08, -0.18).


### Plots

* [Heatmaps of pct change in production features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/production_heatmap.png)

* [Heatmaps of pct change in consumption features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/consumption_heatmap.png)

* [Heatmaps of pct change in share features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/share_heatmap.png)

## Step 2-1
Building baseline model with ARIMA

**ARIMA workflow**:
ADF test to check stationarity (p_value < 0.05) -> ACF, PACF testing to determine p, q -> Gridsearch to determine the optimal order (AIC)

-> Auto ARIMA search -> model comparison (Baseline(1, 1, 1), Manual Grid Search, Auto ARIMA (fixed d), Auto ARIMA (free d))

**Forecast workflow**:
train data for each country -> train ARIMA once -> fit the model -> predict each test year individually

### Code
* [Step 2-1 Baseline ARIMA](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/02_01_Baseline_ARIMA.ipynb)

### Results
* [ARIMA summary result](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/02_01_results/arima_method_summary.md)

The Best order for the US was (0, 1, 0) Auto ARIMA with fixing d order

The Best order for China was (0, 2, 0) Auto ARIMA with fixing d order

The Best order for India was (1, 1, 1) Baseline ARIMA

### Plots
* [Forecast on test data](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/02_01_results/arima_optimal_forecasts.png)

## Step 2-2
Building baseline DL models and comparison with baseline ARIMA.

The baseline DL models are LSTM, Bidirectional LSTM, Encoder-Decoder LSTM, CNN.

**The workflow**:

raw data -> pct change normalisation -> combine all countries' pct_change data -> fit one StandardScaler

-> make sequences(5 input windows, 1 output window) -> stack all sequences for each country -> train each model on this data

**Evaluation workflow**:

for each country, use train+test -> pct_change -> scaling with the same StandardScaler we used before -> create sequences

-> extract sequences to predict test data -> inverse scaling -> denormalise -> calculate metrics

**Errors for each single step** were calculated in the middle of the code

The comparison with the baseline ARIMA (Best optimal order for each country) was presented at the end

ARIMA uses original values of the data.

### Code
* [Step 2-2 Baseline DL Models](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/02_02_Baseline_DL_models.ipynb)

### Results
* [Baseline model comparison](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/02_02_results/baseline_model_comparison.md)

The best model for each country is presented as a table in the result link.

### Plots
* [Baseline model plots for the US](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/02_02_results/United_States_baseline_model_comparison.png)

* [Baseline model plots for China](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/02_02_results/China_baseline_model_comparison.png)

* [Baseline model plots for India](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/02_02_results/India_baseline_model_comparison.png)

`## Step 2-3`
`Comparison of ARIMAX (ARIMA with exogenous variables)`

`### Code`
`* [Step 2-3 ARIMAX](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/02_03_ARIMAX.ipynb)`

## Step 3-1
This feature selection step is to identify which features to choose for the multivariate DL models.

Comparison of correlation coefficients: percent change normalised features vs target for 3 countries, 3 countries + G7, G20

### Code
* [Step 3-1 Feature Selections](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/03_01_Feature_Selections.ipynb)

### Results
Best 6 features from the selected 3 countries:

cumulative_luc_co2, cumulative_oil_co2, population, cumulative_co2, share_of_temperature_change_from_ghg, share_global_cumulative_cement_co2

Best 6 features from G7 + selected 3 countries:

cumulative_oil_co2, cumulative_co2, cumulative_cement_co2, cumulative_co2_including_luc, cumulative_gas_co2, cumulative_luc_co2

Best 5 features from G20 countries:

cumulative_oil_co2, cumulative_oil_co2, cumulative_cement_co2, population, cumulative_gas_co2

* [Overall Correlations for 3 Countries](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/03_01_results/overall_3_countries_ranking.md)

* [Overall Correlations for 3 Countries + G7](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/03_01_results/overall_g7_countries_ranking.md)

* [Overall Correlations for G20](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/03_01_results/overall_g20_countries_ranking.md)

## Step 3-2
Building ARIMAX to see the forecasts with other exogenous variables

Initially, variables to use were ['gdp', 'primary_energy_consumption', 'population'] from the feature selection step.

### Code
* [Step 3-2 ARIMAX](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/03_02_ARIMAX.ipynb)

### Result
Before running ARIMAX, stationary test was conducted for each country.

`population` was not stationary for all the countries, due to the monotonic increase in value.

All the additiona variables for India were not stationary with the optimal ARIMA differencing order. It suggests to use ARIMA for India.
