# Source Data

This directory contains structured extracts from four ancient sources relevant to Julius Caesar's crossing of the Rubicon and the political crisis of 49 BCE.

| Dataset | Ancient Source | Web Edition |
|---|---|---|
| `A_Caesar_Civil_Wars_MIT.csv` | Julius Caesar, *Civil War* 1.5–1.7 | MIT Classics |
| `B_Plutarch_Caesar_Gutenberg.csv` | Plutarch, *Life of Caesar* 32 | Project Gutenberg |
| `C_Suetonius_Julius_Lexundria.csv` | Suetonius, *Life of Julius Caesar* 29–31 | Lexundria |
| `D_Cicero_Ad_Atticum.csv` | Cicero, *Letters to Atticus*, Book 7 | Public online edition |

## Dataset Design

The CSV files transform selected primary-source passages into structured evidence for an LLM evaluation task. Fields identify the author, work, section, source location, evidence summary, and analytical relevance of each passage.

The datasets are not intended to replace the primary texts. They provide a controlled evidence packet that requires the evaluated model to compare claims across sources rather than answer the historical question from general knowledge.

## Source Selection

The four authors provide deliberately different evidentiary perspectives:

- **Caesar** provides the participant's own justification of his actions.
- **Plutarch** provides a later biographical account emphasizing Caesar's deliberation at the Rubicon.
- **Suetonius** preserves competing explanations for Caesar's motives.
- **Cicero** provides contemporary correspondence from a Roman political actor attempting to assess the crisis as it unfolded.

These differences allow the evaluation to test source criticism, contradiction handling, and cross-document synthesis.
