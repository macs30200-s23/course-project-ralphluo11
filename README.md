
# Framing the Nation: Media Construction of National Identity

##  Project Description

This project analyzes how major U.S. news outlets construct and contrast American nationalism with Chinese and Russian nationalism. Using a hybrid NLP framework combining LDA, SBERT+UMAP+KMeans, and BERT-based classification, the analysis maps identity frames (e.g., “geopolitical influence,” “state governance”) and tracks shifts in sentiment and stance across 50,000+ articles from 2021–2024.

Key themes include:
- **Media framing divergence by outlet and political orientation**
- **Temporal shifts in identity frames tied to geopolitical events**
- **Stance-sentiment mismatches revealing framing complexity**

Initial results from NYT 2024 articles show dominant use of strategic and governance frames, with sentiment and stance diverging on emotionally loaded frames like "dictatorship."

---

##  Code Structure & Key Steps

The notebook `mock.ipynb` executes the full pipeline including the following steps:

###  Data Preprocessing
- Load the dataset: `China_article_nyt2024.csv`
- Check and relabel unknown `news_desk` values as 'Multimedia'
- Drop articles missing `full_text`
- Filter out low-frequency `news_desk` groups (fewer than 10 articles)
- Parse and format `pub_date` column

###  Topic Modeling
- Apply LDA to discover latent topics
- Interpret and manually assign identity labels
- Extract topic distributions using `lda.transform()`

### Identity Mapping
- Define `identity_map = {...}` to assign topics to identity dimensions
- Count and visualize identity occurrences with `value_counts()`
- Generate correlation heatmaps for frame co-occurrence

###  Clustering and Semantic Anchoring
- SBERT embedding → UMAP reduction → KMeans clustering
- Align cluster centroids with anchor phrases using cosine similarity
- Refine visualizations by merging similar clusters

###  Sentiment and Stance Analysis
- Perform VADER sentiment scoring on `full_text`
- Visualize sentiment per identity frame using box plots and line charts
- Apply stance detection via GPT-labeled training data and keyword rules
- Plot sentiment vs. frame share over time

---

##  Folder Layout

```
data/
    └── China_article_nyt2024.csv    # NYT full-text articles from 2024
notebooks/
    └── mock.ipynb                   # Full analysis notebook
analysis/
    └── frame_viz/                   # Plots and visualizations
models/
    └── identity_classifier/         # Fine-tuned classifier (TBD)
requirements.txt
README.md
main.py
```

---

##  Environment & Installation

Install dependencies:

```bash
pip install -r requirements.txt
```

Main libraries:
- `transformers`, `sentence-transformers`, `scikit-learn`
- `matplotlib`, `seaborn`, `nltk`, `spacy`, `vaderSentiment`, `umap-learn`, `pandas`

GPU is recommended for classification tasks (e.g., Google Colab Pro or AWS EC2 with GPU).

---

## Sample Output

Plots will be stored under `analysis/frame_viz/` including:
- Identity frame time series
- Sentiment per frame boxplot
- UMAP semantic cluster visualization

---

## 🔖 Citation

Luo, J. (2025). *Framing the Nation: How U.S. Media Constructs American, Chinese, and Russian National Identity* [Unpublished manuscript]. University of Chicago.
