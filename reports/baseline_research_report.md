# AI for Protein Function Prediction Using Traditional Machine Learning

## 1. Introduction

Proteins perform important functions in living organisms. Their amino acid sequences contain information about their biological roles. Predicting protein function from these sequences is an important task in computational biology.

This project explores how traditional machine learning can predict protein functions using amino acid composition features. The project uses data from the CAFA 5 dataset and a Logistic Regression classification model.

## 2. Research Objective

The objective is to build and evaluate a traditional machine learning baseline for protein function prediction.

The project focuses on the following question:

**How effectively can amino acid composition features predict selected Gene Ontology (GO) terms using Logistic Regression?**

## 3. Dataset

This project uses the CAFA 5 protein function prediction dataset.

The training data contains:
- 142,246 unique protein sequences.
- 5,363,863 protein function annotation records.
- 31,466 unique Gene Ontology terms.

For this baseline experiment, 47 GO terms were selected after filtering for terms with at least 100 annotated proteins and removing three root terms.

## 4. Methodology

### 4.1 Feature Extraction

Each protein sequence was converted into 20 numerical features representing the relative frequency of the 20 standard amino acids.

This approach is called amino acid composition.

### 4.2 Label Preparation

A binary label matrix was created for the selected 47 GO terms. Each protein was assigned a value of 1 if it had a particular GO annotation and 0 otherwise.

### 4.3 Train-Test Split

The dataset was divided into:
- Training set: 113,796 proteins.
- Testing set: 28,450 proteins.

An 80/20 split was used with a random state of 42.

### 4.4 Model Training

A Logistic Regression model was trained using a One-vs-Rest classification strategy to handle multiple GO-term predictions.

Class weighting was used to help address differences in the number of positive and negative examples.

## 5. Results

The model achieved the following evaluation scores:

| Metric | Score |
|---|---:|
| Micro F1 | 0.3891 |
| Macro F1 | 0.3655 |
| Micro Precision | 0.2913 |
| Micro Recall | 0.5856 |
| Macro Average Precision | 0.2894 |
| Micro Average Precision | 0.2865 |

The results show that the model identified a portion of the actual positive protein function labels, but its precision remained relatively low.

## 6. Discussion

The baseline demonstrates that amino acid composition features contain some useful information for predicting protein functions.

However, amino acid composition only captures the frequency of amino acids. It does not preserve their order or fully represent more complex sequence patterns.

The model's recall was higher than its precision, suggesting that it identified more actual positive labels but also produced many incorrect positive predictions.

These limitations provide opportunities to explore more advanced protein sequence representations.

## 7. Conclusion

This project established a traditional machine learning baseline for protein function prediction using the CAFA 5 dataset.

The experiment included dataset exploration, feature extraction, label preparation, Logistic Regression training, and model evaluation.

The baseline provides a foundation for future experiments comparing traditional machine learning features with pretrained protein language model representations.

## 8. Future Work

Future improvements may include:

- Exploring pretrained protein language models such as ESM-2.
- Comparing amino acid composition with learned protein sequence representations.
- Testing additional machine learning models.
- Evaluating performance across different Gene Ontology categories.
- Improving prediction performance through model and threshold tuning.