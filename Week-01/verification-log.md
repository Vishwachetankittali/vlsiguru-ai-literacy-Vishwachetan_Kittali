# Week 01 Verification Log

 Question / claim | AI tool | Claim checked | Verification source / experiment | Result |
|---|---|---|---|---|
48,729 × 3,817 | Gemini | Product = 185,998,593 | Python in Google Colab: `48729 * 3817` | Correct |
48,729 × 3,817 | ChatGPT | Product = 186,070,593 | Python in Google Colab; re-added its own partial products by hand | Incorrect (correct value 185,998,593, off by 72,000). The partial products were right; the final sum was wrong |
IPv6  Question | Chatgpt | [bits in an IPv6 address; current RFC number] | [RFC Editor page + search results] | Incorrect |
Google Maps ETA uses ML | web source | Travel time is predicted by a Graph Neural Network | DeepMind blog (2020): deepmind.google/blog/traffic-prediction-with-advanced-graph-neural-networks/ | Confirmed.   Describes the system as of 2020 |
Gmail spam filter uses ML | web source | ML models block spam and phishing, with rules also used | Google Workspace blog on Gmail security updates | confirmed |
Face ID uses neural networks | web source | Facial matching done by neural networks in the Secure Enclave | Apple Platform Security guide: support.apple.com/guide/security/sece151358d1/web | Confirmed |
definitions of AI, ML, DL, GenAI, agent | web source | Hierarchy and definitions | https://toloka.ai/blog/difference-between-ai-ml-llm-and-generative-ai/ | Self Verified |
rules-based vs learned behaviour | web source | Distinction between traditional software and ML | https://hyring.com/learn/artificial-intelligence/rule-based-vs-learning-based-systems | Self Verified |
tokens and next-token prediction | web source | Prompt → tokens → probabilities → next token | (https://medium.com/data-science-collective/what-happens-when-you-send-a-prompt-to-an-llm-d12932849609 | Self Verified |
agent = model + tools in a loop | web source | Definition of agent vs LLM, RAG, tool-using assistant | https://medium.com/@manastiwary2067/understanding-ai-ai-ml-dl-nlp-generative-ai-agentic-ai-fb49bc3e6c15 | Self Verified |
prediction / classification / generation | web source | Definitions; next-token prediction as the basis of text generation | https://medium.com/@magtk/classification-regression-and-prediction-what-is-the-difference-7d10447e6181 | Self Verified |

## Notes

**What did the AI get right?**
Gemini gave the correct product in the multiplication test and the correct
ChatGPT's partial products were all correct.

**What did it get wrong or leave unsupported?**
ChatGPT's final total in the multiplication was wrong by 72,000, even
though its steps were correct.

**What did I learn about verification?**
- A tool (Python) is better than an explanation for checking numbers.
- "Shows its work" does not mean the final answer is right.
- Matching answers from two assistants is not proof; a source is.
- When a check is taking too long, I should log what is verified, what is
  not, and why, instead of guessing.
