# RAG-E: Quantifying Retriever-Generator Alignment and Failure Modes
## Reproducibility and Supplementary Materials

Welcome to the reproducibility repository for the paper **"RAG-E: Quantifying Retriever-Generator Alignment and Failure Modes"**.

This repository provides full transparency, extended datasets, and analysis scripts for the core empirical claims discussed in the paper, as well as supplementary documents prepared during the rebuttal phase.

## 📂 Repository Contents


* **`docs/`**: Markdown documents mirroring the analytical additions provided to reviewers (Qwen results, threshold sensitivity, downstream correlation, and PMCSHAP ablation).

## 📊 Rebuttal Documentation 

During the rebuttal process, we expanded our analyses to definitively answer reviewer questions. You can explore the full data in the `docs/` folder:

1. **[Qwen2.5-7B-Instruct Results](docs/appendix_E_qwen_results.md)**
   Extended evaluations detailing the performance and failure rates for Qwen.
2. **[Sensitivity Analysis of Thresholds](docs/appendix_F_threshold_sensitivity.md)**
   Verification that structural rank inversion (Wasted Retrieval) is a consistent phenomenon across Top-1 to Top-5 thresholds.
3. **[Downstream Performance Correlation](docs/appendix_G_warg_correlation.md)**
   Automated metrics showing that high WARG scores map to higher factual correctness and lower hallucination rates.

