# Summary of Multivariate G20 DL models

RMSE of each DL model trained on G20 countries combined dataset with selected features

The target countries are the US, China, and India

| Model   |   China |   India |   United States |
|:--------|--------:|--------:|----------------:|
| RNN     | 300.447 | 144.762 |         284.64  |
| LSTM    | 308.417 | 123.851 |         240.619 |
| Bi-LSTM | 279.417 | 127.153 |         247.588 |
| ED-LSTM | 323.752 | 126.491 |         256.617 |
| CNN     | 309.631 | 116.537 |         258.872 |

---

MASE of each DL model trained on G20 countries combined dataset with selected features

The target countries are the US, China, and India

| Model   |   China |   India |   United States |
|:--------|--------:|--------:|----------------:|
| RNN     |  1.0881 |  0.871  |          1.1738 |
| LSTM    |  1.0256 |  0.681  |          0.9759 |
| Bi-LSTM |  0.924  |  0.7076 |          0.9891 |
| ED-LSTM |  1.0478 |  0.6994 |          1.0104 |
| CNN     |  0.9261 |  0.6339 |          1.0175 |

