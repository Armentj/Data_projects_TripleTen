# NLP Movie Review Classification

A natural language processing project built for **Film Junky Union**, a community for classic movie enthusiasts, to automatically detect negative movie reviews. The project benchmarks multiple NLP pipelines — from traditional TF-IDF approaches to transformer-based BERT embeddings — targeting an F1 score of at least 0.85.

---

## Project Overview

Film Junky Union needed an automated system to filter and categorize user-submitted movie reviews by sentiment. The goal was to train a binary classifier distinguishing positive from negative reviews using a labeled IMDB dataset.

**Success criterion:** F1 score ≥ 0.85 on the test set.

---

## Dataset

IMDB movie reviews with polarity labels, stored in `imdb_reviews.tsv`.

| Column | Description |
|---|---|
| `review` | Raw review text |
| `pos` | Sentiment label (1 = positive, 0 = negative) |
| `rating` | Numerical rating |
| `ds_part` | Dataset split (`train` / `test`) |

---

## Models Compared

| Model | Approach | Notes |
|---|---|---|
| Model 0 | DummyClassifier (Baseline) | Most-frequent class — establishes minimum benchmark |
| Model 1 | NLTK + TF-IDF + Logistic Regression | Stopword removal, bag-of-words features |
| Model 3 | spaCy Lemmatization + TF-IDF + Logistic Regression | Lemmatization reduces vocab size, improves generalization |
| Model 4 | spaCy Lemmatization + TF-IDF + LightGBM | Gradient boosting captures non-linear feature interactions |
| Model 9 | BERT Embeddings + Logistic Regression | Contextual transformer embeddings — strongest semantic understanding |

---

## Key Results

- **TF-IDF models** significantly outperformed the dummy baseline, with lemmatization (Model 3) providing additional gains over simple stopword removal (Model 1)
- **LightGBM** (Model 4) improved on linear models by capturing non-linear relationships and yielding more balanced precision/recall
- **BERT** (Model 9) delivered the best overall performance, demonstrating the power of contextual embeddings over traditional bag-of-words representations
- Each step in the pipeline progression — from heuristics to embeddings — showed measurable improvement, illustrating the trade-off between sophistication, computational cost, and predictive power

---

## Text Preprocessing Pipeline

1. Lowercasing and HTML tag removal
2. Punctuation and digit stripping
3. Stopword removal (NLTK) or lemmatization (spaCy)
4. TF-IDF vectorization
5. Model training and RMSE/F1 evaluation

---

## Tech Stack

- **Python 3**
- **Pandas / NumPy** — data loading and manipulation
- **NLTK** — stopwords, tokenization
- **spaCy** — lemmatization and linguistic preprocessing
- **Scikit-learn** — TF-IDF, Logistic Regression, DummyClassifier, evaluation metrics
- **LightGBM** — gradient boosting classifier
- **Transformers (Hugging Face)** — BERT tokenizer and model
- **Matplotlib / Seaborn** — EDA visualizations

---

## How to Run

1. Clone the repository
2. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn nltk spacy lightgbm transformers torch matplotlib seaborn tqdm
   python -m spacy download en_core_web_sm
   ```
3. Place `imdb_reviews.tsv` in a `/datasets/` directory (or update the load path in the notebook)
4. Open and run `nlp_movie_review_classification.ipynb` in Jupyter Notebook or JupyterLab

> **Note:** The BERT model requires significant RAM (20+ GB) to process the full dataset. A GPU environment (e.g., Google Colab) is recommended for that section.

---

## Project Structure

```
.
├── nlp_movie_review_classification.ipynb   # Main project notebook
└── README.md                               # Project documentation
```

---

## Concepts Demonstrated

- Binary text classification (sentiment analysis)
- Text normalization: lowercasing, HTML removal, lemmatization
- TF-IDF vectorization with stopword filtering
- NLP pipeline comparison: rule-based → statistical → deep learning
- Gradient boosting for text classification (LightGBM)
- Transformer-based embeddings (BERT)
- F1 score evaluation for imbalanced classification tasks
- ROC-AUC and precision/recall analysis
