# Sources and the claims each supports

> Before submitting: open every link and confirm it still loads and says what is claimed. URLs for the Google/Kaggle/IBM course pages are the standard public addresses; check they are current.

| ID | Source | Link | Supports (mission / claim) |
|---|---|---|---|
| S1 | Google for Developers — Introduction to Machine Learning | https://developers.google.com/machine-learning/intro-to-ml | M1, M3: what ML is, how it differs from traditional programming, supervised/unsupervised/reinforcement learning basics |
| S2 | Google — Machine Learning Crash Course | https://developers.google.com/machine-learning/crash-course | M2, M5, M6: features/labels, linear regression, loss, classification metrics, datasets and generalisation |
| S3 | Google — Overfitting (Crash Course module) | https://developers.google.com/machine-learning/crash-course/overfitting | M6: overfitting, generalisation, train/validation/test roles |
| S4 | Google — Problem framing | https://developers.google.com/machine-learning/problem-framing | M8: deciding whether ML is appropriate, defining outputs and success metrics |
| S5 | Google — Production ML systems | https://developers.google.com/machine-learning/crash-course/production-ml-systems | M7: monitoring, drift, data leakage, test vs real-world gap |
| S6 | Kaggle Learn — Intro to Machine Learning | https://www.kaggle.com/learn/intro-to-machine-learning | M5, M6: model validation, under/overfitting |
| S7 | IBM — What is machine learning? | https://www.ibm.com/think/topics/machine-learning | M1, M3: AI/ML/DL relationship; learning approaches |
| S8 | Xie et al., "RouteNet: Routability Prediction for Mixed-size Designs using Convolutional Neural Network", ICCAD 2018 (**primary**) | https://research.nvidia.com/publication/2018-11_RouteNet%3A-routability-prediction (PDF: https://research.nvidia.com/sites/default/files/pubs/2018-11_RouteNet%3A-routability-prediction/a80-xie.pdf) | M9: CNN used for routability/DRC-hotspot prediction; benchmark results (comparable routability accuracy to global router with less runtime; 50 % better hotspot accuracy than global routing; outperforms SVM/logistic regression) |
| S9 | "Towards Machine Learning for Placement and Routing in Chip Design: a Methodological Overview" (survey) | https://arxiv.org/pdf/2202.13564 | M9: RouteNet described as first CNN attempt at DRC-hotspot forecasting; context of routability-prediction research |

## Notes on source use
- Mission explanations are written in my own words; the sources were used to check concepts and claims.
- The synthetic datasets, numbers and hypothetical failures in Missions 2, 5, 6, 7 and 8 are **illustrative inventions of mine**, not data from any source.
- No claim is made that RouteNet is deployed in commercial tools.
- AI was used as a learning aid; claims were checked against the sources above.
