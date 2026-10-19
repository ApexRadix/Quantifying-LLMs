# LLM Quantification Suite

An empirical evaluation framework designed to systematically quantify Large Language Models across predictive uncertainty, token-level entropy distributions, latency scaling, and behavioral consistency.

## Repository Files

This repository is kept minimal and self-contained:

Theoretical Framework and Empirical Metric Suite
Evaluating Large Language Models requires looking beyond simple task accuracy to analyze the confidence of their probabilistic predictions, information density, and real-time execution overhead. This evaluation suite profiles generative behavior across four core dimensions: predictive dispersion, local unexpectedness, sequence modeling fit, and hardware decoding throughput.
Predictive dispersion is measured via Shannon Entropy across the entire vocabulary at each decoding step. Expressed in bits, it captures how evenly or sharply the model distributes its probability mass. A high entropy value indicates that the model is dividing its confidence among multiple competing candidate tokens, pointing to ambiguity or generative indecision. Conversely, low entropy signifies sharp confidence, where the model concentrates almost all probability onto a single deterministic output.
To isolate local transitions and deviations, the framework evaluates Token-Level Surprisal. Surprisal measures the self-information or unexpectedness of a specific target token given the preceding context. In stable, expected phrasing, surprisal remains low. When the model encounters anomalous syntax, hallucinated claims, or sudden out-of-context shifts, surprisal spikes sharply, serving as an effective diagnostic for local degeneration and sequence-level divergence.
Overall sequence quality is captured using Perplexity. Perplexity represents the exponentiated average negative log-likelihood across evaluated tokens. In practical terms, it acts as the effective branching factor of the model, representing the weighted average number of equally likely tokens between which the model must decide at every generation step. Lower perplexity reflects a model distribution that closely matches the target data manifold.
Operational efficiency is assessed using Inference Latency, specifically isolated to the active generation phase. By separating prompt prefill time from autoregressive decoding, this metric isolates the exact duration required to produce each token in milliseconds. This directly reflects how effectively an architecture utilizes memory bandwidth and computational hardware under diverse batch sizes and prompt lengths.


```text
quantifying-llms/
├── quantification_experiments.ipynb  # Primary Colab notebook with end-to-end evaluation pipeline
├── dataset.csv                       # Prompt evaluation dataset / benchmark corpus
└── README.md                         # Project documentation and quick start
