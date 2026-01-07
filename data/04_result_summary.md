# Summary of Step 4

This summary shows the performance metrics of four deep learning models (sRNN, LSTM, Bi-LSTM, ED-LSTM, CNN) trained on different country groups to predict CO2 emissions for three target countries: The United States, China, and India

Step 4 is the modified version that hyperparameter tuning was done on validation set (0.1 of the total training dataset) of three countries (United States, China, India).

### Performance Summary: RMSE

| Training Dataset  | Model | Avg (3 Countries) |   Avg (All in Train)  | United States | China | India | 
|:------------------|:------|------------------:|----------------------:|--------------:|------:|------:|
| G7 + China + India| sRNN  |           253.367 |               109.712 |       274.856 |349.245|136.000|
|                   | LSTM  |           246.461 |                99.456 |       250.837 |355.867|132.680|
|                   |Bi-LSTM|           239.784 |                97.124 |       256.231 |332.439|130.682|
|                   |ED-LSTM|           626.831 |               234.546 |       180.317 |1542.16|158.019|
|                   | CNN   |           214.010 |                95.911 |       257.051 |235.38|149.599|
| G20               | sRNN  |           243.283 |                63.826 |       284.640 |300.447|144.762|
|                   | LSTM  |           224.296 |                57.520 |       240.619 |308.417|123.851|
|                   |Bi-LSTM|           218.052 |                56.986 |       247.588 |279.417|127.153|
|                   |ED-LSTM|           235.620 |                59.184 |       256.617 |323.752|126.491|
|                   | CNN   |           228.347 |                58.948 |       258.872 |309.631|116.537|
| All Countries     | sRNN  |           304.216 |                       |               |       |       |
|                   | LSTM  |           240.149 |                       |       241.032 |235.446|152.864|
|                   |Bi-LSTM|           224.937 |                       |       242.275 |215.788|159.650|
|                   |ED-LSTM|           249.437 |                       |       256.413 |234.900|132.492|
|                   | CNN   |           254.786 |                       |       287.247 |243.797|129.590|

---

### Performance Summary: MASE

| Training Dataset  | Model | Avg (3 Countries) |   Avg (All in Train)  | United States | China | India |
|:------------------|:------|------------------:|----------------------:|--------------:|------:|------:|
| G7 + China + India| sRNN  |             1.115 |                 1.339 |         1.318 | 1.176 | 0.851 |
|                   | LSTM  |             0.950 |                 1.018 |         0.976 | 1.122 | 0.753 |
|                   |Bi-LSTM|             0.949 |                 1.002 |         1.034 | 1.074 | 0.740 |
|                   |ED-LSTM|             2.471 |                 1.773 |         0.661 | 5.892 | 0.861 |
|                   | CNN   |             0.920 |                 1.325 |         1.165 | 0.734 | 0.863 |
| G20               | sRNN  |             1.044 |                 1.131 |         1.174 | 1.088 | 0.871 |
|                   | LSTM  |             0.894 |                 0.995 |         0.976 | 1.026 | 0.681 |
|                   |Bi-LSTM|             0.874 |                 1.043 |         0.989 | 0.924 | 0.708 |
|                   |ED-LSTM|             0.919 |                 0.992 |         1.010 | 1.048 | 0.699 |
|                   | CNN   |             0.859 |                 1.051 |         1.018 | 0.926 | 0.634 |
| All Countries     | sRNN  |             1.235 |                       |               |       |       |
|                   | LSTM  |             0.964 |                       |         0.933 | 0.810 | 1.000 |
|                   |Bi-LSTM|             0.924 |                       |         0.956 | 0.656 | 1.014 |
|                   |ED-LSTM|             0.989 |                       |         1.019 | 0.841 | 0.824 |
|                   | CNN   |             1.009 |                       |         1.043 | 0.874 | 0.817 |

---

