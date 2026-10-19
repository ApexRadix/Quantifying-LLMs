Quantifying Contextual Decay and Computational Overhead in Multi-Turn LLM Inference for Interactive Software Engineering
An end-to-end quantitative audit framework designed to evaluate and profile the multi-turn inference dynamics, semantic context degradation, Key-Value (KV) cache expansion, and computational throughput across frontier causal language decoders (ChatGPT, Claude, and Gemini) within iterative software engineering workflows.
Prevailing evaluation suites (HumanEval, MBPP) evaluate language models almost exclusively under static, memoryless, single-turn prompts. This repository operationalizes a multi-phase benchmarking harness that tracks the transition from high-level architectural specification (Phase 1, T 
1
​	
 ) to low-level algorithmic implementation and refactoring (Phase 2, T 
2
​	
 ). It formalizes an auditable, Pareto-optimal Overall Performance Index (OPI) via Multi-Criteria Decision Analysis (MCDA) backed by an auditable 4-tier concentric topological knowledge network.
📌 Key Highlights
Dynamic Multi-Turn Harness: Tracks cumulative operational degradation and contextual drift across sequential prompt transitions (T 
1
​	
 →T 
2
​	
 ) rather than isolated single-turn prompts.
Multi-Dimensional Metrics: Measures token expansion factors (κ), dense cosine semantic retention (R 
1→2
​	
 ), cross-entropy reference perplexity drift (ΔP 
c
​	
 ), and real hardware execution throughput (Θ).
Pareto-Optimal Decision Engine (OPI): Unifies fragmented single-dimensional evaluations (e.g., speed vs. accuracy vs. memory) into an objective, normalized scalar index via Multi-Criteria Decision Analysis (MCDA).
Topological Provenance Graph: Projects the decision Directed Acyclic Graph (DAG) into an auditable 4-tier concentric relational knowledge network to ensure transparent mathematical lineage for model selection.
🏗️ System Architecture & Workflow
┌─────────────────────────────────────────────────────────────────────────────┐
│                      Multi-Turn Evaluation Harness                          │
└──────────────────────────────────────┬──────────────────────────────────────┘
                                       │
                    ┌──────────────────┴──────────────────┐
                    ▼                                     ▼
        [ Turn 1: Architecture (T1) ]          [ Turn 2: Algorithmic (T2) ]
        High-level schema, interfaces,         Low-level code continuation,
        system constraints                     refactoring & optimization
                    │                                     │
                    └──────────────────┬──────────────────┘
                                       │
                                       ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                    Operational Degradation Profiling                        │
│  • Token Expansion Factor:          κ = τ_2 / τ_1                           │
│  • Dense Semantic Retention:        R_{1→2} = cos(e_1, e_2)                 │
│  • Reference Perplexity Shift:      ΔP_c = P_c(T_2) - P_c(T_1)              │
│  • Decoding Throughput:             Θ = tokens / second                     │
│  • Wall-Clock Compute Latency:      t_infer (seconds)                       │
└──────────────────────────────────────┬──────────────────────────────────────┘
                                       │
                                       ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│              Pareto-Optimal Multi-Criteria Decision Analysis (MCDA)         │
│  • Objective weight vector calculation across operational trade-offs        │
│  • Concentric 4-tier Relational Topological Knowledge Graph projection      │
│  • Overall Performance Index (OPI) formulation & ranking                    │
└─────────────────────────────────────────────────────────────────────────────┘
Phase 1: Multi-Turn Conversation Sampling (T 
1
​	
 →T 
2
​	
 )
Simulates iterative developer interactions moving from architectural schema definitions (T 
1
​	
 ) to low-level algorithmic code synthesis and unit testing (T 
2
​	
 ).
Phase 2: Contextual Drift & Computational Profiling
Extracts token expansion rates (κ), dense contextual cosine similarity (R 
1→2
​	
 ), external cross-entropy reference perplexity drift (ΔP 
c
​	
 ), wall-clock latency, and token generation throughput (Θ).
Phase 3: MCDA & Concentric Topological Mapping
Synthesizes multidimensional attributes into the Overall Performance Index (OPI), mapping the computational DAG into an auditable concentric network that guarantees explainability for enterprise model deployment.
📊 Benchmark Summary
1. Multi-Turn Inference & Semantic Dynamics Across Frontier Decoders
Evaluated Decoder	Task Accuracy (%)	Semantic Retention (R 
1→2
​	
 )	Token Expansion (κ)	Ref. Perplexity (P 
c
​	
 )	Latency (s)	Throughput (Θ)	Overall Performance Index (OPI)	Pareto Rank
ChatGPT	73.2%	93.0%	1.25×	62.2	14.21 s	38.4 tok/s	83.94 / 100	Rank 1
Claude	68.4%	88.5%	1.48×	74.8	10.93 s	41.2 tok/s	76.51 / 100	Rank 2
Gemini	64.1%	81.2%	1.82×	88.1	16.54 s	45.8 tok/s	69.18 / 100	Rank 3
2. Key Empirical Findings
The Pareto-Optimal Frontier: While Gemini achieves the highest raw decoding speed (Θ=45.8 tokens/s) and Claude minimizes total execution time (10.93 s), ChatGPT defines the Pareto frontier (OPI = 83.94, Rank 1) by balancing high semantic fidelity (R 
1→2
​	
 =93.0%), bounded token bloating (κ≈1.25×), and minimal perplexity degradation (P 
c
​	
 =62.2).
KV-Cache Bloating & Continuation Costs: Unconstrained continuation expansion in extended dialogues leads to disproportionate memory pressure on backend KV-caches, demonstrating that single-turn benchmarks fail to reflect operational serving costs in production developer environments.
📁 Repository Structure
.
├── notebooks/
│   └── Quantifying_LLMs.ipynb       # Interactive Colab audit harness & profiling
├── src/
│   ├── benchmark_harness.py        # Multi-turn conversation prompt runner
│   ├── metrics.py                  # Token expansion (κ), semantic retention (R), ΔPc
│   ├── mcda_engine.py              # Multi-Criteria Decision Analysis & OPI calculator
│   └── topological_graph.py        # 4-tier concentric relational DAG visualizer
├── data/
│   └── prompt_suites/              # Two-turn architectural-to-algorithmic benchmark tasks
├── figures/                        # Generated Pareto frontiers, trade-off plots & DAGs
├── requirements.txt                # Python dependencies
└── README.md                       # Research & implementation documentation
🚀 Getting Started
Prerequisites
Python 3.9+
API keys for target decoders (OpenAI, Anthropic, Google Cloud Vertex / AI Studio)
Installation
Bash
# Clone the repository
git clone https://github.com/<your-username>/Quantifying-LLMs-MultiTurn-Inference.git
cd Quantifying-LLMs-MultiTurn-Inference

# Install required dependencies
pip install -r requirements.txt
Running the Multi-Turn Audit
To run the automated two-phase evaluation pipeline across models:
Bash
python -m src.benchmark_harness \
    --models chatgpt claude gemini \
    --prompt_suite data/prompt_suites/software_engineering_tasks.json \
    --output_dir results/
To compute the Multi-Criteria Decision Analysis (MCDA) and generate the OPI ranking:
Bash
python -m src.mcda_engine --input results/metrics_summary.json --plot_dag
🔗 Interactive Reproduction
Google Colab Notebook: Quantifying LLMs.ipynb
