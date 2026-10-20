# Mission 6 — Evaluation and Generalisation

**Research question:** How do we know whether a model has learned something useful?

## 1. Data splits
| Set | Role | Analogy |
|---|---|---|
| Training | Learn parameters | Practice problems |
| Validation | Compare models/settings and tune | Mock exam |
| Test | One final, untouched estimate of performance on unseen data | The real exam |
If the test set is used to make choices, it stops being an honest test.

## 2. Key ideas
- **Generalisation:** doing well on new, unseen data, not just remembered examples.
- **Overfitting:** model is too tailored to the training data (including noise): high training score, worse unseen score.
- **Underfitting:** model is too simple to catch the real pattern: poor on both.
- Training performance can exceed unseen performance because the model has already "seen" those examples.

## 3. Metrics at a conceptual level
| Metric | Question it answers |
|---|---|
| Accuracy | Of all predictions, how many were correct? |
| Precision | When it says "positive", how often is it right? |
| Recall | Of all real positives, how many did it find? |
| False positive | Predicted positive, really negative (false alarm) |
| False negative | Predicted negative, really positive (a miss) |
| Absolute error | For numbers: how far off was the prediction, ignoring direction? |

A metric must match the cost of mistakes. A **baseline** (e.g. "always predict the most common class", or a simple rule) shows whether the ML model adds any value.

## 4. Worked example: accuracy misleads with imbalanced classes
Setting: 1,000 timing runs; **20 truly fail** (positives = fail), 980 pass.

**Model A — lazy baseline: always predict "pass".**
- Correct: 980 of 1,000 → **accuracy = 98 %**
- Failures found: 0 of 20 → **recall = 0 %**; it never raises a warning. Looks excellent, is useless.

**Model B — a real model.**

| | Predicted fail | Predicted pass |
|---|---|---|
| Actually fail (20) | TP = 14 | FN = 6 |
| Actually pass (980) | FP = 10 | TN = 970 |

- Accuracy = (14 + 970) / 1000 = **98.4 %** (barely above the useless model)
- Precision = 14 / (14 + 10) = **58.3 %**
- Recall = 14 / (14 + 6) = **70 %**

**Lesson:** accuracy of 98 % vs 98.4 % hides a huge difference. **Recall** (and precision, or their trade-off) shows Model A catches 0 % of failures and Model B catches 70 %. In timing/yield, a missed failure (FN) is usually costlier than a false alarm (FP), so recall is highly relevant — but too many false alarms waste engineer time, so precision matters too.

## 5. Unclear
How to choose the decision threshold that balances precision and recall for a real project.
