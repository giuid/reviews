# Additional Results on Qwen2.5-7B-Instruct

During the rebuttal phase, to ensure that the findings regarding **Wasted Retrieval** and **Noise Distraction** are not isolated to older or specific model families, we integrated the state-of-the-art **Qwen2.5-7B-Instruct** into our RAG-E diagnostic pipeline.

## 1. Wasted Retrieval and Noise Distraction
The fundamental failure modes persist structurally within Qwen. The model exhibits a strong primacy bias, consistently prioritizing documents placed at the very top of the context window, regardless of the relative relevance scores originally assigned by the Retriever.

### TREC CAsT Dataset (Subset)
| Retriever | Wasted Retrieval (%) | Noise Distraction (%) |
|:---:|:---:|:---:|
| **Dragon** | ~39.9% | ~28.9% |
| **Snowflake** | ~42.2% | ~27.2% |

### 2. Retriever-Generator Alignment (Attribution vs Rank)
When visualizing the `pmcSHAP` generation attributions across the retrieved ranks, Qwen closely mirrors the distribution seen in Llama and Gemma. The generator overwhelmingly attributes answer generation to Rank 1 and 2, but frequently falls back on local LLM parametric knowledge or irrelevant context when the alignment with the retriever is low.

*(Raw output logs and visual PDF distributions for Qwen are stored directly inside the `data/` folder of this repository).*
