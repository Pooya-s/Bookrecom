# AI-Powered Book Recommender

## Overview
This repository contains a local, hybrid book recommendation system built in Python. It processes raw book metadata and user reviews into a normalized SQLite database, generates dense text embeddings for semantic search, and provides an interactive Jupyter Notebook interface for natural language querying. 

## Technical Architecture

The system utilizes a hybrid scoring mechanism to retrieve and rank books based on user queries:
* **Data Pipeline:** Extracts and cleans pricing, metadata, and reviews from source CSV files, normalizing the data into a relational SQLite database (`Books`, `Prices`, `Reviews`).
* **Embedding Generation:** Uses the `all-MiniLM-L6-v2` SentenceTransformer model to encode book descriptions into high-dimensional vectors. These are saved locally as NumPy arrays for rapid similarity calculations.
* **Query Parsing:** Extracts hard constraints (genre, max price, publisher, publication year) from natural language inputs using Regular Expressions (Regex) and evaluates query sentiment using NLTK's `SentimentIntensityAnalyzer`.
* **Hybrid Scoring Engine:** Ranks candidate books using a weighted formula: 70% cosine similarity (between the query and book description embeddings) and 30% normalized average user rating.
* **User Interface:** Renders a front-end input/output display directly within the notebook using `ipywidgets`.

## Requirements and Installation

To run this project locally, you need a Python 3.11+ environment. 

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/Pooya-s/Bookrecom.git](https://github.com/Pooya-s/Bookrecom.git)
   cd Bookrecom
