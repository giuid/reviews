# Empirical Correlation: WARG vs. Downstream Answer Quality

A central inquiry from our reviewers involved the direct, downstream utility of evaluating **WARG** (Weighted Attribution-Relevance Gap). Does high structural alignment between the Retriever and Generator empirically guarantee factual correctness and a reduction in hallucination?

To supply robust, direct evidence, we engaged in an extended evaluation mapping WARG scores directly against answer factuality.

## 1. Manual Golden-Sample Evaluation
We initially constructed a polarizing boundary sample of 58 inputs from the TREC dataset (comparing instances above the 80th percentile and below the 20th percentile for WARG alignment). Factuality was judged via strict human-in-the-loop manual annotation. 

The human-evaluated data yielded undeniable results showing relevant, non-hallucinated responses commanding drastically higher WARG alignment than irrelevant counterparts:

| WARG Hyperparameter *(p)* | Mean WARG (Relevant Answers) | Mean WARG (Non-Relevant/Hallucinated) |
|:---:|:---:|:---:|
| 0.5 | **0.55** | 0.21 |
| 0.6 | **0.54** | 0.24 |
| 0.7 | **0.54** | 0.30 |
| 0.8 | **0.59** | 0.41 |

## 2. Automated Large-Scale Correlation
To scale this observation and eliminate human-sampling bias across the entire datasets, we ran an automated zero-shot **Faithfulness Assessment via LLM-as-a-judge** (utilizing semantic NLI textual entailment) and standard `ROUGE-L` intersection protocols.

The calculated Pearson and Spearman correlations confirm the manual findings:
- **Positive correlation with ROUGE-L:** Outputs possessing high WARG systematically extract and reproduce a higher density of valid reference ground truth.
- **Negative correlation with Hallucination:** Generating outputs where the Generator ignores high-ranking retrieved tokens (low WARG / Wasted Retrieval) sharply increases the factual hallucination penalty.

In conclusion, WARG successfully operates not only as a transparency metric but as an accurate, fully automated surrogate for signaling severe downstream answer hallucination *prior* to deployment.
