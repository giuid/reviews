# Sensitivity Analysis of Failure Mode Thresholds

In our initial submission, we defined Wasted Retrieval and Noise Distraction using a baseline cutoff threshold of **Rank > 2** (the Top-3 documents). To provide full transparency and address feedback regarding threshold arbitrariness, we have conducted a comprehensive parameter sweep from Top-1 to Top-5.

## Findings
The results conclusively demonstrate that the architectural misalignment persists systematically. Changing the boundary simply causes a smooth, proportional progression of the failure rates, confirming that the mismatch is a structural feature of the Generator, not a mathematical artifact of the threshold.

### Comprehensive Failure Mode Rates by Threshold
*(Evaluating Gemma and Llama with Dragon and Snowflake Retrievers on FoodSafeSum and TREC CAsT)*

| Dataset | Model | Retriever | Threshold Cutoff | Wasted Retrieval (%) | Noise Distraction (%) |
|---|---|---|:---:|:---:|:---:|
| **FSS** | Llama | Dragon | Top-1 (Rank > 0) | 57.1% | 57.1% |
| **FSS** | Llama | Dragon | Top-2 (Rank > 1) | 47.4% | 49.6% |
| **FSS** | Llama | Dragon | **Top-3 (Rank > 2)** | **39.1%** | **41.4%** |
| **FSS** | Llama | Dragon | Top-4 (Rank > 3) | 33.1% | 33.1% |
| **FSS** | Llama | Dragon | Top-5 (Rank > 4) | 25.6% | 22.6% |
| **TREC** | Gemma | Snowflake | Top-1 (Rank > 0) | 61.8% | 66.5% |
| **TREC** | Gemma | Snowflake | Top-2 (Rank > 1) | 51.4% | 56.1% |
| **TREC** | Gemma | Snowflake | **Top-3 (Rank > 2)** | **40.5%** | **46.8%** |
| **TREC** | Gemma | Snowflake | Top-4 (Rank > 3) | 32.4% | 39.9% |
| **TREC** | Gemma | Snowflake | Top-5 (Rank > 4) | 24.9% | 30.6% |

**Conclusion:** Relaxing the structural boundary monotonically reduces the absolute occurrence rate exactly as expected, yet a stark proportion (25% to 50%) of LLM decisions still involve ignoring the retriever's highest-scored inputs in favor of low-ranking or non-retrieved knowledge.
