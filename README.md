```markdown
# AI-Powered Book Recommender

## Overview
A local, hybrid book recommendation engine built in Python. This system processes raw book metadata and user reviews into a normalized SQLite database, generates dense text embeddings for semantic search, and provides an interactive Jupyter Notebook interface for natural language querying.

## Technical Architecture & Performance
* **Scale:** Deployed a normalized SQLite database (`Books`, `Prices`, `Reviews`) to process and query a dataset of 2,457 items.
* **Latency:** Achieved sub-second retrieval latency against live natural-language user queries.
* **Embedding Generation:** Uses the `all-MiniLM-L6-v2` SentenceTransformer model to encode descriptions into high-dimensional vectors, saved locally as NumPy arrays for rapid similarity calculations.
* **Hybrid Scoring Engine:** Ranks candidate books using a weighted formula: 70% cosine similarity (between query and book description embeddings) and 30% normalized average user rating.
* **Query Parsing:** Extracts hard constraints (genre, max price, publisher, year) from natural language inputs using Regex and evaluates query sentiment using NLTK's `SentimentIntensityAnalyzer`.

## Installation and Execution
Requires a Python 3.11+ environment.

```bash
git clone [https://github.com/Pooya-s/Bookrecom.git](https://github.com/Pooya-s/Bookrecom.git)
cd Bookrecom
pip install -r requirements.txt
jupyter notebook
