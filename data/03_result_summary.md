# Summary of Multivariate Deep Learning Experiments

This summary shows the performance of four deep learning models (LSTM, Bi-LSTM, ED-LSTM, CNN) trained on different country groups to predict CO2 emissions for three target countries: The United States, China, and India

### Performance Summary: RMSE

| Training Dataset  | Model | Avg (3 Countries) |   Avg (All in Train)  | United States | China | India | 
|:------------------|:------|------------------:|----------------------:|--------------:|------:|------:|
| Three Countries   | LSTM  |           272.237 |               272.237 |       251.134 |426.572|139.005|
|                   |Bi-LSTM|           239.235 |               239.235 |       263.716 |328.626|125.362|
|                   |ED-LSTM|           259.509 |               259.509 |       223.622 |411.619|143.287|
|                   | CNN   |           289.161 |               289.161 |       243.810 |466.028|157.645|
| G7 + China + India| LSTM  |           227.882 |                93.296 |       257.344 |296.170|130.133|
|                   |Bi-LSTM|           252.552 |               100.759 |       222.043 |407.204|128.409|
|                   |ED-LSTM|           237.861 |                96.769 |       243.517 |335.206|134.860|
|                   | CNN   |           217.599 |                91.121 |       235.652 |281.326|135.819|
| G20               | LSTM  |           198.041 |                53.430 |       210.954 |267.572|115.598|
|                   |Bi-LSTM|           220.889 |                57.339 |       242.950 |294.988|124.730|
|                   |ED-LSTM|           225.208 |                57.709 |       239.030 |312.625|123.970|
|                   | CNN   |           238.790 |                61.981 |       267.378 |310.956|138.035|
| All Countries     | LSTM  |           209.781 |                 8.885 |       241.032 |235.446|152.864|
|                   |Bi-LSTM|           205.904 |                 8.877 |       242.275 |215.788|159.650|
|                   |ED-LSTM|           207.935 |                 8.479 |       256.413 |234.900|132.492|
|                   | CNN   |           220.211 |                10.188 |       287.247 |243.797|129.590|

---
