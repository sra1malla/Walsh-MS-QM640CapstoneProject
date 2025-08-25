# Walsh-MS-QM640CapstoneProject

## Overview

This project analyzes and compares customer app reviews from multiple banks, using advanced NLP and retrieval-augmented generation (RAG) techniques. It includes extraction, cleaning, scoring, and interactive analysis of reviews from Google Play and Apple App Store.

## Key Features

- **Review Extraction & Processing:**  
  Extracts reviews using AppFollow API, cleans and merges data from both app stores.

- **Review Scoring & Sentiment:**  
  Predicts sentiment and department, calculates SLA status, and exports scored datasets.

- **RAG Pipeline for Analytics:**  
  Interactive Jupyter notebook with a hybrid RAG pipeline (semantic search + LLM code generation) for both natural language and structured queries.

- **Visualization:**  
  Plots for SLA status, language distribution, and more, at both overall and per-app levels.

## Main Notebooks

- `reviews_extraction.ipynb` — Extraction, cleaning, and merging of raw review data.
- `reviews_scoring.ipynb` — Sentiment, department, and SLA scoring.
- `reviews_rag_pipeline.ipynb` — RAG pipeline for interactive analytics and LLM-powered querying.
- `reviews_classification.ipynb` — Additional classification and analysis tasks.

## Data & Models

- **Data:**

  - `extracts/` — Raw and processed review files.
  - `scored/` — Scored and labeled review datasets.
  - `lookup/CompetitorApps_Lookup.csv` — App metadata.

- **Models:**
  - `sentiment_eng/`, `sentiment_multi/` — Pretrained sentiment models and tokenizers.

## How to Use

1. **Install dependencies:**

   - All notebooks use `pandas`, `numpy`, `requests`, `openai`, `faiss`, `matplotlib`, `seaborn`, and `tqdm`.
   - Install with `pip install -r requirements.txt` or run the `%pip install ...` cells in the notebooks.

2. **Run the ETL pipeline:**

   - Start with `reviews_extraction.ipynb` to extract and process reviews.
   - Use `reviews_scoring.ipynb` to score and label reviews.
   - Explore and analyze with `reviews_rag_pipeline.ipynb`.

3. **Interactive Analytics:**
   - Use the RAG pipeline to ask questions about the reviews, either in natural language or as structured queries.

## Example Queries

- "Show departments that had most complaints last month."
- "What are some common issues related to fraud mentioned by users?"
- "Plot the distribution of SLA status for each app."

## Project Structure

```
extracts/         # Raw and processed review data
scored/           # Scored and labeled review data
lookup/           # App metadata lookup
sentiment_eng/    # English sentiment model files
sentiment_multi/  # Multilingual sentiment model files
reviews_extraction.ipynb
reviews_scoring.ipynb
reviews_rag_pipeline.ipynb
reviews_classification.ipynb
README.md
```

## Notes

- API keys (e.g., OpenAI) should be set in youy environment.
- All data exports are in Excel format with UTF-8 encoding.
- For more details, see the markdown cells in each notebook.

---

### ⚠️ Large Model Files Not Included

Due to size limitations, the following model folders are **not included** in this repository and are listed in `.gitignore`:

- `mistral-7b-instruct-v0.2/`
- `xlm-roberta-base-language-detection/`

If you need these models:

- Download them from their official sources or your organization’s storage.
- Place them in the project root under the same folder names.

> **Note:** Only lightweight model files (such as `tokenizer.json` in `sentiment_eng/` and `sentiment_multi/`) are tracked with Git LFS.
