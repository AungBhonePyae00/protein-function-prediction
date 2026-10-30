# AI for Protein Function Prediction Using Traditional Machine Learning

A reproducible baseline study exploring how well amino acid composition features can predict selected Gene Ontology (GO) terms from protein sequences.

## Research question

**How effectively can amino acid composition features predict selected GO terms using Logistic Regression?**

## Project summary

This project uses the CAFA 5 protein function prediction dataset. Each protein sequence is represented by the relative frequencies of the 20 standard amino acids. A One-vs-Rest Logistic Regression model predicts 47 selected GO terms.

| Dataset detail | Value |
|---|---:|
| Unique protein sequences | 142,246 |
| Selected GO terms | 47 |
| Training proteins | 113,796 |
| Test proteins | 28,450 |
| Sequence features | 20 |

## Baseline results

| Metric | Score |
|---|---:|
| Micro F1 | 0.3891 |
| Macro F1 | 0.3655 |
| Micro Precision | 0.2913 |
| Micro Recall | 0.5856 |
| Macro Average Precision | 0.2894 |
| Micro Average Precision | 0.2865 |

### Visual results

**Overall model performance**

![Baseline metrics](results/baseline_metrics_chart.png)

**Top 10 GO terms by F1 score**

![Top 10 GO terms](results/top_10_go_terms.png)

## Method

1. Explore the CAFA 5 training annotations and protein sequences.
2. Convert each sequence into 20 amino acid composition features.
3. Build a binary target matrix for 47 selected GO terms.
4. Split the data into training and test sets (80/20, random state 42).
5. Train One-vs-Rest Logistic Regression with class weighting.
6. Evaluate predictions using F1, precision, recall, and average precision.

## Repository contents

- [Data exploration and baseline notebook](notebooks/01_data_exploration.ipynb) — data exploration, feature preparation, baseline modeling, and evaluation.
- [Baseline research report](reports/baseline_research_report.md) — research report and interpretation.
- [Overall evaluation metrics](results/baseline_metrics.csv).
- [Per-GO-term evaluation metrics](results/baseline_per_term_metrics.csv).
- [Overall metric visualization](results/baseline_metrics_chart.png).
- [Top GO terms visualization](results/top_10_go_terms.png).

## Reproducing the experiment

1. Clone this repository.
2. Obtain the CAFA 5 training data separately; raw dataset files are not included in this repository.
3. Place the training files in data/raw/cafa5/Train/, including train_sequences.fasta, train_terms.tsv, and go-basic.obo.
4. Open and run the notebook in notebooks/ from top to bottom. The notebook expects the project folder to be its parent directory.

The experiment uses Python with pandas, NumPy, scikit-learn, Matplotlib, and Biopython.

## Interpretation and limitations

The baseline's recall (0.5856) is higher than its precision (0.2913), meaning it retrieves a portion of the positive labels but also produces false-positive predictions. Amino acid composition captures how often amino acids occur, but discards their order and other sequence patterns. The results should therefore be treated as a baseline, not as a state-of-the-art protein function predictor.

## Future work

- Compare the baseline with pretrained protein language model representations such as ESM-2.
- Evaluate additional traditional machine learning models.
- Investigate threshold tuning and performance across GO categories.

**Note:** ESM-2 experiments are planned future work and have not yet been completed.

## Technologies

Python · pandas · NumPy · scikit-learn · Matplotlib · Biopython · Jupyter Notebook

## Research report

[Read the full baseline research report](reports/baseline_research_report.md)
