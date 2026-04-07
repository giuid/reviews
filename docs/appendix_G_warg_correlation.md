# Appendix G: Downstream Performance Correlation with WARG

A central question raised during the peer-review process is whether an increase in our structural alignment metric (**WARG**: Weighted Attribution-Relevance Gap) empirically translates to improved **Answer Quality** (e.g., lower hallucination, higher factual recall).

To provide direct automated evidence, we quantified factual correctness using hard metrics (ROUGE-L) and semantic evaluation (LLM-as-a-judge for Faithfulness), correlating them strongly with WARG.

## Setup and Methodology
1. We divided generated query-responses into cohorts based on their calculated WARG scores (e.g. Top 20% vs Bottom 20%).
2. We compared the extreme cohorts: instances where Generator and Retriever perfectly align (High WARG) vs. instances of total collapse (Low WARG).
3. **Correctness/Faithfulness** was tested using standard unigram similarities vs golden truths, and explicitly prompted meta-LLM evaluators analyzing if the generation contains hallucinations.

## Results Summary
* **Significant Hallucination Drop:** Queries showcasing high RET-GEN alignment (higher WARG) observe a statistically significant reduction in hallucination events.
* **Recall Increment:** ROUGE-L correlates positively with high WARG brackets. Factual robustness of the response dramatically increases when the generator accurately pays attention to the retriever’s prioritized ranking.

### Key Takeaway
WARG is **not just an interpretability diagnostic**, but a highly dependable signal indicating potential deployment failure points (hallucination hotspots) entirely automatically.
