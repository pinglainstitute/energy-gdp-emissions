# Summary of Multivariate G20 DL models

RMSE of each DL model trained on G20 countries combined dataset with selected features

The target countries are the US, China, and India

| Model   |   China |   India |   United States |
|:--------|--------:|--------:|----------------:|
| LSTM    | 267.572 | 115.598 |         210.954 |
| Bi-LSTM | 294.988 | 124.73  |         242.95  |
| ED-LSTM | 312.625 | 123.97  |         239.03  |
| CNN     | 310.956 | 138.035 |         267.378 |

---

MASE of each DL model trained on G20 countries combined dataset with selected features

The target countries are the US, China, and India

| Model   |   China |   India |   United States |
|:--------|--------:|--------:|----------------:|
| LSTM    |  0.9076 |  0.6263 |          0.8093 |
| Bi-LSTM |  0.9615 |  0.6859 |          0.955  |
| ED-LSTM |  1.0255 |  0.6793 |          0.9407 |
| CNN     |  0.9936 |  0.7245 |          1.1716 |

