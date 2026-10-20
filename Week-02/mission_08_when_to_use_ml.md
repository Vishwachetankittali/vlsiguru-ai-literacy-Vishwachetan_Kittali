# Mission 8 — Does this problem actually need ML?

**Principle:** Start with the problem, not the technology.

## Decision checklist
1. **Define the problem and desired outcome.** (What decision will this support?)
2. **Is a simple rule or conventional program already good enough?**
3. **Is suitable data available**, and what exactly should the model predict?
4. **How will success be measured**, and against what baseline?
5. **What happens if a prediction is wrong?**

## Example problem: early warning of likely timing-closure failure in a P&R run

| | Rule-based solution | ML solution |
|---|---|---|
| Idea | "Flag if utilisation > 80 % AND congestion > 10 % AND clock period < 1.8 ns" | Model trained on past runs predicts fail probability from many features |
| Data required | Engineer experience; a few historical runs to set thresholds | Hundreds–thousands of labelled runs with consistent features and sign-off outcomes |
| Strengths | Transparent, cheap, easy to explain and audit, no training | Can capture non-obvious combinations of many features; can improve with data |
| Weaknesses | Misses subtle interactions; thresholds go stale; hard to maintain with many features | Needs data, maintenance and monitoring; less transparent; may overfit |
| Failure modes | Rigid thresholds → false alarms or misses when design style changes | Leakage, drift, bias to training designs, silent degradation, over-trust |
| Cost of a wrong prediction | Same business consequence, but easier to see why it failed | Same consequence; harder to diagnose |
| Maintenance | Update thresholds by hand | Retrain, re-validate, monitor |

## Verdict
Begin with the rule-based flag as the **baseline**. Move to ML only if (a) the rule is not accurate enough, (b) enough reliable data exists, and (c) the ML model beats the baseline on unseen designs by a margin that justifies its cost. If the rule is already adequate, ML adds complexity without benefit. Data existing is not a reason by itself to use ML.
