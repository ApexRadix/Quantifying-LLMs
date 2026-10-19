# LLM Quantification Suite

An empirical evaluation framework designed to systematically quantify Large Language Models across predictive uncertainty, token-level entropy distributions, latency scaling, and behavioral consistency.


## Repository Files

This repository is kept minimal and self-contained:

```text
quantifying-llms/
├── quantification_experiments.ipynb  # Primary Colab notebook with end-to-end evaluation pipeline
├── dataset.csv                       # Prompt evaluation dataset / benchmark corpus
└── README.md                         # Project documentation and quick start

Theoretical Framework & Metric Quantification
Large Language Model quantification requires moving past standard aggregate benchmark accuracies to evaluate fine-grained probabilistic confidence, informational efficiency, and runtime hardware behavior. Our evaluation pipeline assesses generation dynamics across four core dimensions: predictive dispersion, local information density, sequence-level fit, and autoregressive decoding throughput.
Predictive dispersion is captured via sequence-level Shannon Entropy, calculated across the complete vocabulary space at each generation step:
H(X)=− 
i=1
∑
∣V∣
​	
 P(w 
i
​	
 )log 
2
​	
 P(w 
i
​	
 )
This formulation quantifies the distribution spread in bits (shannons). Elevated entropy values reflect diffuse probability allocations across multiple candidate tokens—indicating model indecision, exploration regimes, or ambiguous context—while localized, low entropy signatures confirm sharp concentration on single deterministic outputs.
To assess local transition anomalies, the framework tracks Token-Level Surprisal, defined as the self-information of an observed target token conditioned on historical context:
I(w 
t
​	
 )=−log 
2
​	
 P(w 
t
​	
 ∣w 
<t
​	
 )
Surprisal directly indexes the information density of each generation step. Smooth, anticipated sequences sustain near-zero surprisal values, whereas abrupt divergence, syntactic breakdowns, and factual hallucinations register as high-magnitude surprisal spikes.
Overall sequence modeling competence is formalized through Perplexity (PPL), evaluated as the exponentiated mean negative log-likelihood over a window of length N:
PPL=exp(L 
CE
​	
 )=exp(− 
N
1
​	
  
t=1
∑
N
​	
 lnP(w 
t
​	
 ∣w 
<t
​	
 ))
Perplexity establishes the effective geometric branching factor of the autoregressive distribution, representing the equivalent number of uniform candidate choices the model navigates at each decision boundary.
Finally, hardware efficiency is quantified via Inference Latency, isolated to the token generation loop:
τ 
gen
​	
 = 
L 
generated
​	
 
t 
total
​	
 −t 
prefill
​	
 
​	
 
By factoring out prompt prefill time, this metric computes pure decoding latency in milliseconds per token (ms/token), providing a hardware-grounded profile of memory bandwidth saturation and autoregressive efficiency across varied sequence lengths and batch dimensions.
