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
```

The architecture deliberately separates **evidence**, **task specification**, **evaluation criteria**, and **reference reasoning**. This makes individual model failures easier to diagnose than a simple correct/incorrect score.

## The Evaluation Task

The central question is:

> **Was Caesar's crossing of the Rubicon legally and politically justified?**

The task requires the evaluated model to distinguish two related but non-identical questions:

1. Whether Caesar possessed sufficient **legal or constitutional justification** for military action.
2. Whether the circumstances provided sufficient **political justification** for his decision.

No individual source provides the complete answer. The model must construct its judgment by comparing claims across the evidence packet.

## Source Dataset

The evaluation uses structured extracts from four ancient sources representing deliberately different evidentiary perspectives:

| Source | Evidentiary Role |
|---|---|
| Julius Caesar, *Civil War* | Caesar's own account and justification of his actions |
| Plutarch, *Life of Caesar* | Later biographical account emphasizing deliberation and escalation |
| Suetonius, *Life of Julius Caesar* | Later biographical tradition preserving competing explanations of Caesar's motives |
| Cicero, *Letters to Atticus* | Contemporary correspondence from a Roman political participant observing the crisis |

The source diversity creates a realistic reasoning problem: the sources differ in proximity to events, purpose, perspective, interests, and evidentiary value.

## What the Rubric Tests

The ten-criterion rubric evaluates whether a model can:

- identify Caesar's stated grievances;
- corroborate claims across independent accounts;
- recognize evidence that complicates Caesar's own narrative;
- identify plausible alternative motives;
- evaluate whether negotiation remained possible;
- distinguish source provenance and evidentiary limitations;
- separate legitimate grievances from justified remedies;
- reach defensible legal and political judgments; and
- synthesize conflicting evidence rather than produce a binary verdict unsupported by the source packet.

The rubric therefore evaluates the **reasoning process leading to the conclusion**, not merely whether the model happens to reach the same final judgment as the reference answer.

## Repository Structure

```text
rubicon-crossing-evaluation/
├── README.md
├── LICENSE
├── data/
│   ├── A_Caesar_Civil_Wars_MIT.csv
│   ├── B_Plutarch_Caesar_Gutenberg.csv
│   ├── C_Suetonius_Julius_Lexundria.csv
│   ├── D_Cicero_Ad_Atticum.csv
│   └── README.md
├── evaluation/
│   ├── prompt.md
│   ├── rubric.md
│   └── golden_response.md
└── docs/
    └── methodology.md
```

### [`data/`](data/)

Structured source evidence used by the evaluation.

### [`evaluation/prompt.md`](evaluation/prompt.md)

The source-grounded task presented to the evaluated model.

### [`evaluation/rubric.md`](evaluation/rubric.md)

The ten-criterion evaluation framework, including source requirements, rationales, criterion types, weights, and dependencies.

### [`evaluation/golden_response.md`](evaluation/golden_response.md)

A reference response demonstrating one defensible synthesis of the evidence.

### [`docs/methodology.md`](docs/methodology.md)

Design rationale covering source selection, cross-document reasoning, source criticism, rubric construction, and evaluation philosophy.

## Design Principle

The benchmark is intentionally constructed so that **retrieving isolated facts is insufficient**.

A strong response must perform a chain of operations:

**extract → compare → corroborate → contextualize → evaluate provenance → distinguish grievance from remedy → synthesize → judge**

This structure adapts methods familiar from historical source criticism to contemporary LLM evaluation. Conflicting testimony is treated not as noise to be eliminated, but as evidence whose provenance, perspective, and relationship to other evidence must be evaluated.

## Portfolio Context

This is an independent portfolio project demonstrating the application of historical research methodology to AI evaluation and dataset design.

The project was designed to showcase transferable skills in:

**LLM evaluation · rubric design · dataset curation · prompt design · source-grounded reasoning · knowledge organization · provenance analysis · quality assurance**

## License and Source Notice

Original evaluation materials and documentation are provided under the terms described in [`LICENSE`](LICENSE).

Underlying ancient texts, translations, editions, and other third-party source materials remain subject to their respective copyright, public-domain, licensing, and attribution terms.
