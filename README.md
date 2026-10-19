Quantifying Contextual Decay and Computational Overhead in Multi-Turn LLM Inference for Interactive Software Engineering
An end-to-end quantitative audit framework designed to evaluate and profile multi-turn inference dynamics, semantic context degradation, Key-Value (KV) cache expansion, and computational throughput across frontier causal language decoders (ChatGPT, Claude, and Gemini) within iterative software engineering workflows.
Prevailing evaluation suites (HumanEval, MBPP) evaluate language models almost exclusively under static, memoryless, single-turn prompts. This repository operationalizes a multi-phase benchmarking harness that tracks the transition from high-level architectural specification (Phase 1, T1) to low-level algorithmic implementation and refactoring (Phase 2, T2). It formalizes an auditable, Pareto-optimal Overall Performance Index (OPI) via Multi-Criteria Decision Analysis (MCDA) backed by an auditable 4-tier concentric topological knowledge network.
Key Highlights
Dynamic Multi-Turn Harness: Tracks cumulative operational degradation and contextual drift across sequential prompt transitions (T1 to T2) rather than isolated single-turn prompts.
Multi-Dimensional Metrics: Measures token expansion factors, dense cosine semantic retention, cross-entropy reference perplexity drift, and real hardware execution throughput.
Pareto-Optimal Decision Engine (OPI): Unifies fragmented single-dimensional evaluations (speed vs. accuracy vs. memory) into an objective, normalized scalar index via Multi-Criteria Decision Analysis (MCDA).
Topological Provenance Graph: Projects the decision Directed Acyclic Graph (DAG) into an auditable 4-tier concentric relational knowledge network to ensure transparent mathematical lineage for model selection.
System Architecture and Workflow
Phase 1: Multi-Turn Conversation Sampling (T1 to T2)
Simulates iterative developer interactions moving from architectural schema definitions (T1) to low-level algorithmic code synthesis and unit testing (T2).
Phase 2: Contextual Drift and Computational Profiling
Extracts token expansion rates, dense contextual cosine similarity, external cross-entropy reference perplexity drift, wall-clock latency, and token generation throughput.
Phase 3: MCDA and Concentric Topological Mapping
Synthesizes multidimensional attributes into the Overall Performance Index (OPI), mapping the computational DAG into an auditable concentric network that guarantees explainability for enterprise model deployment.
Benchmark Summary
1. Multi-Turn Inference Dynamics Across Frontier Decoders
ChatGPT:
Task Accuracy: 73.2%
Semantic Retention: 93.0%
Token Expansion: 1.25x
Reference Perplexity: 62.2
Latency: 14.21 s
Throughput: 38.4 tokens/s
Overall Performance Index (OPI): 83.94 / 100
Pareto Rank: Rank 1
Claude:
Task Accuracy: 68.4%
Semantic Retention: 88.5%
Token Expansion: 1.48x
Reference Perplexity: 74.8
Latency: 10.93 s
Throughput: 41.2 tokens/s
Overall Performance Index (OPI): 76.51 / 100
Pareto Rank: Rank 2
Gemini:
Task Accuracy: 64.1%
Semantic Retention: 81.2%
Token Expansion: 1.82x
Reference Perplexity: 88.1
Latency: 16.54 s
Throughput: 45.8 tokens/s
Overall Performance Index (OPI): 69.18 / 100
Pareto Rank: Rank 3
2. Key Empirical Findings
The Pareto-Optimal Frontier: While Gemini achieves the highest raw decoding speed (45.8 tokens/s) and Claude minimizes total execution time (10.93 s), ChatGPT defines the Pareto frontier (OPI = 83.94, Rank 1) by balancing high semantic fidelity (93.0%), bounded token expansion (1.25x), and minimal perplexity degradation (62.2).
KV-Cache Bloating: Unconstrained continuation expansion in extended dialogues leads to disproportionate memory pressure on backend KV-caches, demonstrating that single-turn benchmarks fail to reflect operational serving costs in production developer environments.
Repository Structure
notebooks/ : Contains interactive Colab audit harness and profiling notebooks.
src/ : Core source code including benchmark harness, metrics calculator, MCDA engine, and topological graph generator.
data/ : Two-turn architectural-to-algorithmic benchmark task prompt suites.
figures/ : Generated Pareto frontiers, trade-off plots, and DAG visual outputs.
requirements.txt : Project Python dependencies.
README.md : Main project documentation.
Getting Started
Prerequisites
Python 3.9+
API keys for target decoders (OpenAI, Anthropic, Google Cloud Vertex / AI Studio)
Installation
Clone the repository and install required packages:
pip install -r requirements.txt
Running the Pipeline
Run the automated two-phase evaluation pipeline across models:
python -m src.benchmark_harness --models chatgpt claude gemini --prompt_suite data/prompt_suites/software_engineering_tasks.json --output_dir results/
Compute the Multi-Criteria Decision Analysis (MCDA) and generate the OPI ranking:
python -m src.mcda_engine --input results/metrics_summary.json --plot_dag
Interactive Reproduction
Run directly in Google Colab:
https://colab.research.google.com/drive/1QkwQfBJKK6J-WIR3rNYmbEVclH6b8Vmi
