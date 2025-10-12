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
file that contains [tables comparing results](../results/Summary.md)

## Step 0: Data Preparation
Since there are resources from two different repo and files, data were pre-processed to be used for our experiments.

The available energy data was from the year 1965, also with time lag = 4, the start year for the data was changed to 1969. There were two preprocessing techniques:

Merging and excluding duplicates

Applying time lags for Auto-Regressive models train

### Code
* [Step 0 Data Preparation](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/00_Data_Preparation.ipynb)

### Results
There are multiple DataFrames created to serve any possible experiment purposes [data folder](https://github.com/pinglainstitute/energy-gdp-emissions/tree/main/data)

* lag_df.csv could not be uploaded due to the size limit of github. However, this can be created by running the code.

## Step 1-1: Data Analysis
Last 9 years of data was split for test and only the train data was analysed for the target variable (CO2).

### Code
* [Step 1-1 Data Analysis](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/01_01_Data_Analysis.ipynb)

### Results

With lag correlation for target on GDP and Energy,

the minimum correlation coefficient is ~ 0.846 for all the features for all three countries.

the maximum std for energy - co2 for the US is 0.43.

The high correlation coefficient and low variability shows the reliability of the features and their consistency.
* ! R2 and Granger causality were tested but should be considered to be added in the paper

### Plots

* [Heatmap for lag correlation on CO2 for 3 countries](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/data/01_01_results/corr_co2_vs_lagged_features_combined.png)

## Step 1-2: Feature Selection
Proportions of resources are included, Herfindahl-Hirschmann Index and its lags are added to the features.

Herfindahl-Hirschmann Index

Since the proportions are in percent values, when the value is close to 10,000, this indicates that the countries are highly dependent on one energy type.

When HHI value gets lower, this implies that the share amount of resources are more diversified.

* "==hhi_detailed==": HHI of total energy for all energy resources. Decrease in the value indicates that the country's attempts to diversify the energy resources.

* "==hhi_fossil==": HHI of total fossil-resource energy. Since there are different intensities on different resources and it helps to distinguish different-resource-heavy nations.


### Code

### Results

### Plots
