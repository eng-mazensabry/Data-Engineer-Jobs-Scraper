# Data Engineer Jobs Scraper

Python/Selenium notebooks that scrape "Data Engineer" job listings from two job boards — **Wuzzuf** (Egypt) and **Naukrigulf** (Gulf region) — and export the results to CSV.

Built as a web scraping exercise: same goal (collect structured job data), different site structures, different selectors.

## What it does

For each site, the scraper collects:

- Job title
- Company name
- Location
- Years of experience required
- Full job description
- Job posting link

Results are saved as CSV files.

## Project structure

```
├── Wuzzuf.ipynb            # Scrapes Wuzzuf "Data Engineer" listings (first 3 result pages)
├── wuzzuf_jobs.csv          # Wuzzuf scrape output
├── Naukrigulf.ipynb         # Scrapes Naukrigulf "Data Engineer" listings
├── naukrigulf_jobs.csv      # Naukrigulf scrape output
└── README.md
```

## Why two notebooks

Wuzzuf and Naukrigulf render job cards with completely different HTML/CSS structures, so each notebook needed its own locators and page-handling logic (pagination, missing fields, etc.). This shows the scraping approach generalizes across sites rather than being hardcoded to one.

## Tech stack

- Python
- Selenium (browser automation)
- Pandas (data structuring / CSV export)

## How to run

1. Install dependencies:
   ```bash
   pip install selenium pandas
   ```
2. Make sure you have Chrome + a matching ChromeDriver installed (or let Selenium Manager handle it automatically with recent Selenium versions).
3. Open either notebook (`Wuzzuf.ipynb` or `Naukrigulf.ipynb`) in Jupyter and run all cells.
4. The corresponding CSV file will be generated/updated in the project folder.

## Notes

- Selectors are based on each site's structure as of the scrape date; job boards update their HTML periodically, so locators may need updates over time.
- Fields that are missing on a given card (e.g. no posting date) are saved as `None` rather than breaking the notebook.

## Author

Mazen Sabry — Junior Data Engineer
