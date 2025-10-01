# CommBank Introduction to Data Science

A collection of exploratory notebooks prepared for the CommBank Introduction to Data Science challenge. Each task focuses on a different stage of the analytics workflow: aggregating transaction data, anonymising sensitive customer attributes, and outlining approaches for social media insight generation.

From this link: https://www.theforage.com/simulations/commonwealth-bank/intro-data-science-sd7t

## Repository Layout
- `task1.ipynb` – supermarket transaction aggregation and KPI calculations.
- `task2.ipynb` – customer data anonymisation pipeline and export.
- `task3.ipynb` – exploratory calls to the Twitter API plus brainstorming for further analysis.
- `data/` – source Excel workbooks supplied with the challenge brief.
- `uploaded/` – exported artefacts such as the anonymised CSV and written proposals.

## Requirements
- Python 3.8 or newer
- JupyterLab or Jupyter Notebook (to execute the notebooks)
- Python packages: `pandas`, `openpyxl`, `requests`, `python-dotenv`

Create an isolated environment (recommended):

```bash
python3 -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install --upgrade pip
pip install jupyterlab pandas openpyxl requests python-dotenv
```

## Data Sources
- `data/supermarket_transactions.xlsx` – point-of-sale data for multiple stores (used in Task 1).
- `data/mobile_customers.xlsx` – customer profile dataset that includes personally identifiable information (used in Task 2).

Keep the raw data files in the `data/` directory so the notebooks can load them using relative paths.

## Running the Notebooks
1. Launch Jupyter:
   ```bash
   jupyter lab
   ```
2. Open the notebook of interest and run the cells in order (Kernel → Restart & Run All) to reproduce the results.

### Task 1 – Data Aggregation and Analysis (`task1.ipynb`)
- Loads `supermarket_transactions.xlsx` into a pandas DataFrame.
- Filters and aggregates to answer:
  - Cash apple purchases across all locations (count and total cash spent).
  - Total spend at the Bakershire store by non-member customers.
- Outputs (for the supplied data): 117 apples purchased for $537.03 in cash, and $2,857.51 spent by Bakershire non-members across all payment methods.

### Task 2 – Data Anonymisation (`task2.ipynb`)
- Drops direct identifiers (names, contact details, card numbers, locations).
- Hashes employer and job fields using SHA-256.
- Buckets ages into decade bands and rounds salaries to the nearest thousand to minimise re-identification risk.
- Writes the sanitised dataset to `uploaded/anonymised_mobile_customers.csv` (path can be adjusted inside the notebook).

### Task 3 – Social Media Insight Exploration (`task3.ipynb`)
- Demonstrates how to authenticate against the Twitter API v2 using environment variables.
- Contains sample queries for recent tweets from `@CommBank` and keyword-based searches to inspire downstream analysis (engagement, sentiment, collaborations, etc.).

To run Task 3 you need a Twitter developer account. Store credentials in a `.env` file alongside the notebook:

```
API_KEY=your_api_key
API_KEY_SECRET=your_api_key_secret
BEARER_TOKEN=your_bearer_token
```

Then restart the kernel so `python-dotenv` can load the environment variables before the API calls are executed.

## Outputs and Supporting Notes
- `uploaded/anonymised_mobile_customers.csv` – anonymised customer data generated in Task 2.
- `uploaded/task3.txt` – written outline of potential Twitter-derived insights.
- `uploaded/task4.txt` – suggested data model for structuring social media entities.
