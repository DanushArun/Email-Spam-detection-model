# Spam Classification — Evaluation guide

Start with the smallest path that exercises the project. Distinguish source inspection,
syntax/build checks, functional behavior and domain validation when recording a result.

## Guided reading and demonstration

1. **Supply the input data.** The required CSV files are not tracked. Obtain an authorized copy
with the expected schema and replace the author-specific absolute paths before execution.

2. **Inspect the preparation.** TF-IDF is fitted on the training text. Review the transformations
and exclusions before rerunning; an output cannot be understood separately from its input
preparation.

3. **Run the experiment.** The implemented method is TF-IDF plus four classifiers. The CSV is read
with Latin-1 encoding and renamed columns. Execute in a fresh kernel to reveal ordering and
dependency problems.

4. **Read the diagnostics.** Saved SVC accuracy is 0.976682, precision 0.992063 and recall
0.833333. Precision and recall describe different errors; neither is implied by accuracy.
RandomForest has no fixed seed; compare saved outputs with a fresh run before relying on them.

## Declared checks

These commands/checks describe the intended verification path. Their presence in this
guide does not claim that they passed. See the dated evidence below and the README for setup.

```text
Parse notebook JSON and nonempty Python cells without execution.
```

## Evidence levels

| Level | What it establishes | What it does not establish |
| --- | --- | --- |
| Source review | A path exists in tracked code | Successful runtime behavior |
| Syntax/build | Parser/compiler accepts that path | End-to-end correctness |
| Behavioral check | A specific input/output case passed | Generalization beyond cases |
| Domain evaluation | Performance on a stated target setting | Other users/data/environments |

## What to record

- Commit, environment, dependency versions and date.
- Input provenance and whether data is synthetic, public or privately supplied.
- Absolute pass/fail/skip counts; keep failed cases and their root causes.
- Whether external services, hardware or a production deployment were actually exercised.
- Expected output and an artifact showing the observation.

## Review scenarios

- **Inputs are explicit:** message text, spam/ham training label.

- **Method is inspectable:** TF-IDF plus four classifiers is the implemented method; no broader
modeling capability is inferred.

- **Historical evidence is labeled:** Saved SVC accuracy is 0.976682, precision 0.992063 and
recall 0.833333. Precision and recall describe different errors; neither is implied by accuracy.

## Documentation inspection — 7 October 2026

The documentation was traced to committed source and checked for local links, balanced
code fences and supported implementation claims. Historical notebook outputs remain labeled
as historical. Live provider access, private databases and hardware behavior are not inferred
from configuration or dependency files. Any fresh run is recorded separately in the README.

## Next evidence to collect

- Supply data provenance and a reproducible local path.
- Record a fresh-kernel run with package versions.
- Evaluate stability across independent samples before widening any performance claim.
