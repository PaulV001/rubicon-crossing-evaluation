# Rubicon Crossing Evaluation

**A source-grounded LLM evaluation benchmark for testing multi-document reasoning, source criticism, contradiction handling, and calibrated judgment.**

This project transforms a historical research problem — whether Julius Caesar's crossing of the Rubicon in 49 BCE was legally and politically justified — into a structured evaluation task for large language models.

Rather than testing factual recall, the benchmark requires a model to synthesize evidence from multiple primary sources, distinguish legal from political justification, reconcile conflicting accounts, assess source provenance and bias, and produce a defensible source-grounded judgment.

## What This Project Demonstrates

This repository demonstrates an end-to-end approach to designing an LLM evaluation:

- **Dataset construction** — selected primary-source evidence transformed into structured CSV datasets
- **Prompt design** — a constrained task requiring cross-document synthesis rather than retrieval
- **Rubric design** — ten criteria evaluating extraction, reasoning, synthesis, source criticism, and judgment
- **Dependency-aware evaluation** — later analytical criteria build on evidence established in earlier criteria
- **Golden-response design** — a reference answer demonstrating the expected reasoning process
- **Source provenance** — evidence remains traceable to publicly verifiable editions of the underlying texts
- **Evaluation methodology** — documentation explaining the design principles and intended model behaviors

## Evaluation Architecture

```text
Primary Sources
      │
      ▼
Structured Evidence (CSV)
      │
      ▼
Source-Grounded Prompt
      │
      ▼
10-Criterion Evaluation Rubric
      │
      ▼
Golden Reference Response
      │
      ▼
Model Evaluation
