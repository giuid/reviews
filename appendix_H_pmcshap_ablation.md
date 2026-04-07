# Appendix H: (p)mcSHAP Theoretical Motivation and Ablation

Our explainability framework employs an autoregressive attribution mapping. For LLMs acting via the function $f(\text{docs}) \rightarrow \text{tokens}$, calculating the exact Shapley values is computationally infeasible. Using `kSHAP` directly is theoretically fraught in RAG due to its baseline assumption regarding the independent variance of features, which breaks when retrieved contexts contain overlapping, non-independent semantic fields.

### The Role of PMCSHAP and Variance Smoothing

1. **`kSHAP`**: Operates efficiently via Weighted Least Squares (WLS), but implicit sampling struggles with correlated semantic similarities.
2. **`pSHAP` ($N'=N$)**: Re-introduces symmetry by enforcing paired sampling. It inherently eliminates first-order variance inconsistencies.
3. **`pmcSHAP` (Our framework)**: Supercharges `pSHAP` by applying robust Monte Carlo samples across perturbed subsets. By escalating $N'$ beyond $N$, the estimator smooths out higher-order fluctuations specific to highly-sensitive autoregressive sequence generation.

### Empirical Ablation

We performed a Mean Squared Error (MSE) comparison test of these estimators relative to the intractable but exact Shapley calculation on constrained subset inputs.

**Findings:**
- `kSHAP` displays the highest instability (high MSE) when faced with redundant semantic contexts.
- Moving to `pSHAP` ($N'=N$) demonstrates an immediate visible drop in variance.
- Incrementally increasing parameter $N'$ (e.g. 10, 50) in `pmcSHAP` leads to a clean, monotonic convergence of MSE toward theoretical perfection limits. 

The integration of `pmcSHAP` guarantees reliable, run-to-run consistent attribution mappings even within inherently noisy and overlapping generative inference windows.
