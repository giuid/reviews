# Appendix E: Additional Results on Qwen2.5-7B-Instruct

As noted during the review process, assessing RAG architectural behaviors across multiple divergent model families reinforces the generalized validity of the findings. Along with Llama and Gemma, we extensively integrated **Qwen2.5-7B-Instruct** into the RAG-E diagnostic pipeline.

## General Diagnostics

The results for Qwen follow a remarkably similar trajectory to Gemma and Llama. Qwen exhibits measurable vulnerability to **Wasted Retrieval** and **Noise Distraction** when interfaced natively with DRAGON and Arctic Embed models. 

### Selected Highlights
While specific failure percentages fluctuate depending on exact prompt construction, the **primacy bias** strictly mimics behaviors identified in other leading open weights. Evaluating Qwen solidifies the conclusion that failure mappings uncovered via `WARG` and the `pmcSHAP` attributions are structural issues of modern decoder-only architectures applied naively to dense retrieval context windows, and are not tied to an isolated model paradigm.

*(Complete logs, CSV arrays, and attribution plots concerning Qwen outputs reside natively in the `/analysis_data/` directory of this repository).*
