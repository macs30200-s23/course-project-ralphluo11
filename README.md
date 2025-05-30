#  Framing the Nation: Media Construction of National Identity

##  Project Description

This proposal outlines a computational media analysis project focused on understanding how U.S. English-language media constructs national identity in relation to geopolitical rivals. Specifically, the study investigates how American outlets portray the United States in contrast to China and Russia, emphasizing how these portrayals shift over time, differ across political orientations, and respond to major international developments.

By analyzing large-scale news data from The New York Times, Fox News, CNN, and The Wall Street Journal (2021–2024), this project applies scalable natural language processing (NLP) techniques to identify and classify thematic identity frames. Using a hybrid pipeline that combines Latent Dirichlet Allocation (LDA), Sentence-BERT embeddings, UMAP+KMeans clustering, and BERT-based supervised classifiers, the study extracts frames like “geopolitical influence,” “state governance,” “historical legacy,” and “dictatorship.”

In addition to thematic classification, the project detects sentiment (via VADER) and stance (supportive, oppositional, neutral) using both rule-based and GPT-assisted methods. These dimensions are tracked over time to reveal how news coverage shifts in tone and framing during moments of international tension (trade wars, military standoffs, diplomatic events, and other events).

Ultimately, this research seeks to uncover patterns in how national identity is discursively constructed, contested, and politicized in American media. The proposed framework enables comparative analysis across outlets and over time, offering insights into the performative role of journalism in shaping geopolitical narratives.

---

## Workflow Summary (from `initial mock.ipynb`)

### 1. Data Preprocessing
- Load and clean NYT dataset from `China_article_nyt2024.csv`
- Relabel missing or unknown `news_desk` values to “Multimedia”
- Drop rows with missing `full_text` entries
- Remove low-volume news desks: Business Day, Multimedia, Technology, World
- Standardize and parse `pub_date` for downstream temporal analysis

### 2. Topic Modeling
- Apply Latent Dirichlet Allocation (LDA) to extract latent topics
- Manually align LDA topics to predefined national identity dimensions
- Aggregate and track frame prevalence monthly using `pub_date`

### 3. Semantic Clustering
- Encode article text using Sentence-BERT
- Reduce embedding dimensionality using UMAP (`n_neighbors=50`, `min_dist=0.1`)
- Cluster with K-Means (optimal k via silhouette score)
- Match cluster centroids to identity anchor phrases using cosine similarity

### 4. Sentiment & Stance Inference (Mock Phase)
- Compute sentiment using BERT-based transformer (not VADER)
- Use GPT-assisted zero-shot labeling to assign cluster-level stances: support, oppose, or neutral
- Analyze temporal trends in sentiment and stance across identity frames

---

*Note: This notebook reflects a prototype pipeline focused on the NYT 2024 subset. Full implementation will scale this approach to the entire 2021–2024 corpus across all selected outlets.*

##  Illustrative Mock-Up (Proposal Phase)

This bar chart provides an example of how identity frames are automatically extracted and categorized in the NYT 2024 China coverage:

![Document Count](initial_fig/lda/Document%20Count%20per%20National%20Identity%20Dimension.png)

*Fig. 1. Distribution of identity dimensions assigned via LDA + manual alignment*

---

##  Folder Layout

```
COURSE-PROJECT/
│
├── Data/
│   └── China_article_nyt2024.csv               # Cleaned full-text articles from NYT
│
├── initial_fig/                                # Mock-up figures used in proposal
│   ├── lda/                                    # Topic modeling and clustering visuals
│   ├── sentiment/                              # Sentiment trends and distributions
│   └── stance/                                 # Stance classification plots
│
├── mock.ipynb                                  # Main analysis notebook
├── main.tex                                    # LaTeX source file for paper/report
├── Annotated_Bibliography.bib                  # Annotated bibliography (BibTeX format)
├── IEEEannot.bst                               # Custom BibTeX style for annotations
├── Big Picture Literature Review.tex           # Literature review
└── README.md                                   # Project overview and documentation
```
---

## Setup Instructions

To reproduce or extend the pipeline:

- Use **Python 3.9+**
- Install the following Python packages:
  - `pandas`
  - `matplotlib`
  - `seaborn`
  - `nltk`
  - `spacy`
  - `vaderSentiment`
  - `umap-learn`
  - `scikit-learn`
  - `transformers`
  - `sentence-transformers`
- Clone this repository and navigate to the project root
- Open and run `notebooks/mock.ipynb` to execute the full analysis
- For BERT-based classification or embedding steps, a GPU-enabled environment is recommended

---

##  Citation

Luo, J. (2025). *Framing the Nation: How U.S. Media Constructs American, Chinese, and Russian National Identity* [Research proposal]. University of Chicago.
