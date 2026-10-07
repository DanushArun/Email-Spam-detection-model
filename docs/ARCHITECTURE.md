# Spam Classification — Architecture and implementation

This guide follows the tracked implementation. Proposed work is identified separately.

## The problem and the system boundary

Labeled text messages provide an approachable way to inspect the relationship between inputs and
spam/ham label. This repository keeps that work in a notebook so preparation, computation and
saved outputs can be read together. Its value is an inspectable experiment, not a deployed
prediction service.

## Processing path

```mermaid
flowchart LR
    N0["Messages"]
    N1["TF-IDF"]
    N2["classifiers"]
    N3["precision/recall"]
    N0 --> N1
    N1 --> N2
    N2 --> N3
```

## End-to-end behavior

### 1. Supply the input data

The required CSV files are not tracked. Obtain an authorized copy with the expected schema and
replace the author-specific absolute paths before execution.

### 2. Inspect the preparation

TF-IDF is fitted on the training text. Review the transformations and exclusions before rerunning;
an output cannot be understood separately from its input preparation.

### 3. Run the experiment

The implemented method is TF-IDF plus four classifiers. The CSV is read with Latin-1 encoding and
renamed columns. Execute in a fresh kernel to reveal ordering and dependency problems.

### 4. Read the diagnostics

Saved SVC accuracy is 0.976682, precision 0.992063 and recall 0.833333. Precision and recall
describe different errors; neither is implied by accuracy. RandomForest has no fixed seed; compare
saved outputs with a fresh run before relying on them.

## Design choices and consequences

### Inputs are explicit

message text, spam/ham training label.

### Method is inspectable

TF-IDF plus four classifiers is the implemented method; no broader modeling capability is inferred.

### Historical evidence is labeled

Saved SVC accuracy is 0.976682, precision 0.992063 and recall 0.833333. Precision and recall
describe different errors; neither is implied by accuracy.

## Source entry points

### [Task_4.ipynb](../Task_4.ipynb)

29 nonempty Python cells are committed, along with any saved outputs.
Cell order and absolute data paths are part of reproducibility; outputs are historical.

## Implementation state

| State | Evidence boundary |
| --- | --- |
| Present | Notebook source and historical saved outputs |
| Required externally | Authorized CSV input and compatible Python packages |
| Not rerun | Data-dependent execution in this documentation pass |
| Not supplied | Deployment service, model registry or automated behavior suite |

“Present” means tracked source or assets exist. It does not mean a production or domain
validation has passed. See [Evaluation](EVALUATION.md) for reproducible checks and limits.
