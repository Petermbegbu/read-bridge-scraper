# Webscraping Project

`scraper.ipynb` scrapes 10 catalogue pages from [Books to Scrape](https://books.toscrape.com/), cleans the data, and loads it into PostgreSQL.

**Extract** — Fetches each page with `safe_get()` (timeout, error handling, 1s delay) and pulls title, price, star rating, availability, and page number for every book.

**Transform** — Builds a pandas DataFrame, strips the £ from price, maps ratings (`One`–`Five`) to `1`–`5`, adds `scraped_at`, and sets column types.

**Load** — Writes table `readbridge` using credentials from `.env`, then reads it back to confirm.

## Run it

1. Install: `pip install requests beautifulsoup4 pandas sqlalchemy psycopg2-binary python-dotenv`
2. Start PostgreSQL and create database `readbridge_scraper`.
3. Fill in `.env` (`POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_HOST`, `POSTGRES_PORT`, `POSTGRES_DB`).
4. Open `scraper.ipynb` and Run All.
