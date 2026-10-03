# AI Engineering Journal - Week 01

**Date:** 2026-10-04

## What I learned that was genuinely new
- An AI answer can show correct steps and still end with a wrong final
  result. In my multiplication test, ChatGPT's four partial products were
  correct, but its total was wrong by 72,000.
- Language models generate likely-looking text one token at a time; they
  do not calculate or check facts. (Q3)
- Many "smart" features are not AI, and it matters whether behaviour is
  learned from data or written as rules. (Q2, Q8)

## One AI output I initially trusted
ChatGPT's answer to 48,729 × 3,817 (186,070,593). It was neatly laid out,
showed its method, and stated the result confidently, so it looked
reliable until I compared it with another source.

## How I verified it
I ran `48729 * 3817` in Google Colab, which printed 185998593. I then
re-added ChatGPT's own partial products by hand and got the same value,
which showed the error was in its final addition. Gemini's answer matched
Python.

## What the AI did well
- Explained methods and concepts clearly and quickly.
- Showed its working, which made it possible to find where the error was.

## What the AI could not be trusted to decide
- Whether its own final answer was correct.
- Whether a claim is true without a source (for example the BLEU score
  and version-history claim about the Transformer paper).
- Which source is authoritative, and whether information is current.

## One question I still have
- How do tools like Python get used inside AI assistants automatically?  
- How will AI change Physical Design work in the next 3-5 years?

## What I will do differently next week
- Verify numbers with a tool and re-check the final step myself.
- Choose test questions with an answer that can be checked quickly, and
  log the verification as I go instead of at the end.
- Start the week's work earlier so the deadline does not squeeze the
  verification. 

## Other notes
- Biggest difficulty this week: The work for this week felt too much as I had training class assignments also. 10 questions with AEVR analysis actually consumed lot of time.
