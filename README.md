#  Framing the Nation: Media Construction of National Identity

##  Project Description

This proposal outlines a computational media analysis project focused on understanding how U.S. English-language media constructs national identity in relation to geopolitical rivals. Specifically, the study investigates how American outlets portray the United States in contrast to China and Russia, emphasizing how these portrayals shift over time, differ across political orientations, and respond to major international developments.

By analyzing large-scale news data from The New York Times, Fox News, CNN, and The Wall Street Journal (2021–2024), this project applies scalable natural language processing (NLP) techniques to identify and classify thematic identity frames. Using a hybrid pipeline that combines Latent Dirichlet Allocation (LDA), Sentence-BERT embeddings, UMAP+KMeans clustering, and BERT-based supervised classifiers, the study extracts frames like “geopolitical influence,” “state governance,” “historical legacy,” and “dictatorship.”

In addition to thematic classification, the project detects sentiment (via VADER) and stance (supportive, oppositional, neutral) using both rule-based and GPT-assisted methods. These dimensions are tracked over time to reveal how news coverage shifts in tone and framing during moments of international tension (trade wars, military standoffs, diplomatic events, and other events).

Ultimately, this research seeks to uncover patterns in how national identity is discursively constructed, contested, and politicized in American media. The proposed framework enables comparative analysis across outlets and over time, offering insights into the performative role of journalism in shaping geopolitical narratives.

---

##  Workflow Summary (from `mock.ipynb`)

###  Data Preprocessing
- Load and clean NYT 2024 dataset: `data/China_article_nyt2024.csv`
- Relabel unknown news desks → “Multimedia”
- Remove articles with missing `full_text`
- Standardize date format for time-based analysis

###  Topic Modeling
- Apply LDA to extract latent frames
- Map LDA topics to identity dimensions via manual alignment
- Track frame prevalence over time using `pub_date`

###  Semantic Clustering
- Use SBERT + UMAP + KMeans to cluster embeddings
- Align clusters to identity anchors 

###  Sentiment and Stance Mock-Up
- VADER sentiment scores by identity dimension
- GPT-assisted stance annotations for frame-attitude correlation

---

##  Illustrative Mock-Up (Proposal Phase)

This bar chart provides an example of how identity frames are automatically extracted and categorized in the NYT 2024 China coverage:

![Document Count](initial_fig/lda/Document%20Count%20per%20National%20Identity%20Dimension.png)

*Fig. 1. Distribution of identity dimensions assigned via LDA + manual alignment*

---

##  Folder Layout

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
├── main.tex                                    # LaTeX source file for bibliography
├── Annotated_Bibliography.bib                  # Annotated bibliography (BibTeX format)
├── IEEEannot.bst                               # Custom BibTeX style for annotations in bibliography
├── Big Picture Literature Review.tex           # Literature review
└── README.md                                   # Project overview and documentation

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
