# Spam Detection — TF-IDF Classifier Comparison

> Compare four text classifiers on one recorded split; distinguish saved scores from a fresh run.

[Task_4.ipynb](Task_4.ipynb) labels messages as `ham` or `spam`. It prepares a CSV, fits a TF-IDF
vocabulary on training messages, evaluates Multinomial Naive Bayes, and compares logistic
regression,
a support-vector classifier and a random forest. No mail-server integration or deployed API is
built.

## Inspect and reproduce

The notebook's saved outputs can be read directly on GitHub. For local execution:

```sh
python3 -m venv .venv
.venv/bin/python -m pip install jupyterlab pandas matplotlib seaborn scikit-learn
.venv/bin/python -m jupyter lab Task_4.ipynb
```

Obtain the matching `spam.csv` separately; it is not committed. Replace the notebook's local
`file_path` before running all cells. The loader uses Latin-1 encoding and expects `v1`, `v2` and
three `Unnamed` columns, which are dropped before renaming to `label` and `message`.
Package versions are unpinned; no exact historical environment is provided.

## Pipeline and recorded results

`CSV → label/message cleanup → 80/20 split → training-only TF-IDF → classifiers → metrics/charts`.
The split uses `random_state=42`: **4,457 training and 1,115 test messages** in the saved run.

| Classifier | Accuracy | Spam precision | Spam recall | Spam F1 |
|---|---|---|---|---|
| Multinomial Naive Bayes | 0.9668 | 1.0000 | 0.7533 | 0.8593 |
| Logistic regression | 0.9525 | 0.9709 | 0.6667 | 0.7905 |
| Support-vector classifier | 0.9767 | 0.9921 | 0.8333 | 0.9058 |
| Random forest | 0.9740 | 0.9919 | 0.8133 | 0.8938 |

These are saved outputs inspected on **7 October 2026**, not newly executed measurements.
Naive Bayes has high recorded precision but misses some spam: precision and recall answer
different questions. Comparing several models on the same test set is not a separate final
held-out assessment.

## What is built, and what is missing

Built: preprocessing, sparse text features, four classifier fits, metrics and comparison plots.
Missing: supplied CSV, locked environment, persisted pipeline, automated tests, independent
validation, drift monitoring and email integration. The random forest does not pin its random seed.

The data is message text; the repository name does not prove email-specific performance.
Dataset provenance/licensing and class-level error analysis remain necessary before wider reuse.
Saved accuracy does not establish reliable performance on new senders, languages or spam campaigns.
