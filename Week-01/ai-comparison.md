# Week 01 AI Assistant Comparison

## Common question
What is 48,729 × 3,817? Give the exact result and show how you got it.

Each assistant received this exact wording in a fresh chat.

## Tool 1
Name: ChatGPT

Answer summary: Gave the result 186,070,593. It used the place-value
method, with partial products of 48,729 × 3,000 = 146,187,000,
48,729 × 800 = 38,983,200, 48,729 × 10 = 487,290 and
48,729 × 7 = 341,103, then added them.

Strengths:
- Clear, short layout, with the answer stated first
- All four partial products were correct
- Showed its method so the work could be checked

Weaknesses:
- The final sum was wrong (186,070,593 instead of 185,998,593, off by 72,000)
- The stated total did not follow from the partial products it listed
- The confident format hid the error

## Tool 2
Name: Gemini

Answer summary: Gave the result 185,998,593. It used the same partial
products method (×7, ×10, ×800, ×3,000) and added them to reach the final
result.

Strengths:
- Correct final answer
- Correct partial products and a step-by-step addition layout
- Clear explanation of the method

Weaknesses:
- No independent check, such as an estimate or a second method, was offered
- The answer gives no way to confirm correctness without another tool
- One correct answer on one question does not prove the tool is reliable

## Verification source
Python in Google Colab: `48729 * 3817` printed `185998593`.
Integer multiplication in Python is exact, so this is a reliable reference.
I also re-added ChatGPT's own partial products by hand
(146,187,000 + 38,983,200 + 487,290 + 341,103) and got 185,998,593.

## Final comparison
- **Accuracy:** Gemini was correct. ChatGPT was wrong in the final answer, though its intermediate steps were correct.
- **Traceability:** Both showed their method, which let me find where ChatGPT's error occurred (the final addition). Neither cited an external source, and for arithmetic none was needed.
- **Explanation quality:** Both were clear and used the same method. Good explanation quality did not predict correctness.
- **Ease of verification:** Very easy. One line of Python gave the exact answer in seconds.
- **Which claims required correction or qualification?** ChatGPT's total (186,070,593) needed correction to 185,998,593. Gemini's answer needed no correction, but it should still be confirmed with a tool before use.

## Lesson
Showing the steps does not guarantee the answer is right, and a neat,
confident explanation can hide a wrong result. For numbers, I should
verify with a tool such as Python and re-check the final step myself. Two
assistants disagreeing was useful evidence: it told me at least one was
wrong before I even ran the check.

*Note: this was a single question on a single occasion. It shows that
such errors can happen, but it does not measure how often either tool
makes them.*
