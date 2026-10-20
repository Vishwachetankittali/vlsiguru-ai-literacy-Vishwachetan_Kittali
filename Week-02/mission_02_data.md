# Mission 2 — Data: what does an ML system learn from?

**Research question:** What does it mean to learn a pattern from data?

## 1. Vocabulary (own words)
| Term | Meaning | Example (physical design) |
|---|---|---|
| Dataset | The whole collection of examples | All 8 runs in the table below |
| Sample / observation | One example (one row) | One P&R run |
| Feature | An input property used to predict | Utilisation %, clock period |
| Label / target | The answer we want the model to predict | `timing_result` (pass/fail) |
| Labelled example | Has the answer attached | Run with a known pass/fail |
| Unlabelled example | No answer attached | A new run before timing sign-off |

**Structured vs unstructured:** structured data fits rows/columns (a table of run metrics); unstructured data does not (layout images, log text, waveforms).
**Numerical vs categorical:** numerical = measured numbers (utilisation 72.5); categorical = labels from a set (`tool_version = A / B`).
*Label vs target:* often used interchangeably; "target" is what the model predicts, "label" is the known value attached to a training example.

## 2. Illustrative dataset (synthetic — not real chip data)
Goal: predict whether a place-and-route run will meet timing.

| run_id | utilization_pct | clock_period_ns | num_macros | avg_fanout | congestion_pct | tool_version | timing_result (target) |
|---|---|---|---|---|---|---|---|
| R01 | 62 | 2.0 | 4 | 3.1 | 3.5 | A | pass |
| R02 | 68 | 2.0 | 6 | 3.4 | 5.0 | A | pass |
| R03 | 75 | 1.8 | 8 | 3.9 | 9.2 | A | fail |
| R04 | 81 | 1.8 | 10 | 4.2 | 12.8 | B | fail |
| R05 | 58 | 2.2 | 3 | 2.9 | 2.1 | B | pass |
| R06 | 79 | 1.6 | 9 | 4.5 | (missing) | B | fail |
| R07 | 70 | 2.0 | 5 | 3.3 | 6.1 | A | pass |
| R08 | 72 | 1.7 | 7 | 4.0 | 8.7 | B | pass *(suspect label)* |

- **Features:** utilization_pct, clock_period_ns, num_macros, avg_fanout, congestion_pct (numerical); tool_version (categorical).
- **Target:** timing_result (categorical: pass/fail) → a classification problem.
- **Not a feature:** run_id (just an identifier).
- Deliberate issues for discussion: R06 has a **missing value**; R08 looks like a **possible inconsistent label** (its inputs resemble the failing runs).

## 3. Two ways data quality affects a model
1. **Label errors / inconsistency.** If R08 is really a failure but was recorded as a pass (e.g. a different timing corner was checked), the model is taught a wrong rule. With a tiny dataset one wrong label can shift what it learns; in large datasets systematic label errors are the bigger risk.
2. **Missing or unrepresentative data.** Missing congestion in R06 must be dropped or filled in; filling with an average could hide the very congestion that caused the failure. Also, all runs here are small designs — a model trained on them may mislead on large designs.

## 4. Quantity ≠ quality
A million rows from one design family, one tool version, with sloppy labels still teaches a narrow or wrong pattern. More data helps only if it is **accurate, consistent, relevant and representative** of the situations where the model will be used. Clean 500 representative rows can beat 50,000 noisy, duplicated ones.

## 5. Data collection / cleaning checklist
- Collect from reproducible runs; record tool version, corner and constraints.
- Remove duplicates; check units; flag outliers.
- Decide how to handle missing values (drop, fill, flag) and document why.
- Audit labels (is "pass" always defined the same way?).
- Keep an untouched test set (see Mission 6).

## 6. What remains unclear
How much data is "enough" — it depends on problem complexity and model, and I need to learn how to judge it.
