# This folder contains dropped code which were tested in advance

## Step 2-3: Baseline DL Models

Building baseline DL models and comparison with baseline ARIMA.

The baseline DL models are LSTM, Bidirectional LSTM, Encoder-Decoder LSTM, CNN.

The workflow:

raw data -> pct change normalisation -> combine all countries' pct_change data -> fit one StandardScaler

-> make sequences(5 input windows, 1 output window) -> stack all sequences for each country -> train each model on this data

Evaluation workflow:

for each country, use train+test -> pct_change -> scaling with the same StandardScaler we used before -> create sequences

-> extract sequences to predict test data -> inverse scaling -> denormalise -> calculate metrics

Errors for each single step were calculated in the middle of the code

The comparison with the baseline ARIMA (Best optimal order for each country) was presented at the end

ARIMA uses original values of the data.
