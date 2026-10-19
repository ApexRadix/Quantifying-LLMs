# LLM Quantification Suite

An empirical evaluation framework designed to systematically quantify Large Language Models across predictive uncertainty, token-level entropy distributions, latency scaling, and behavioral consistency.


## Repository Files

This repository is kept minimal and self-contained:

```text
quantifying-llms/
├── quantification_experiments.ipynb  # Primary Colab notebook with end-to-end evaluation pipeline
├── dataset.csv                       # Prompt evaluation dataset / benchmark corpus
└── README.md                         # Project documentation and quick start

## Core Metrics Computed

| Metric | Mathematical Formulation | Description & Practical Interpretation |
| :--- | :--- | :--- |
| **Shannon Entropy** | $$H(X) = -\sum_{i=1}^{|V|} P(w_i) \log_2 P(w_i)$$ | Measures the flat dispersion and predictive uncertainty across the full vocabulary $|V|$ at a specific token step. Higher entropy indicates the model is uncertain or sampling from multiple viable candidates, while lower entropy indicates sharp confidence in a single output token. Expressed in bits (shannons). |
| **Token Surprisal** | $$I(w_t) = -\log_2 P(w_t \mid w_{<t})$$ | Quantifies the information content or "unexpectedness" of a specific target token $w_t$ given the preceding context $w_{<t}$. Highly anticipated tokens yield near-zero surprisal, whereas unexpected transitions or hallucinations produce sharp spikes in bit values. |
| **Perplexity (PPL)** | $$\text{PPL} = \exp\left( \mathcal{L}_{\text{CE}} \right) = \exp\left( -\frac{1}{N} \sum_{t=1}^N \ln P(w_t \mid w_{<t}) \right)$$ | Computes the exponentiated average negative log-likelihood over a sequence of length $N$. Intuitively represents the effective branching factor, or the weighted average number of equally likely tokens the model is choosing between at each step. Lower perplexity reflects superior generative model fit. |
| **Inference Latency** | $$\tau_{\text{gen}} = \frac{t_{\text{total}} - t_{\text{prefill}}}{L_{\text{generated}}}$$ | Measures decoding speed in milliseconds per token ($\text{ms/token}$) during the autoregressive generation phase, isolated from prompt prefill latency. Evaluates real-time decoding efficiency and hardware throughput across batch sizes and context lengths. |
