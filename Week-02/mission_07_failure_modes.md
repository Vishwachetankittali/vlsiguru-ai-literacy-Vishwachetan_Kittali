# Mission 7 — Why ML Systems Fail

**Research question:** Even if a model works during testing, why might it fail in reality?

Key ideas: unrepresentative data, label errors, missing/noisy values, bias (performance differing across subsets), **data leakage** (information in training that would not be available at prediction time, making evaluation look too good), **drift** (real-world data changing), and the need for human oversight because wrong predictions have consequences.

## Failure 1 — Data leakage in a timing predictor (hypothetical)
- **What happened:** A model to predict timing pass/fail at *placement* stage scores 99 % in testing, but is nearly useless at real placement time.
- **Likely cause:** One feature (e.g. post-route slack or a final-report field) was only available after routing, so the model effectively "saw" the answer.
- **Evidence:** Feature-importance shows one feature dominating; checking the feature's timestamp/stage in the flow; performance collapses when the feature is removed.
- **Mitigation:** Build features only from information available at the prediction point; review each feature's origin; split by design (not randomly by run) so near-duplicates don't cross the split.

## Failure 2 — Drift after a tool/process change (hypothetical)
- **What happened:** A congestion-prediction model works for months, then accuracy falls after a new EDA tool version and a new technology node.
- **Likely cause:** Data drift — input distributions and the relationship between features and outcome changed (different routing behaviour, design rules).
- **Evidence:** Compare feature distributions of recent vs training data; monitor error over time; spot checks against actual routed results.
- **Mitigation:** Monitoring with alerts; retrain/re-validate on new data; keep tool/node metadata as features or train separate models; keep a fallback to the standard flow.

## Failure 3 — Unrepresentative data / subgroup bias (hypothetical)
- **What happened:** A defect-classification model on wafer images performs well overall but misses defects on one product line.
- **Likely cause:** Training images came mostly from other product lines; defect types for that line were rare or mislabelled.
- **Evidence:** Break metrics down by product line/subset; examine confusion matrix per subset; review labels with a domain expert.
- **Mitigation:** Collect and correctly label more data for under-represented groups; set minimum per-subset performance targets; human review for low-confidence cases.

## Human oversight
A wrong prediction in EDA can waste days of runtime (false alarm) or let a real failure reach tape-out (miss). Predictions should be treated as **evidence to check**, with sign-off tools and engineers responsible for decisions.
