# Summary of Multivariate G20 DL models

RMSE of each DL model trained on G20 countries combined dataset with selected features

The target countries are the US, China, and India

| Model   |   China |   India |   United States |
|:--------|--------:|--------:|----------------:|
| RNN     | 273.973 | 124.26  |         252.754 |
| LSTM    | 322.86  | 123.992 |         238.161 |
| Bi-LSTM | 289.704 | 126.942 |         250.429 |
| ED-LSTM | 301.918 | 126.674 |         254.679 |
| CNN     | 307.72  | 127.191 |         242.975 |

---

MASE of each DL model trained on G20 countries combined dataset with selected features

The target countries are the US, China, and India

| Model   |   China |   India |   United States |
|:--------|--------:|--------:|----------------:|
| RNN     |  0.9374 |  0.7055 |          0.979  |
| LSTM    |  1.0639 |  0.6817 |          0.9428 |
| Bi-LSTM |  0.946  |  0.71   |          0.9742 |
| ED-LSTM |  1.0188 |  0.6972 |          0.9949 |
| CNN     |  1.0036 |  0.7049 |          1.0211 |

