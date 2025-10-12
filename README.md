# Energy, GDP and Carbon Emissions

Project looking at forecasting models incorporating multiple 
related data sets.

### Resources

* [Overleaf Paper Draft](https://www.overleaf.com/project/67a5fa2578743cc4a6c2bd95)
 
* [Our World in Data Energy]( https://github.com/owid/energy-data)

* [Our World in Data CO2](https://github.com/owid/co2-data)

* New IEA report with links to a lot of data [Electricity 2025](https://www.iea.org/reports/electricity-2025)

python version = 3.10.0

required installs = requirements.txt

# Experiments
Our experiments are conducted over multiple stages, you can go
through each of the notebooks. Or go straight to the markdown
file that contains [tables comparing results](../results/Summary.md)

## Step 0: Data Preparation
Since there are resources from two different repo and files, data were pre-processed to be used for our experiments.

The available energy data was from the year 1965, also with time lag = 4, the start year for the data was changed to 1969.

Preprocessing techniques:

* Merging and excluding duplicates

* Applying time lags for Auto-Regressive models train

### Results
There are multiple DataFrames created to serve any possible experiment purposes [data folder]()

* lag_df.csv could not be uploaded due to the size limit of github. However, this can be created by running the code.

### Plots

