# Methodology

## Purpose

This project demonstrates the design of a source-grounded LLM evaluation task using methods derived from historical research, source criticism, and structured rubric design.

The evaluation asks a model to determine whether Julius Caesar's crossing of the Rubicon in 49 BCE was legally/constitutionally and politically justified.

The task is deliberately designed so that the answer cannot be obtained by extracting a single fact from one document. Instead, the model must synthesize conflicting and differently situated primary sources, assess their evidentiary value, distinguish factual corroboration from interpretive agreement, and produce a calibrated historical judgment.

## Evaluation Philosophy

Historical reasoning provides a useful framework for evaluating large language models because historical questions frequently involve incomplete evidence, conflicting testimony, uncertain motives, source bias, and competing interpretations.

A strong response therefore requires more than factual recall.

The model must demonstrate several distinct capabilities:

- evidence extraction
- cross-document synthesis
- contradiction handling
- source and provenance evaluation
- temporal and contextual reasoning
- distinction between evidence and inference
- calibrated judgment under uncertainty

The rubric converts these capabilities into individually evaluable criteria.

## Source Selection

The evaluation packet uses four ancient sources:

1. **Julius Caesar, _Civil War_**
2. **Plutarch, _Life of Caesar_**
3. **Suetonius, _Life of Julius Caesar_**
4. **Cicero, _Letters to Atticus_**

These sources were selected because they occupy different evidentiary positions relative to the crisis.

### Caesar

Caesar was a principal participant in the events and provides the clearest surviving account of his stated political and constitutional grievances.

His proximity to the events gives his account substantial evidentiary value, but his status as an interested participant creates an obvious incentive for self-justification.

### Cicero

Cicero's private correspondence provides contemporary evidence from another participant in Roman political life.

Because the letters were written while events were unfolding rather than as a retrospective narrative of the civil war, they preserve uncertainty, changing assessments, rumors, negotiations, and contemporary perceptions.

Cicero nevertheless had his own political interests and did not possess complete information.

### Plutarch

Plutarch wrote substantially later than the events but preserves traditions concerning Caesar's political conflict, deliberation, and decision to cross the Rubicon.

His account is particularly useful for comparison with Caesar's self-presentation, although chronological distance and the literary conventions of ancient biography require caution when evaluating reconstructed motives, speeches, and dramatic scenes.

### Suetonius

Suetonius likewise provides a later biographical account and preserves multiple explanations for Caesar's actions.

His presentation is useful for evaluating competing traditions concerning Caesar's motives, including constitutional grievances, fear of prosecution, political status, and personal ambition.

The purpose of using these four sources is not to treat them as four equally independent witnesses. Instead, the task requires the model to evaluate differences in provenance, purpose, proximity, genre, and evidentiary value.

## Structured Source Data

Relevant passages from the primary sources are represented in four CSV datasets:

- `A_Caesar_Civil_Wars_MIT.csv`
- `B_Plutarch_Caesar_Gutenberg.csv`
- `C_Suetonius_Julius_Lexundria.csv`
- `D_Cicero_Ad_Atticum.csv`

The CSV files transform selected passages into a structured evidence packet containing source identification, textual location, evidence summaries, and analytical relevance.

This design serves two purposes.

First, it constrains the evaluation to a defined body of evidence rather than allowing the model to rely primarily on information memorized during training.

Second, it makes the evidence auditable. Claims evaluated by the rubric can be traced back to specific entries and ultimately to publicly accessible editions of the ancient texts.

The structured datasets supplement rather than replace the primary texts.

## Reasoning Architecture

The rubric follows a staged reasoning structure.

### Stage 1: Evidence Identification

The model must first identify the major pieces of evidence relevant to Caesar's justification, including:

- Caesar's stated constitutional and political grievances
- corroborating evidence from other sources
- evidence concerning the deliberate nature of the Rubicon crossing
- alternative explanations for Caesar's motives
- evidence that negotiated alternatives remained possible

These criteria test whether the model has correctly assembled the evidentiary foundation needed for subsequent analysis.

### Stage 2: Source Criticism

The model must then evaluate the evidentiary characteristics of the sources themselves.

This requires distinguishing between:

- participant testimony and later narrative
- public self-justification and private correspondence
- contemporary evidence and retrospective biography
- corroboration of events and corroboration of interpretation
- reported motives and directly observable actions

This stage prevents a simple "vote counting" approach in which agreement among several ancient authors is automatically treated as independent confirmation.

## Stage 3: Analytical Distinction

A central design feature of the evaluation is the distinction between **legitimate grievance** and **justified remedy**.

Evidence that Caesar's opponents violated political norms or treated him unfairly does not automatically establish that Caesar was legally entitled to respond by bringing troops into Italy.

The model must therefore reason across two separate questions:

1. Did Caesar possess legitimate political or constitutional grievances?
2. Did those grievances justify the remedy he ultimately chose?

This distinction forces the model to move beyond extraction and perform historical and normative reasoning.

## Stage 4: Calibrated Judgment

The prompt requires separate judgments concerning:

- legal/constitutional justification
- political justification

This prevents the model from collapsing different analytical standards into a single binary verdict.

A response may therefore conclude, for example, that Caesar possessed substantial political reasons for resisting his opponents while simultaneously concluding that those reasons did not provide an equally strong legal justification for military escalation.

The evaluation rewards judgments proportional to the strength and limitations of the available evidence rather than rhetorical certainty.

## Rubric Architecture

The ten rubric criteria form a progression from evidence extraction to synthesis.

Criteria 1–5 establish the evidentiary inputs.

Criterion 6 evaluates source provenance and evidentiary limitations.

Criterion 7 tests the distinction between grievance and remedy.

Criteria 8 and 9 require separate legal/constitutional and political judgments.

Criterion 10 evaluates the final comparative synthesis.

Dependencies are used where later analytical conclusions require earlier evidentiary or reasoning steps.

This structure makes it possible to identify not only whether a model reached an incorrect conclusion, but also **where its reasoning process failed**.

For example, two models could reach the same final judgment while differing substantially in quality. One might arrive there through careful source comparison and calibrated reasoning, while another might produce the conclusion through unsupported assertion or general historical knowledge.

The rubric is designed to distinguish between those responses.

## Golden Response

The golden response represents one defensible high-quality synthesis of the supplied evidence.

It is not intended to imply that historical interpretation can always be reduced to a single uniquely correct conclusion.

Instead, it demonstrates the expected reasoning process:

1. identify relevant evidence;
2. compare evidence across sources;
3. evaluate provenance and source limitations;
4. distinguish corroborated events from interpretations of those events;
5. consider competing explanations;
6. distinguish grievance from remedy;
7. reach separate legal and political judgments; and
8. calibrate those judgments to the strength of the evidence.

The evaluation therefore prioritizes the quality and traceability of reasoning rather than simple agreement with a predetermined historical opinion.

## Historical Method and LLM Evaluation

The project applies traditional historical research skills to modern AI evaluation.

| Historical Method | LLM Evaluation Capability |
|---|---|
| Primary-source analysis | Evidence extraction |
| Source criticism | Provenance and reliability evaluation |
| Comparing conflicting accounts | Contradiction handling |
| Corroborating testimony | Cross-document reasoning |
| Contextualization | Context-sensitive interpretation |
| Distinguishing fact from inference | Grounded reasoning |
| Evaluating competing explanations | Hypothesis comparison |
| Historiographical synthesis | Multi-source synthesis |
| Qualified historical judgment | Calibration under uncertainty |
| Citation and documentation | Traceability and auditability |

These parallels make historical analysis particularly suitable for constructing evaluations of model reasoning over complex documentary evidence.

## Limitations

This project evaluates reasoning over a deliberately bounded source packet rather than attempting to resolve the complete historiographical debate concerning the outbreak of the Roman Civil War.

The selected passages do not represent every surviving ancient source, every relevant aspect of Roman constitutional practice, or the full range of modern scholarship.

The terms "legal/constitutional justification" and "political justification" are analytical categories imposed by the evaluation design. Roman Republican political institutions did not operate through a modern codified constitutional system.

Accordingly, the project should be understood as an evaluation of **source-grounded historical reasoning**, not as an attempt to produce a definitive legal ruling on Caesar's actions.

## Design Goal

The central question of the project is not simply:

> Can an LLM tell us what happened when Caesar crossed the Rubicon?

It is:

> Can an LLM construct a defensible historical judgment from incomplete, interested, differently situated, and partially conflicting evidence — and can we evaluate that reasoning systematically?

That is the capability this rubric is designed to measure.
