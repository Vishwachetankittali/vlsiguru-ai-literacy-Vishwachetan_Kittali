# Mission 4 — ML Task Types

**Research question:** What kinds of problems can machine learning solve?

## 1. Task types: input → output
| Task | Typical input | Expected output |
|---|---|---|
| Classification | Features of an item | A category (pass/fail, defect/no defect) |
| Regression | Features of an item | A number (delay, power) |
| Clustering | Many unlabelled items | Group assignments |
| Anomaly detection | Measurements, usually mostly "normal" | A flag/score for unusual items |
| Dimensionality reduction | Data with many features | Fewer-dimensional representation |
| Recommendation / ranking | A set of candidates | An ordered list |

## 2. Eight real-world problems classified
| # | Problem | Task type | Input | Output | Domain |
|---|---|---|---|---|---|
| 1 | Email spam detection | Classification | Email text, sender | Spam / not spam | General |
| 2 | House price estimate | Regression | Area, location, rooms | Price | General |
| 3 | Customer segmentation | Clustering | Purchase histories | Segment groups | General |
| 4 | Credit-card fraud flagging | Anomaly detection | Transaction patterns | Suspicious score | General |
| 5 | Movie suggestions | Recommendation/ranking | Watch history | Ranked movie list | General |
| 6 | Compressing hundreds of sensor readings to 2-D plot | Dimensionality reduction | Many measurements | 2–3 derived features | General |
| 7 | **Predict post-route congestion/DRC-hotspot from placement** | Classification (per region) or regression (per region) | Placement/density features per layout tile | Hotspot yes/no or congestion value | **Semiconductor** |
| 8 | **Flag abnormal wafer-test measurement patterns** | Anomaly detection | Parametric test measurements per die/wafer | Anomaly score / flag | **Semiconductor** |
| (extra) | Estimate post-synthesis delay or power from RTL-stage features | Regression | Early design features | Delay (ns) / power (mW) | Semiconductor |

## 3. Task type ≠ learning paradigm
- The **task** says *what the model must do* (output type).
- The **paradigm** says *how it learns* (training signal).
- Same task, different paradigms: anomaly detection can be supervised (labelled defects exist), unsupervised (only "normal" data), or semi-supervised.
- Same paradigm, different tasks: supervised learning can do classification **or** regression.
- Therefore a task type by itself does **not** tell you how the model was trained.
- Several algorithms can address the same task (e.g. classification by logistic regression, random forest or a neural net).

## 4. Unclear / to check
Clustering and anomaly detection can overlap (outliers may be "tiny clusters"); I will look at how practitioners separate them.
