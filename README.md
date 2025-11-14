# Energy, GDP and Carbon Emissions for US, China, India

Project looking at forecasting models incorporating multiple 
related data sets.

### Resources

* [Overleaf Paper Draft](https://www.overleaf.com/project/67a5fa2578743cc4a6c2bd95)
 
* [Our World in Data Energy]( https://github.com/owid/energy-data)

* [Our World in Data CO2](https://github.com/owid/co2-data)

* New IEA report with links to a lot of data [Electricity 2025](https://www.iea.org/reports/electricity-2025)

python version = 3.10.19

required libraries to install: [requirements.txt](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/requirements.txt)

The requirements.txt is based on arm64 macos, make sure to change the libraries depending on your environment.

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

## Step 1-2: Herfindhal-Hirschmann Index

When it comes to the energy mix, HHI was considered to train models with its explainability.

Proportions of resources are included, Herfindahl-Hirschmann Index and its lags are added to the features.

This has a range (0, 1). Value close to 1 indicates high level of concentration of one resource/category. Value close to 0 indicates that the resources are diversifed.

* `hhi_detailed`: HHI of total energy for all energy resources. Decrease in the value indicates that the country's attempts to diversify the energy resources.

* `hhi_fossil`: HHI of total fossil-resource energy. Since there are different intensities on different resources and it helps to distinguish different-resource-heavy nations.

### Code

* [Step 1-2 Herfindahl Index](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/01_02_Herfindahl_index.ipynb)

### Results

New dataframe [train_3_hhi_detail_fossil.csv](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/train_3_hhi_detail_fossil.csv) was created to add HHI values and their lags

Correlation results

* [Corr coef CO2 vs features in total](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/hhi_correlation_total.md)

* [Corr coef Co2 vs features for each country](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/hhi_correlation_by_country.md)

The negative correlation coefficients imply though there was a decrease in HHI (diverification in resources), CO2 emission increased. Which means the energy consumption kept increasing along with resource diversification.

In the notebook, additional experiments, targetting on CO2 per capita and Carbon intensity (based on kaya indentity) were tested. However, the results had bias. Also, even if the results were acceptable, since the main target should be CO2, an additional forecast would be required. This will lead to an error propagation

After the results, the decision was made to exclude HHI.

### Plots

* [Energy mix trends (%)](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/energy_mix_trends.png)

* [Heatmap of CO2 vs Energy mix % in total](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/hhi_correlation_energy_prop_total.png)

* [Heatmap of CO2 vs Energy mix % by country](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/hhi_correlation_energy_prop_by_country.png)

 US: There are negative corr coef of coal and gas, positive corr coef of nulcear on CO2, which means US has shifted from coal-> gas but generally shifting from fossil -> nuclear. 

 China & India: These two countries showed similar trend. They have been shfting from coal (their dominant in the past) to other renewables alongside high CO2 emission.

* [Heatmaps of CO2 vs HHI Energy in total](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/hhi_heatmaps_total.png)

* [Heatmaps of CO2 vs HHI Energy by country](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_02_results/hhi_heatmaps_by_country.png)

The negative corr coef along with the increase in CO2 emission imply that population needs to be considered since the increase in HHI would have a possibility of decrease in CO2 per capita.

After experimenting co2_per_capita and co2_intensity as a target in the notebook, HHI has meaningful correlations for each country but HHI for India has a strongly negative corr coeff. (probably due to the economic development) 

**-> Decision is to drop Herfindahl-Hirschmann Index**

## Step 1-3: Correlation Analysis
This step is to identify optimal features for CO2 forecasting models through correlation analysis across different groups.

percent change normalised features (its lags) vs target for Country Groups below

The reason why all the featuers were normalised into pct_change is combining all country data due to the small sample size.

**Method**: 

1. Data Preparation

* `Train-test split`: split from last 9 years for testing

* `Data coverage`: set a threshold of >= 0.8 to filter features (For G20 and All countries, this method was used to filter the countries meet the threshold)

* `Interpolation`: foward fill for missing data which meet the data coverage threshold

* `Normalisation`: all features and the target were normalised with percent change

2. Country Groups

* 3 countries (US, China, India)

* G7 + 3 countries above (EU excluded)

* G20 countries (EU excluded)

* All countries (meet the data coverage threshold)

3. Correlation types

* No Lags: current feature values vs CO2

* With Lags: Mean abolute correlation across features + 4 time lags (t -> t-4)

4. Feature exclusion

Variables containing 'cumulative_', 'temperature_', '_including_luc', 'ghg', 'co2' are excluded due to the circular dependency and causality issues.

5. Variance Inflation Factor (<= 10)

Simple VIF test was conducted (threshold at 10) in order to deal with multicollinearity among the independent variables.

### Code
* [Step 1-3 Correlation Analysis](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/01_03_Correlation_Analysis.ipynb)

### Results

* [Correlation table of pct change for three countries without lags](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/three_summary_no_lags.md)

* [Correlation table of pct change for three countries with lags](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_03_results/three_summary_with_lags.md)

* [**Correlation tables for other categories**](https://github.com/pinglainstitute/energy-gdp-emissions/tree/main/data/01_03_results)

There are variables based on the same resource such as `biofuel_share_energy`, `biofuel_consumption`, `biofuel_cons_per_capita`. Only one of the variables with the highest mean absolute correlation coefficient was considered.

From the result, the variables to consider are `gdp`, `primary_energy_consumption`, `population`, `coal_consumption`, `biofuel_share_energy`, `low_carbon_share_energy`, `energy_per_gdp`, `methane`, `nitrous_oxide`.

After testing variance_inflation_factor, excluding `coal_consumption` and `energy_per_gdp` returns the overall VIF values became more acceptable.

Hence, the finalised variables to consider are: `gdp`, `primary_energy_consumption`, `population`, `biofuel_share_energy`, `low_carbon_share_energy`, `methane`, `nitrous_oxide`

## Step 2-1: Baseline ARIMA Model
For the baseline ARIMA model, raw CO2 emission data were used instead of percent change normalisation due to the violation of normality.

**ARIMA workflow**:
1. Used interpolated training DataFrame with test data from full DataFrame
2. ADF test to check stationarity (p_value < 0.05)
 - US: d = 1, China = 4, India = 2
3. ACF, PACF testing to determine p, q
 - PACF cutoff for all countries at lag 1: AR(1)
 - ACF for all countries showed gradual decay. Showing AR pattern
4. Gridsearch to determine the optimal order (AIC)
 - Search ranges: p = \[0, 2], d = \[0, 2], q = \[0, 2]
5. Auto ARIMA
 - Fixed d: auto-selected d from ADF (For China, added d = 2 as well since 4 is too high)
 - Free d:fully automated selection with AIC
   
**Model Comparison** 
1. (Baseline(1, 1, 1)
2. Manual Grid Search
3. Auto ARIMA (fixed d)
4. Auto ARIMA (free d))

**Forecast workflow**:
train ARIMA once on train data for each country -> fit the model -> predict each test year individually

### Code
* [Step 2-1 Baseline ARIMA](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/02_01_Baseline_ARIMA.ipynb)

### Results
* [ARIMA summary result](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/02_01_results/arima_method_summary.md)

The Best order for the US was (2, 2, 0) Manual Grid Search

The Best order for China was (0, 2, 0) Auto ARIMA with fixing d order

The Best order for India was (1, 1, 1) Baseline ARIMA

### Plots
* [Forecast on test data](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/02_01_results/arima_optimal_forecasts.png)

## Step 2-2: Baseline ARIMAX Model
For the Baseline ARIMAX, raw CO2 emission data with 7 exogenous varialbes from **Step1-3**

Since only `methane` and `nitrous_oxide` were stationary after differencing for all the countries, only auto ARIMAX was conducted for this step.

**Exogenous Variables**
`gdp`, `primary_energy_consumption`, `population`, `biofuel_share_energy`, `low_carbon_share_energy`, `methane`, `nitrous_oxide`

**ARIMAX Workflow**
1. Used interpolated training DataFrame with test data from full DataFrame
2. Stationary test (ADF): though all the variables remained stationary after differencing for the US, the variables China and India did not.
3. Auto ARIMAX: manual ARIMAX was not feasible from the stationary test.
 - information criterion: AIC

**Forecast Workflow**
Train auto ARIMAX once on training data with exogenous variables -> Fit the model -> forecast Multi-step ahead

### Code
* [Step 2-2 Baseline ARIMAX](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/02_02_Baseline_ARIMAX.ipynb)

### Results
* [Auto ARIMAX summary result](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/02_02_results/Bseline_ARIMAX_result_three.md)

Baseline ARIMAX peformed worse than Baseline ARIMA for all three countries

This is possibly due to the non-stationarity of some exogenous variables, however, the key variables such as `gdp` and `primary_energy_consumption` were not stationary after differerncing for India.

### Plots
* [Plot of auto ARIMAX result for three countries](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/02_02_results/auto_ARIMAX_three_forecast.png)

**`!This step is moved to temp`**

Step 2-3: Baseline DL Models

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

## Step 3-3: Multivariate DL models (Should be modified to 3-1)
Building multivariate DL models.

The models are multivariate versions from the baseline models: LSTM, Bi-directional LSTM, ED-LSTM, CNN

`! To add`: Due to its small number of dataset, tuning hyperparameters with validation = 0.1 and its loss of mse was conducted.

And the validation set was included in the training dataset.

**Data prep and train workflow**:

raw data -> split train and test -> pct_change normalisation -> combine all countries' train data -> fit universal StandardScaler

-> create sequences (5 input windows, 1 output window) -> train models with hyperparmeter tuning

**Test and evaluation workflow**:

for each country, combine train + test data (lags) -> calculate pct_change -> scale with the previous Scaler -> create sequences

-> Extract the last 9 sequences -> Model prediction -> Inverse StandardScaler -> Denormalise -> calculate metrics

The selected features from the previous feature selection step:

* Key features = `gdp`, `primary_energy_consumption`, `population`

* Selected features = `oil_production`, `nulcear_consumption`, `wind_consumption`, `biofuel_consumption`, `energy_per_gdp`

### Code
* [Step 3-3 Multivariate DL models](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/03_03_Multivariate_DL_models.ipynb)

### Results
The best DL model based on RMSE for:

United States - Encoder-Decoder LSTM (rmse = , mase = )

China - LSTM (rmse = , mase = )

India - CNN (rmse = , mase = )

* [RMSE and MASE tables](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/03_03_results/Multi_DL_summary.md)

### Plots
