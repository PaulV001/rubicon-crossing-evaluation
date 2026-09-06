# Rubicon Crossing Evaluation

A source-grounded LLM evaluation task designed to test historical reasoning across conflicting primary accounts of Julius Caesar's crossing of the Rubicon in 49 BCE.

## Overview

This project demonstrates the design of a structured prompt–rubric evaluation using methods from historical source criticism and LLM evaluation.

Rather than testing factual recall, the task requires a model to synthesize evidence from multiple primary sources, distinguish legal from political justification, reconcile conflicting accounts, evaluate competing explanations of Caesar's motives, and produce a source-grounded judgment.

The evaluation packet uses structured extracts from:

- Julius Caesar, *Civil War*
- Plutarch, *Life of Caesar*
- Suetonius, *Life of Julius Caesar*
- Cicero, *Letters to Atticus*

## Evaluation Design

The project consists of four components:

1. **Source dataset** — structured extracts from primary sources
2. **Prompt** — a source-grounded historical reasoning task
3. **Rubric** — criteria covering extraction, synthesis, source criticism, and reasoning
4. **Golden response** — a reference answer demonstrating the expected reasoning process

The central evaluation question is:

> **Was Caesar's crossing of the Rubicon legally and politically justified?**

The task deliberately requires synthesis rather than simple retrieval. No individual source provides the answer. The model must reconcile Caesar's self-justification with competing ancient accounts and contemporary evidence.

## Repository Structure

```text
rubicon-crossing-evaluation/
├── README.md
├── LICENSE
├── data/
│   ├── A_Caesar_Civil_Wars_MIT.csv
│   ├── B_Plutarch_Caesar_Gutenberg.csv
│   ├── C_Suetonius_Julius_Lexundria.csv
│   └── D_Cicero_Ad_Atticum.csv
├── evaluation/
│   ├── prompt.md
│   ├── rubric.md
│   └── golden_response.md
└── docs/
    └── methodology.md
