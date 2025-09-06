# Walsh-MS-QM640CapstoneProject

## Overview

This project analyzes and compares customer app reviews from multiple banks, using advanced NLP and retrieval-augmented generation (RAG) techniques. It includes extraction, cleaning, scoring, and interactive analysis of reviews from Google Play and Apple App Store.

## Key Features

- **Review Extraction & Processing:**
  - Extract reviews using AppFollow API, clean and merge data from both app stores.
- **Review Scoring & Sentiment:**
  - Predict sentiment and issue category department, calculate SLA status, and export scored datasets.
- **Hybrid RAG Pipeline for Analytics:**
  - Interactive Jupyter notebook with a hybrid RAG pipeline (semantic search + LLM code generation) for both natural language and structured queries.
  - Robust intent detection (keyword + model-based) and code cleaning for LLM-generated pandas code.
  - Quantitative evaluation with 50+ queries, reporting metrics: intent detection accuracy, latency, error rate, and coverage.
- **Visualization:**
  - Plots for SLA status, language distribution, and more, at both overall and per-app levels.

## RAG Pipeline Evaluation & Metrics

After running 50 diverse queries through the RAG pipeline, the following metrics are reported:

- **Intent Detection Accuracy:** Percentage of queries correctly classified as "structured" or "semantic" (e.g., 98%).
- **Average Latency:** Mean time to process each query (e.g., 2.16 seconds).
- **Error Rate:** Percentage of queries resulting in errors (e.g., 6%).
- **Coverage:** Percentage of queries answered successfully (e.g., 94%).

These metrics indicate the pipeline is highly accurate, fast, and reliable for a wide range of review analytics queries.

## Main Notebooks

- `reviews_extraction.ipynb` — Extraction, cleaning, and merging of raw review data.
- `reviews_scoring.ipynb` — Sentiment, department, and SLA scoring.
- `reviews_rag_pipeline.ipynb` — RAG pipeline for interactive analytics and LLM-powered querying.
- `reviews_classification.ipynb` — Additional classification and analysis tasks.

## Data & Models

- **Data:**

  - `extracts/` — Raw and processed review files.
  - `scored/` — Scored and labeled review datasets.
  - `scored/review_faiss_index.bin` — FAISS index for semantic search (tracked with Git LFS).
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

- API keys (e.g., OpenAI) should be set in your environment.
- All data exports are in Excel format with UTF-8 encoding.
- For more details, see the markdown cells in each notebook.
- To track large binary files (e.g., FAISS index), use Git LFS:
  ```sh
  git lfs track "scored/review_faiss_index.bin"
  git add .gitattributes scored/review_faiss_index.bin
  git commit -m "Track review_faiss_index.bin with Git LFS"
  ```

---

### ⚠️ Large Model Files Not Included

Due to size limitations, the following model folders are **not included** in this repository and are listed in `.gitignore`:

- `mistral-7b-instruct-v0.2/`
- `xlm-roberta-base-language-detection/`

If you need these models:

- Download them from their official sources or your organization’s storage.
- Place them in the project root under the same folder names.

> **Note:** Only lightweight model files (such as `tokenizer.json` in `sentiment_eng/` and `sentiment_multi/`) are tracked with Git LFS.
