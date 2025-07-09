# Energy, GDP and Carbon Emissions

Project looking at forecasting models incorporating multiple 
related data sets.


### Resources

* [Overleaf Paper Draft](https://www.overleaf.com/project/67a5fa2578743cc4a6c2bd95)
 
* [Our World in Data Energy]( https://github.com/owid/energy-data)

* New IEA report with links to a lot of data [Electricity 2025](https://www.iea.org/reports/electricity-2025)

# Added by Julian
python version = 3.10.0

required installs = req3.txt

# Experiments
Our experiments are conducted over multiple stages, you can go
through each of the notebooks. Or go straight to the markdown
file that contains [tables comparing results](../results/Summary.md)

## Step 0: Data Preparation
Make some notes about anything specific
* [Preparing data](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/00_Prepare_data.ipynb)

### Results
* [Analysis of all features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/00_results/feature_g20_analysis.md)
* [Analysis of all features from year 1965](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/00_results/feature_g20_start_year_analysis.md)

## Step 1: Initial Autoregression Models
Describe your baseline autoregressions models, i.e. input window size
forecast window size etc.
* [Autoregressive model](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/01_Autoregressive.ipynb)
### Results
* [Analysis of Autoregressive models on targets](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/01_results/ar_summay.csv)

### Example plots of Autoregressive model results
* [United States on co2](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/01_plots/United%20States_co2_comparison.png)
* [China on co2](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/01_plots/China_co2_comparison.png)
* [Germany on co2](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/01_plots/Germany_co2_comparison.png)

* [United States on gdp](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/01_plots/United%20States_gdp_comparison.png)
* [China on gdp](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/01_plots/China_gdp_comparison.png)
* [Australia on gdp](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/01_plots/Australia_gdp_comparison.png)

* [United States on energy](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/01_plots/United%20States_primary_energy_consumption_comparison.png)
* [China on energy](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/01_plots/China_primary_energy_consumption_comparison.png)
* [South Korea on energy](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/01_plots/South%20Korea_primary_energy_consumption_comparison.png)

## Step 2: Multivariate Models
### Step 2-1: Statistical Analysis
* [Statistical Analysis](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/02_01_Stats_Analysis.ipynb)
### Results
* [Plot for correlations](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_plots/01_stats_analysis/comparison_avg_abs_correlation.png)
* [Plot for granger causality](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_plots/01_stats_analysis/comparison_granger_significance_rate.png)
* [Plot for mutual information](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_plots/01_stats_analysis/comparison_avg_mutual_info.png)

### Step 2-2: Feature Screen
* [Feature Screen](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/02_02_Feature_Screening.ipynb)
### Results
* [Results after screen](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_results/screen_summary.csv)
### Plots
* [Summary plot](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_plots/02_feature_screen/screening_summary.png)
* [Feature heatmap](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_plots/02_feature_screen/screen_correlation_matrix.png)

### Step 2-3: Univariate Model-Based Selection

## Step 3: Multivariate Models with Exogenous Fetaures
 
Describe

* [link_to_notebook_or_script](03_Multivariate_Models.ipynb)


## Step 4: Recursive Framework for Longer Predictions


* [link_to_notebook_or_script](04_Recursive.ipynb)



## Step 5: Evaluation of Recursive Predictions


* [link_to_notebook_or_script](05_Evaluation.ipynb)






