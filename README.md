# My Graph Doesn't Help!

Code and data for:

**My Graph Doesn’t Help! Analyzing Causal Graph Construction, Representation, and Utility in LLMs**

Aman Syed and Benjamin Li

NeurIPS 2026 Workshop Paper.

## Overview

This repository contains the code and data used to study whether explicit causal graphs improve downstream reasoning in large language models.

The project contains two studies:

- **Study 1 — CausalProbe:** compares direct LLM reasoning against reasoning augmented with a target-centered causal SubGraph.
- **Study 2 — Controlled Structural Causal Reasoning:** evaluates Baseline, ground-truth graphs, FullGraph construction, QuickGraph construction, and causal-role annotations across a controlled 32-context benchmark.

## Repository Structure

```text
my-graph-doesnt-help/
├── data/
│   └── study2/
│       ├── causal_reasoning_dataset_cleaned_v2.json
│       ├── causal_reasoning_dataset_shuffled_v1.json
│       └── handmade_true_dags.json
│
├── notebooks/
│   ├── study1_preprocessing.ipynb
│   └── study2_experiments.ipynb
│
└── src/
    └── study1_subgraph.py
```

## Study 1

Study 1 uses the hard portion of **CausalProbe-2024**.

`notebooks/study1_preprocessing.ipynb` performs preprocessing and causal-variable extraction for the CausalProbe data.

`src/study1_subgraph.py` contains the SubGraph construction procedure, direct baseline prompting, graph-assisted reasoning, and model evaluation code.

The original CausalProbe dataset is not redistributed in this repository.

## Study 2

Study 2 contains 32 contexts covering eight causal graph topologies, with five questions per context for a total of 160 questions.

The files are:

- `causal_reasoning_dataset_cleaned_v2.json` — reference version of the benchmark.
- `causal_reasoning_dataset_shuffled_v1.json` — answer-choice-shuffled version used in the reported experiments.
- `handmade_true_dags.json` — ground-truth causal graphs used for reconstruction evaluation.
- `study2_experiments.ipynb` — FullGraph, QuickGraph, Baseline, Truth, annotation, evaluation, and statistical-analysis pipeline.

## Models

Experiments evaluate:

- GPT-4o
- GPT-4o-mini
- Claude Sonnet 4.5
- Llama 3.3 70B Instruct
- Llama 3.1 8B Instruct

Models were accessed through OpenRouter with fixed provider routing.

## Reproduction

API credentials are not included in this repository.

Set your own OpenRouter API key before running the experiment code.

Study 1 requires obtaining the CausalProbe dataset separately and running the preprocessing notebook before executing the SubGraph experiments.

For Study 2, use:

```text
data/study2/causal_reasoning_dataset_shuffled_v1.json
data/study2/handmade_true_dags.json
```

with `notebooks/study2_experiments.ipynb`.

## Citation

If you use this repository, please cite:

```text
Syed, Aman and Li, Benjamin.
"My Graph Doesn't Help! Analyzing Causal Graph Construction,
Representation, and Utility in LLMs."
NeurIPS 2026 Workshop Paper.
```
