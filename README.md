# A Comparative Study of Binary Sentiment Analysis on IMDB and SST-2

## Team Members
* **Cuclea Luca-Nicolae** 
* **Rizea Mihai-Marius** 
* **Dilmac Cemil-Andrei** 
* **Popa Petru**

## Project Overview
This repository contains a comprehensive benchmarking study evaluating the evolution of machine learning architectures for binary sentiment analysis. The project traces the progression of Natural Language Processing (NLP) techniques, starting from classical statistical baselines to state-of-the-art Transformer models. By analyzing performance and error patterns, we demonstrate how transitioning from frequency-based representations (like TF-IDF) to deep contextualized embeddings resolves critical limitations in capturing compositional semantics, long-range dependencies, and contextual nuance (irony, negation, contrastive shifts).

## Datasets
The models are benchmarked on two complementary datasets to evaluate their performance across different text lengths and complexities:
* **SST-2 (Stanford Sentiment Treebank):** Short, sentence-level text snippets (average 9.4 words). Tests a model's ability to infer sentiment from limited context.
* **IMDB (Large Movie Review Dataset):** Long, document-level movie reviews (average 233 words). Provides rich contextual information and tests long-range dependency tracking.

## Models Implemented
The project is structured into four evolutionary stages:
1. **Classical Baselines (Logistic Regression & Linear SVM):** Uses TF-IDF vectorization. Fast and lightweight, but struggles with word order and "linguistic messiness" like sarcasm.
2. **Hybrid Models (NB-SVM):** Combines generative power (Naive Bayes log-count ratios) with discriminative logic (SVM).
3. **Sequential Deep Learning (LSTM):** Processes text sequentially with internal gating mechanisms to capture word order. Improves on short text but struggles with long-document sentiment dilution.
4. **Context Era (Transformers):** Implements BERT, RoBERTa, and RoBERTa + Supervised Contrastive Learning (SCL). Uses deep bidirectional attention to solve contextual blindness and push past the performance limits of classical models.

## Key Results

| Evolution Stage | Model | SST-2 Accuracy | IMDB Accuracy |
| :--- | :--- | :--- | :--- |
| **Stage 1: Classical** | SVM (TF-IDF) | 83.7% | 90.11% |
| **Stage 2: Hybrid** | NB-SVM | 84.0% | 91.6% |
| **Stage 3: Sequential**| LSTM | ≈ 85-86% | ≈ 89-90% |
| **Stage 4: Context** | RoBERTa + SCL | 95.5% | 94.6% |

**Key Takeaway:** RoBERTa + SCL successfully breaks the performance ceilings by pulling same-sentiment reviews into tight, distinct clusters in the vector space, handling irony, plot descriptions, and mixed signals far better than frequency-based models.

## Limitations
* **Hardware Dependency:** While classical models run efficiently on standard hardware, the Transformer-based models required a rented high-memory GPU (NVIDIA RTX 5090 32GB) for fine-tuning.
* **Generalization:** The study focuses strictly on English binary sentiment analysis. Results may not directly transfer to other languages, multilingual datasets, or multi-class tasks.

## Ethical Considerations
Sentiment analysis systems carry inherent risks:
* **Profiling & Surveillance:** Can be used to build behavioral profiles or monitor public reactions without explicit consent.
* **Misclassification:** Sarcasm, jokes, or misunderstood opinions may be wrongly classified as hostile. Sentiment predictions should **not** be used as direct evidence or the sole basis for legal, administrative, or security decisions.

---
*This project was completed as part of an NLP course evaluating classical baselines to transformer architectures.*
