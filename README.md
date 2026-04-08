# Comparative Analysis of Text Summarization and Classification Techniques

> A systematic empirical study comparing classical and neural NLP approaches across extractive summarization and topic classification — with focus on methodological transparency and cross-domain generalizability

A rigorous comparative framework evaluating modern techniques for two fundamental NLP tasks: **Extractive Text Summarization** and **Topic Classification**. Built to answer a critical question: does architectural complexity (neural networks, contextual embeddings) consistently outperform traditional baselines across different textual domains?

---

## Research Objective

**Inter-task validation** — testing whether methodological choices that work for summarization also work for classification, and vice versa. The goal is to verify the **solidity and generalizability** of design assumptions beyond single-task optimisation.

Central focus: **reproducibility**. Transparent preprocessing, uniform experimental design, and fair baseline comparisons to isolate the true impact of model architecture from confounding factors.

---

## Datasets

Two established benchmarks selected for domain coverage and literature comparability.

| Dataset | Task | Size | Domain | Use Case |
|---------|------|------|--------|----------|
| **NEWSROOM** | Summarization | 1.3M articles | News media | Extractive strategy evaluation |
| **AGNews** | Classification | 120K samples | News topics | Multi-class discrimination |

Both represent standard evaluation sets, ensuring results are directly comparable to existing literature.

---

## Methodology — Extractive Summarization

**Graph-based approach: Enhanced TextRank**

Three configurations tested:
- **Baseline** — Classical TextRank with TF-IDF sentence similarity (lexical frequency only)
- **BERT-enhanced** — TextRank with BERT contextual embeddings for semantic sentence representation
- **Hybrid** — Combined BERT semantics + TF-IDF weighting to balance context and frequency

**Evaluation:** ROUGE-1, ROUGE-2, ROUGE-L (F1-score) for lexical overlap measurement against reference summaries.

---

## Methodology — Topic Classification

Four architectures compared to isolate the effect of model complexity on discrimination performance.

| Model | Type | Optimisation Strategy |
|-------|------|----------------------|
| **1D CNN** | Neural | Early stopping, dropout regularisation |
| **Random Forest** | Ensemble | Systematic Grid Search over tree depth, estimator count |
| **Logistic Regression** | Linear | L2 regularisation |
| **Linear SVC** | Linear | Hinge loss optimisation |

**Evaluation:** Error Rate (1 − Accuracy) — chosen for direct comparison with existing classification literature.

---

## Results — Classification

| Model | Error Rate | Key Insight |
|-------|------------|-------------|
| 1D CNN | Lowest | Neural structures deliver measurable gains in complex pattern recognition |
| Random Forest | Competitive | Strong performance with inherent feature interpretability |
| Linear Models | Baseline | Efficient for high-volume production environments |

**Takeaway:** While the 1D CNN achieves the best discrimination, linear models remain viable when **computational efficiency** is the primary constraint.

---

## Results — Summarization

| Configuration | ROUGE-1 (F1) | Insight |
|---------------|--------------|---------|
| BERT-enhanced TextRank | ≈ 0.22 | Marginal improvement over baseline |
| Classical TextRank | ≈ 0.21 | Lexical frequency dominates in news domain |

**Surprising finding:** Contextual embeddings (BERT) provided only **minimal gains** for extractive news summarization. In this domain, **keyword frequency remains the dominant signal** — semantic enrichment does not universally improve extractive tasks.

This challenges the assumption that more sophisticated representations always yield better performance, particularly in domains where surface-level statistics are highly predictive.

---

## Key Contributions

- **Methodological transparency** — uniform preprocessing and hyperparameter documentation to ensure fair comparison
- **Cross-domain validation** — tested assumptions across two distinct NLP tasks rather than optimising for a single benchmark
- **Complexity vs. utility analysis** — direct evaluation of whether neural architectures justify their computational cost
- **Literature-aligned evaluation** — metrics chosen for direct comparability with existing work

---

## Limitations & Future Work

- **Abstractive summarization** — transition from extractive to generative models (T5, BART, GPT-based architectures)
- **Full Transformer architectures** — fine-tune BERT/RoBERTa for classification rather than using embeddings as features
- **Feature set expansion** — move beyond the current 200-term vocabulary constraint for richer text representations
- **Domain adaptation** — evaluate robustness across scientific, legal, and medical corpora to test cross-domain generalisation

---

## Contributors

**Federico Cesare Cattò** · **Francesco Beretta** · **Riccardo Borserini**

*MSc Data Science · Università degli Studi di Milano-Bicocca*

---

## Stack

`Python` `BERT` `Transformers` `TensorFlow/Keras` `1D CNN` `TextRank` `scikit-learn` `Random Forest` `ROUGE` `NLTK` `spaCy` `extractive summarization` `topic classification` `NLP`
