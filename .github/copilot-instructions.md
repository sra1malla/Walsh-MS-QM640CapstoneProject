# Copilot Instructions for QM640 Capstone Project

## Project Overview
This project extracts, processes, and merges app review data from Google Play Store and Apple App Store using Python in a Jupyter notebook (`reviews_extraction.ipynb`). Data is sourced via the AppFollow API and processed for further analysis.

## Key Components
- **reviews_extraction.ipynb**: Main workflow for extraction, cleaning, merging, and exporting review data.
- **extracts/**: Stores raw and processed review Excel files.
- **lookup/CompetitorApps_Lookup.csv**: Lookup table for app metadata (store, app name, IDs).

## Data Flow
1. **Extraction**: Reads app info from the lookup CSV, fetches reviews from AppFollow API for each app/store, and saves raw data to Excel.
2. **Processing**: Cleans and normalizes review data, standardizes columns, and saves processed data.
3. **Merging**: Combines Google and Apple reviews, deduplicates, and exports a merged dataset.
4. **Analysis**: Performs sentiment labeling and sample size calculations.

## Patterns & Conventions
- All review extraction and processing logic is in the notebook, not in separate modules.
- API tokens are hardcoded in the notebook (consider securing for production).
- Dataframes are always exported to Excel using UTF-8 encoding.
- Timezone conversions are handled to 'Asia/Dubai' for all date fields.
- Column renaming and selection is explicit before merging.
- Deduplication uses a composite key of reviewId, userName, reviewContent, rating, reviewedAt, and store.

## Developer Workflows
- **Run all cells in `reviews_extraction.ipynb`** to perform the full ETL pipeline.
- **Update `lookup/CompetitorApps_Lookup.csv`** to add/remove apps for extraction.
- **Output files** are written to `extracts/`.
- No custom build or test scripts; all logic is in the notebook.

## External Dependencies
- `pandas`, `numpy`, `requests`, `xlsxwriter`, `scipy` (for sample size calc)
- AppFollow API for review data

## Example: Adding a New App
1. Add the app's metadata to `lookup/CompetitorApps_Lookup.csv`.
2. Rerun the notebook to extract and process new reviews.

## Tips
- Review extraction loops are capped at 100 pages per app.
- If API limits are hit, rerun the failed cells after waiting.
- All processed and merged data is exported for reproducibility.

---
For questions, see the notebook markdown cells for step-by-step explanations.
