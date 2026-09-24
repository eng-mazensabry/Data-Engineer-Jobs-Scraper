# Wuzzuf Data Engineer Jobs Scraper

A Selenium + Python script that scrapes "Data Engineer" job listings from [Wuzzuf](https://wuzzuf.net/jobs/egypt) (first 3 result pages) and exports them to a CSV file.

**Author:** Mazen Sabry

## What it does

1. Opens Wuzzuf's Egypt jobs page in Chrome and searches for **Data Engineer**.
2. Goes through the **first three pages** of results, clicking the Next button between pages.
3. For every listing, extracts the title, company, location, required experience, and the job link.
4. Visits each job's own page and extracts the **full job description**.
5. Removes duplicate listings and saves everything to `wuzzuf_jobs.csv` (UTF-8 with BOM, so Arabic text displays correctly in Excel).

## Extracted fields

| Column        | Description                              |
|---------------|------------------------------------------|
| `job_title`   | Title of the job                         |
| `company`     | Company name                             |
| `location`    | Job location                             |
| `experience`  | Required experience                      |
| `job_link`    | URL of the job page                      |
| `description` | Full job description from the job page   |

## Requirements

- Python 3.8+
- Google Chrome
- Python packages:

```bash
pip install selenium pandas
```

Selenium 4.6+ downloads the matching ChromeDriver automatically, so no manual driver setup is needed.

## How to run

```bash
python wuzzuf_scraper.py
```

The script prints its progress (page number, then description number) and saves `wuzzuf_jobs.csv` in the folder you ran it from.

## Project structure

```
.
├── wuzzuf_scraper.py   # the Selenium script
├── wuzzuf_jobs.csv     # scraped output
└── README.md
```

## Notes and limitations

- **Fragile selectors:** Wuzzuf uses auto-generated CSS class names (e.g. `css-pkv5jc`) that can change when the site is updated. If the script stops finding elements, re-inspect the page and update the selectors.
- **Page refreshes:** `driver.refresh()` and `time.sleep()` are used after loading and searching because the results did not always load reliably on the first attempt.
- **Delay between requests:** a short pause is added between job pages to avoid overloading the site.
- Listings with a missing field are stored as `"Not specified"`.
- Scraped data is for educational purposes only. Respect the website's terms of use.
