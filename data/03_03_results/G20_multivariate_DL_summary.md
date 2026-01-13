# Summary of Multivariate G20 DL models

RMSE of each DL model trained on G20 countries combined dataset with selected features

The target countries are the US, China, and India

| Model   |   China |   India |   United States |
|:--------|--------:|--------:|----------------:|
| RNN     | 274.324 | 127.93  |         261.27  |
| LSTM    | 284.296 | 122.12  |         238.576 |
| Bi-LSTM | 289.303 | 122.958 |         241.754 |
| ED-LSTM | 280.136 | 122.798 |         311.446 |
| CNN     | 298.318 | 138.256 |         248.356 |

---

MASE of each DL model trained on G20 countries combined dataset with selected features

The target countries are the US, China, and India

| Model   |   China |   India |   United States |
|:--------|--------:|--------:|----------------:|
| RNN     |  0.9109 |  0.7094 |          1.031  |
| LSTM    |  0.9734 |  0.6745 |          0.9426 |
| Bi-LSTM |  0.97   |  0.6855 |          0.9657 |
| ED-LSTM |  0.9074 |  0.7021 |          1.3069 |
| CNN     |  1.0026 |  0.722  |          1.0137 |

