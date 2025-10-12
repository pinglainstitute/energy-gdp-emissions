# Note: This repo contains the legacy files for the CO2 Project. These experiments will not be used for the publication.

# Energy, GDP and Carbon Emissions

Project looking at forecasting models incorporating multiple 
related data sets.

### Resources

* [Overleaf Paper Draft](https://www.overleaf.com/project/67a5fa2578743cc4a6c2bd95)
 
* [Our World in Data Energy]( https://github.com/owid/energy-data)

* New IEA report with links to a lot of data [Electricity 2025](https://www.iea.org/reports/electricity-2025)

python version = 3.10.0

required installs = req3.txt

# Experiments
Our experiments are conducted over multiple stages, you can go
through each of the notebooks. Or go straight to the markdown
file that contains [tables comparing results](../results/Summary.md)

## Step 0: Data Preparation
Since CO2 and Energy data came from different raw data, they got merged and created time lagged (t-4) dataframe.

Tailored data with the year 1965 based on the reasonable data coverage for all features.

* [00_Preparing data](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/00_Prepare_data.ipynb)

### Results
* [Analysis of all features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/00_results/feature_g20_analysis.md)
* [Analysis of all features from year 1965](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/00_results/feature_g20_start_year_analysis.md)

## Step 1: Initial Autoregression Models
Baseline autoregressive models (ARIMA, VAR(with its lags), LSTM, Bidirectional LSTM, Encoder-Decoder LSTM, CNN) were used to compare the performance on the data from year 1965.

* [01_Autoregressive model](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/01_Autoregressive.ipynb)

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

## Step 2: Feature Engineering
### Step 2-1: Statistical Analysis

Since the data contains 198 features, feature selection is needed

Average Absolute Correlation with the features and their lags, Granger Causality, and Mutual Information for each target were tested.

* [02_01_Statistical Analysis](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/02_01_Stats_Analysis.ipynb)
  
### Results

These plots are the top 20 rankings on the scores for each statistical analysis.

* [Plot for correlations](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_plots/01_stats_analysis/comparison_avg_abs_correlation.png)
* [Plot for granger causality](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_plots/01_stats_analysis/comparison_granger_significance_rate.png)
* [Plot for mutual information](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_plots/01_stats_analysis/comparison_avg_mutual_info.png)

### Step 2-2: Feature Screen

Domain features were selected due to its theoretical importance.

Feature-Feature correlation was applied to remove highly correlated features.

OLS Regression was used to identify each feature's significance for each target and to remove less important features (threshold at 0.5).

VIF was used to check any multicollinearity.

* [02_02_Feature Screen](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/02_02_Feature_Screening.ipynb)
  
### Results

After filtering out the less important or highly correlated featrues, the summary and the diagonal heatmap shows the correlations of the features survived.

* [Results after screen](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_results/screen_summary.csv)

### Plots

* [Summary plot](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_plots/02_feature_screen/screening_summary.png)
* [Feature heatmap](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_plots/02_feature_screen/screen_correlation_matrix.png)

### Step 2-3: Univariate Model-Based Selection

Those survived features from the Step 2-2 were tested with univariate models (ARIMA and ML models described earlier).

* [02_03_Univariate Model-based comparison](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/02_03_Uni_Model_Selection.ipynb)

### Results

Combined the rankings of the performance of those models and the ranking of the average results were shown to identify the overall ranking of features.

6 features were selected since the data for each country contain 39 samples. (The data has values for each year and the starting year was trimmed to 1965).

* [Result Summary](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_results/uni_model_summary.csv)
* [Filtered Overall Ranking for Features](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_results/overall_feature_ranking.csv)
  
### Plots

These are the plots of predictions of models for the example countries.

* [Australia Fossil Fuel Consumption - CO2](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_plots/03_univariate_models/uni_Australia_fossil_fuel_consumption_to_co2.png)
* [China Electricity Generation - GDP](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_plots/03_univariate_models/uni_China_electricity_generation_to_gdp.png)
* [United States Population - Energy](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/02_plots/03_univariate_models/uni_United%20States_population_to_primary_energy_consumption.png)

## Step 3: Multivariate Models with Exogenous Fetaures
 
With the selected 6 features from the Step 2, simple multivariate models (LSTM, Bidirectional LSTM, Encoder-Decoder LSTM, CNN) were tested.

These multivariate models feed in 5 window size (its time lag) and predict 1.

* [03_Multivariate Models](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/03_Multi_Model.ipynb)

### Results

The performance was tested with RMSE and MASE.

Best performing model for CO2 was CNN, for GDP was Encoder-Decoder LSTM, and for Energy was Encoder-Decoder LSTM.

* [Analysis of four different DeepLearning models for three targets](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/03_results/multivariate_summary.csv)
  
### Plots

These are the plots of example countries.

* [US_co2](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/03_plots/multivariate_models/multi_United%20States_co2_all_models.png)
* [China_gdp](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/03_plots/multivariate_models/multi_China_gdp_all_models.png)
* [Australia_energy](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/03_plots/multivariate_models/multi_Australia_primary_energy_consumption_all_models.png)

## Step 4: Leaving-One-Country-Out model and Recursive Strategy

### Step 4-1: LOCO vs Single

Due to the lack of data on each country, some strategies were tested.

Percentage change normalisation was applied for all model testing.

- LOCO Model

This LOCO model is training the ML model with either developed or developing countries from G20 (Except EU) but kept out one country's data and make predictions for the excluded country's target.

These LOCO model was trained with its target value (for 18 countries, except 1 country to leave out).

This LOCO model was compared with the last 9 years of the Simple ML model which was trained with its own single country.

All the models feed in 5 window size (its time lags) and predict 3 stpes each iteration.

- The Recursive Strategy

With this strategy, the model feeds in 5 window size for each iteration but the feed-in values are changed in order to satisfy the recursive strategy.

Iter 0: It takes last 5 train values (train[:5]) -> predict 3 windows (predict[:3])

Iter 1: It takes last 2 train values + predicted 3 values (train[:2] + predict[:3]) -> predict 3 windows (predict[3:6])

Iter 2: It takes last 5 predict values (predict[1:6]) -> predict 3 windows (predict[6:9])

* [04_01_LOCO_vs_Single](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/04_01_Loco_Single_dev.ipynb)

### Results

The non-recursive LOCO model on developed countries was performing better on more than a half of those countries.

* [full_comparison_result](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/04_results/final/final_summary_table.csv)

Due to its possibility of better performance than the simple model trained with its own country's data, there were some experiments proceeded.

### Step 4-2: LOCO vs Single one target lags

The LOCO model was trained with its own target values and their lags (for 18 countries, 1 country is to leave out)

* [04_02_LOCO_vs_Single_one_target](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/04_02_Loco_Single_1tar_norm%20copy.ipynb)

### Results

* [One_target_results](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/04_results/1target/1target_summary_table.csv)

### Step 4-3: LOCO vs Single all target lags

The LOCO model was trained with all three target values and their lags (for 18 countries, 1 country is to leave out)

* [04_03_LOCO_vs_Single_all_target](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/04_03_Loco_Single_alltar_norm%20copy.ipynb)

### Results

* [All_target_results](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/04_results/alltarget/final_summary_table.csv)

### Insight

Generally, the performance on LOCO models for developed countries with all target lags performed better than Single Country Model but their variances were bigger. This was not applicable for Energy dataset.

### Step 4-4: LOCO vs Single Breakdown

When it comes to the performance of models predicting 3 windows, calculating the average rmse and mase of 3 predictions were used on previous steps.

This step is to breakdown these calculations of average and identify the time series trend on which occasion performs well or poorly.

This was tested only under a few conditions: developed countries, lstm and bilstm, and co2.

* [04_04_LOCO_vs_Single_Breakdown](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/04_04_Loco_Single_breakdown%20copy.ipynb)

### Results

Since there were some countries (e.g. United States) have values oscillate, categorising the countries into two groups would not be the best option for the model to forecast.

* [Breakdown_results](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/04_results/breakdown/developed/model_performance_summary.csv)

### Step 5: Similarity and Clustering

Correlation coefficients on target-to-target and Hierarchical clutsering were used to identify better groups to explain to the model.

* [05_01_Similarity](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/05_01_Country_Correlation.ipynb)
* [05_02_Clutering](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/05_02_Country_Clustering_LOCO.ipynb)

### Results

The similarity on target-to-target is shown with the heatmap.

With the Elbow curve method, the best clustering number was 4.

Hierarchical Clustering was shown with dendrogram and heatmap for each target.

* [CO2_Similarity_result](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_01_country_correlation/co2_correlations.csv)
* [GDP_Similarity_result](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_01_country_correlation/gdp_correlations.csv)
* [Energy_Similarity_result](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_01_country_correlation/primary_energy_consumption_correlations.csv)

### Plots

* [CO2_heatmap](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_01_country_correlation/co2_correlation_heatmap.png)
* [GDP_heatmap](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_01_country_correlation/gdp_correlation_heatmap.png)
* [Energy_heatmap](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_01_country_correlation/primary_energy_consumption_correlation_heatmap.png)

* [CO2_Elbow](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_02_clustering/co2_elbow_analysis.png)
* [GDP_Elbow](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_02_clustering/gdp_elbow_analysis.png)
* [Energy_Elbow](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_02_clustering/primary_energy_consumption_elbow_analysis.png)

* [CO2_Dendrogram](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_02_clustering/co2_dendrogram.png)
* [GDP_Dendrogram](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_02_clustering/gdp_dendrogram.png)
* [Energy_Dendrogram](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_02_clustering/primary_energy_consumption_dendrogram.png)

* [CO2_Heatmap](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_02_clustering/co2_clustered_heatmap.png)
* [GDP_Heatmap](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_02_clustering/gdp_clustered_heatmap.png)
* [Energy_Heatmap](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/05_results/05_02_clustering/primary_energy_consumption_clustered_heatmap.png)

Since Russia contains the values from the Soviet Union, Russia was the only group has only its own country.

Since some of the current developed countries such as South Korea were not developed countries in the earlier years, they were clutsered with other developed countries.

----------------------

## Legacy experiment

* [04_01_Recursive Deep Learning Framework](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/code/04_Recursive.ipynb)

### Plots

* [United States-co2 comparion](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/04_plots/United%20States_co2_preds_actual.png)
* [China - gdp comparison](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/04_plots/China_gdp_preds_actual.png)
* [Australia - energy comparison](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/04_plots/Australia_primary_energy_consumption_preds_actual.png)

### Plots for the limitation (error propagation)

* [United States-co2](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/04_plots/United%20States_co2_expriments.png)
* [China-gdp](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/04_plots/China_gdp_expriments.png)
* [Australia-energy](https://github.com/pinglainstitute/energy-gdp-emissions/blob/main/results/04_plots/Australia_primary_energy_consumption_expriments.png)

## Step 5: Evaluation of Recursive Predictions


* [link_to_notebook_or_script](05_Evaluation.ipynb)






