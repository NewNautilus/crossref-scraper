[Crossref Scraper](https://apify.com/fortuitous_pirate/crossref-scraper?fpr=data)

# CrossRef Scholarly Publications Scraper

## Overview

Extract scholarly publication metadata from CrossRef API covering 145M+ academic works. Get DOIs, titles, authors, citations, journals, and publication dates. Search by keywords, author, ISSN, or date range.

## Features

- Search by keywords to find specific results
- Filter results by category or type
- Export data in JSON, CSV, or Excel formats

## Use Cases

- **Aggregate** - Aggregate academic papers and research data
- **Build** - Build course catalogs and educational resource databases
- **Track** - Track educational institution data and rankings
- **Monitor** - Monitor academic publishing trends

## Input Parameters

| Parameter | Type | Description | Default |
| --- | --- | --- | --- |
| `query` | string | Search query for scholarly works |  |
| `doi` | string | Specific DOI to look up (e.g., 10.1038/nature12373) |  |
| `author` | string | Filter by author name |  |
| `publishedSince` | string | Filter works published after this date (YYYY-MM-DD) |  |
| `type` | string | Type of scholarly work |  |
| `mailto` | string | Your email for CrossRef's polite pool (faster rate limits) |  |
| `limit` | integer | Maximum number of works to return | `100` |

## Output Example

Each result contains structured data like this:

```
{
  "doi": "Sample doi",
  "title": "Sample Education/Academic Result",
  "authors": [
    "J. Smith",
    "A. Johnson"
  ],
  "type": "Standard",
  "containerTitle": "Sample containerTitle",
  "publisher": "Sample publisher",
  "publishedDate": "2025-01-15",
  "citedByCount": 127,
  "url": "https://example.com/item/12345",
  "abstract": "Detailed description of the item..."
}
```

## Pricing

This actor uses pay-per-result pricing:

- **$0.001** per result
- **$1.00** per 1,000 results

No monthly fees. You only pay for what you scrape. [Apify Free plan](https://apify.com/pricing) includes $5/month in platform credits.

## How to Run

### Apify Console

1. Go to the [CrossRef Scholarly Publications Scraper](https://apify.com/fortuitous_pirate/crossref-scraper) actor page
2. Configure your input parameters
3. Click **Start** and wait for the results
4. Download data in JSON, CSV, or Excel format

### API

```
curl -X POST "https://api.apify.com/v2/acts/fortuitous_pirate~crossref-scraper/runs?token=YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"maxItems": 10}'
```

### Python SDK

```
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")
run = client.actor("fortuitous_pirate/crossref-scraper").call(
    run_input={"maxItems": 10}
)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Integration

Connect CrossRef Scholarly Publications Scraper with your existing tools and workflows:

- **API access** - Programmatic access via [Apify API](https://docs.apify.com/api/v2)
- **Webhooks** - Get notified when scraping completes
- **Scheduling** - Set up recurring runs on any schedule
- **Zapier / Make** - Connect with 5,000+ apps via [Apify integrations](https://apify.com/integrations)
- **Python / Node.js SDKs** - Native client libraries for easy integration