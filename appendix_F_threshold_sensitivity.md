# Appendix F: Sensitivity Analysis of Failure Mode Thresholds

In our main manuscript, we reported the rates for **Wasted Retrieval** and **Noise Distraction** using a Top-3 threshold (Rank > 2). To demonstrate that the architectural misalignment is structurally systematic (and not an artifact of the cutoff), we evaluated the failure mode rates across a continuous sweep of ranking thresholds (Top-1 to Top-5). 

The data confirms a smooth and proportional degradation in structural rank inversions exactly as the boundary is relaxed. The misalignment remains robustly visible regardless of the predefined scope parameter.

### Empirical Failure Mode Rates by Threshold (Excerpt)

| Dataset | Model | Retriever | Threshold | Wasted Retrieval (%) | Noise Distraction (%) |
|---|---|---|:---:|:---:|:---:|
| **FSS** | Llama | Dragon | Top-1 | 57.1% | 57.1% |
| **FSS** | Llama | Dragon | Top-2 | 47.4% | 49.6% |
| **FSS** | Llama | Dragon | Top-3 | 39.1% | 41.4% |
| **FSS** | Llama | Dragon | Top-4 | 33.1% | 33.1% |
| **FSS** | Llama | Dragon | Top-5 | 25.6% | 22.6% |
| **TREC**| Gemma | Snowflake | Top-1 | 61.8% | 66.5% |
| **TREC**| Gemma | Snowflake | Top-3 | 40.5% | 46.8% |
| **TREC**| Gemma | Snowflake | Top-5 | 24.9% | 30.6% |

*(For the exhaustive table covering all cross-evaluations, refer to the full CSV outputs in the `/analysis_data/` folder).*

### Conclusion
Shifting the threshold systematically changes the absolute failure rate exactly as expected, yet a massive proportion of interactions still feature the LLM prioritizing low-ranked documents. Setting the threshold dynamically or via parameterized metrics (such as WARG) effectively captures the true alignment signal.
