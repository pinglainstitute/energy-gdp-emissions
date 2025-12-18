# Summary of Step 4

This summary shows the performance metrics of four deep learning models (sRNN, LSTM, Bi-LSTM, ED-LSTM, CNN) trained on different country groups to predict CO2 emissions for three target countries: The United States, China, and India

Step 4 is the modified version that hyperparameter tuning was done on validation set (0.1 of the total training dataset) of three countries (United States, China, India).

### Performance Summary: RMSE

| Training Dataset  | Model | Avg (3 Countries) |   Avg (All in Train)  | United States | China | India | 
|:------------------|:------|------------------:|----------------------:|--------------:|------:|------:|
| G7 + China + India| sRNN  |           253.367 |                       |               |       |       |
|                   | LSTM  |           246.461 |                       |       257.344 |296.170|130.133|
|                   |Bi-LSTM|           239.784 |                       |       222.043 |407.204|128.409|
|                   |ED-LSTM|           626.831 |                       |       243.517 |335.206|134.860|
|                   | CNN   |           214.010 |                       |       235.652 |281.326|135.819|
| G20               | sRNN  |           243.283 |                       |               |       |       |
|                   | LSTM  |           224.296 |                       |       210.954 |267.572|115.598|
|                   |Bi-LSTM|           218.052 |                       |       242.950 |294.988|124.730|
|                   |ED-LSTM|           235.620 |                       |       239.030 |312.625|123.970|
|                   | CNN   |           228.347 |                       |       267.378 |310.956|138.035|
| All Countries     | sRNN  |           304.216 |                       |               |       |       |
|                   | LSTM  |           240.149 |                       |       241.032 |235.446|152.864|
|                   |Bi-LSTM|           224.937 |                       |       242.275 |215.788|159.650|
|                   |ED-LSTM|           249.437 |                       |       256.413 |234.900|132.492|
|                   | CNN   |           254.786 |                       |       287.247 |243.797|129.590|

---

### Performance Summary: MASE

| Training Dataset  | Model | Avg (3 Countries) |   Avg (All in Train)  | United States | China | India |
| G7 + China + India| sRNN  |             1.115 |                       |               |       |       |
|                   | LSTM  |             0.950 |                       |         1.009 | 1.012 | 0.737 |
|                   |Bi-LSTM|             0.949 |                       |         0.862 | 1.359 | 0.695 |
|                   |ED-LSTM|             2.471 |                       |         0.971 | 1.149 | 0.770 |
|                   | CNN   |             0.920 |                       |         1.054 | 0.886 | 0.783 |
| G20               | sRNN  |             1.044 |                       |               |       |       |
|                   | LSTM  |             0.894 |                       |         0.809 | 0.908 | 0.626 |
|                   |Bi-LSTM|             0.874 |                       |         0.955 | 0.962 | 0.686 |
|                   |ED-LSTM|             0.919 |                       |         0.941 | 1.026 | 0.679 |
|                   | CNN   |             0.859 |                       |         1.172 | 0.994 | 0.725 |
| All Countries     | sRNN  |             1.235 |                       |               |       |       |
|                   | LSTM  |             0.964 |                       |         0.933 | 0.810 | 1.000 |
|                   |Bi-LSTM|             0.924 |                       |         0.956 | 0.656 | 1.014 |
|                   |ED-LSTM|             0.989 |                       |         1.019 | 0.841 | 0.824 |
|                   | CNN   |             1.009 |                       |         1.043 | 0.874 | 0.817 |

---

