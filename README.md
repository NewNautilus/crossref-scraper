[Crossref Scraper](https://apify.com/automation-lab/crossref-scraper?fpr=data)

Search and extract academic papers, journal articles, and scholarly works from Crossref's database of over 130 million records. Get titles, authors, DOIs, citation counts, abstracts, and publication metadata.

## What does Crossref Scraper do?

Crossref Scraper searches the Crossref REST API — the world's largest database of scholarly metadata — and extracts structured data from matching works. It returns paper titles, author lists, DOIs, citation counts, abstracts, journal names, publication dates, and licensing information.

You can search by keyword, filter by work type (journal article, book chapter, conference paper, etc.), and sort by relevance, publication date, or citation count.

## Who is Crossref Scraper for?

- **Academic researchers** conducting literature reviews and bibliometric analyses across disciplines
- **Data scientists** building training datasets for scholarly AI models and recommendation engines
- **Research administrators** tracking publication output and citation impact for institutions
- **Science journalists** sourcing citation data and identifying influential papers for reporting
- **Library professionals** cataloging and analyzing scholarly works across publishers
- **Graduate students** surveying research landscapes and identifying key papers for thesis work

## Why scrape Crossref?

Crossref indexes over 130 million scholarly works from 18,000+ publishers. It's the authoritative source for:

- **Literature reviews** — find relevant papers by keyword and sort by citation impact
- **Bibliometric analysis** — study citation patterns, publication trends, and research output
- **Dataset construction** — build training data for academic AI models or recommendation systems
- **Research monitoring** — track new publications in specific fields or by specific authors
- **Citation analysis** — identify the most influential papers in any research area
- **Publisher intelligence** — analyze publication volumes and patterns across journals

## How much does it cost to scrape Crossref?

Crossref Scraper uses pay-per-event pricing:

| Event | Price |
| --- | --- |
| Run started | $0.001 |
| Paper extracted | $0.001 per paper |

**Example costs:**

- 20 most-cited papers on "deep learning": ~$0.021
- 100 recent papers on "CRISPR": ~$0.101
- 500 papers across 5 research topics: ~$0.506

Platform costs are minimal — a typical run uses under $0.002 in compute.

## Input parameters

| Parameter | Type | Description | Default |
| --- | --- | --- | --- |
| `searchQueries` | string[] | Keywords to search for in academic papers | Required |
| `type` | string | Filter by work type: journal-article, book-chapter, proceedings-article, book, dataset, report, dissertation, preprint | All types |
| `sortBy` | string | Sort results: `relevance`, `published` (newest first), `is-referenced-by-count` (most cited) | `relevance` |
| `maxResults` | integer | Maximum papers per keyword (1–1000) | `50` |

### Input example

```
{
  "searchQueries": ["machine learning", "deep learning"],
  "sortBy": "is-referenced-by-count",
  "maxResults": 20
}
```

## Output example

Each paper is returned as a JSON object:

```
{
  "doi": "10.1038/nature14539",
  "title": "Deep learning",
  "authors": ["Yann LeCun", "Yoshua Bengio", "Geoffrey Hinton"],
  "abstract": "Deep learning allows computational models that are composed of multiple processing layers to learn representations of data with multiple levels of abstraction...",
  "type": "journal-article",
  "publisher": "Springer Science and Business Media LLC",
  "journal": "Nature",
  "publishedDate": "2015-05-27",
  "citationCount": 69717,
  "referenceCount": 73,
  "url": "https://doi.org/10.1038/nature14539",
  "subjects": ["Multidisciplinary"],
  "license": "https://www.springer.com/tdm",
  "language": "en",
  "page": "436-444",
  "volume": "521",
  "issue": "7553",
  "isbn": [],
  "issn": ["0028-0836", "1476-4687"],
  "scrapedAt": "2026-03-03T04:20:00.000Z"
}
```

## What data can you extract from Crossref?

| Field | Type | Description |
| --- | --- | --- |
| `doi` | string | Digital Object Identifier — unique paper identifier |
| `title` | string | Paper title |
| `authors` | string[] | List of author names |
| `abstract` | string | Paper abstract (when available) |
| `type` | string | Work type (journal-article, book-chapter, etc.) |
| `publisher` | string | Publisher name |
| `journal` | string | Journal or container title |
| `publishedDate` | string | Publication date (YYYY-MM-DD format) |
| `citationCount` | number | Number of times this work has been cited |
| `referenceCount` | number | Number of references in this work |
| `url` | string | DOI URL linking to the paper |
| `subjects` | string[] | Subject categories |
| `license` | string | License URL |
| `language` | string | Language code |
| `page` | string | Page range |
| `volume` | string | Journal volume |
| `issue` | string | Journal issue |
| `isbn` | string[] | ISBN identifiers (for books) |
| `issn` | string[] | ISSN identifiers (for journals) |
| `scrapedAt` | string | ISO timestamp when data was extracted |

## How to scrape academic papers from Crossref

1. Go to the [Crossref Scraper](https://apify.com/automation-lab/crossref-scraper) page on Apify Store.
2. Click **Try for free** to open the actor in Apify Console.
3. Enter one or more search keywords (e.g., "machine learning", "CRISPR").
4. Optionally filter by work type, sort order, and maximum results.
5. Click **Start** and download your data as JSON, CSV, or Excel from the **Dataset** tab.

## How to use the Crossref Scraper API

### Python

```
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")

run = client.actor("automation-lab/crossref-scraper").call(run_input={
    "searchQueries": ["transformer neural network"],
    "sortBy": "is-referenced-by-count",
    "maxResults": 50,
})

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    authors = ", ".join(item["authors"][:3])
    print(f"{item['title']}")
    print(f"  {authors} | {item['publishedDate']} | {item['citationCount']} citations")
    print(f"  DOI: {item['doi']}")
```

### Node.js

```
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

const run = await client.actor('automation-lab/crossref-scraper').call({
    searchQueries: ['transformer neural network'],
    sortBy: 'is-referenced-by-count',
    maxResults: 50,
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
items.forEach(item => {
    console.log(`${item.title} (${item.citationCount} citations)`);
    console.log(`  DOI: ${item.doi}`);
});
```

### REST API

```
curl -X POST "https://api.apify.com/v2/acts/automation-lab/crossref-scraper/runs?token=YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "searchQueries": ["machine learning"],
    "sortBy": "is-referenced-by-count",
    "maxResults": 20
  }'
```

## Integrations

Connect Crossref Scraper to hundreds of apps using built-in integrations:

- **Google Sheets** — export citation data to spreadsheets for analysis
- **Slack / Microsoft Teams** — get notifications when scraping completes
- **Zapier / Make** — trigger workflows with new paper data
- **Amazon S3 / Google Cloud Storage** — store large research datasets
- **Webhook** — send results to your own API endpoint

## Tips and best practices

1. **Sort by citations** — use `is-referenced-by-count` to find the most influential papers in any field.
2. **Filter by type** — narrow results to journal articles, conference papers, or books to focus your search.
3. **Combine keywords** — use multiple search terms like `["CRISPR", "gene therapy", "genome editing"]` to cover a topic broadly.
4. **Abstract availability** — not all papers have abstracts in Crossref. About 30-40% include them.
5. **Citation counts** — these reflect citations tracked by Crossref, which may differ from Google Scholar or Scopus counts.
6. **Rate limits** — the scraper uses Crossref's polite pool (with mailto) for faster responses. No API key needed.
7. **Up to 1000 per keyword** — for larger datasets, use multiple related keywords.

## Use with AI agents via MCP

Crossref Scraper is available as a tool for AI assistants via the [Model Context Protocol (MCP)](https://docs.apify.com/platform/integrations/mcp).

### Setup for Claude Code

```
$claude mcp add --transport http apify "https://mcp.apify.com?tools=automation-lab/crossref-scraper"
```

### Setup for Claude Desktop, Cursor, or VS Code

Add this to your MCP config file:

```
{
    "mcpServers": {
        "apify": {
            "url": "https://mcp.apify.com?tools=automation-lab/crossref-scraper"
        }
    }
}
```

### Example prompts

- "Search Crossref for papers about 'CRISPR gene editing'"
- "Get citation metadata for this DOI"
- "Find the most-cited machine learning papers published in 2024 using Crossref"

## FAQ

**Q: How current is the data?**
A: Crossref data is updated continuously as publishers register new DOIs. Most papers appear within days of publication.

**Q: Does it include full paper text?**
A: No. Crossref stores metadata only — titles, authors, abstracts, DOIs, and citations. For full text, follow the DOI link to the publisher's site.

**Q: Do I need an API key?**
A: No. Crossref's API is completely open. The scraper uses the polite pool for better performance.

**Q: What types of works are covered?**
A: Journal articles, book chapters, conference papers, books, datasets, reports, dissertations, preprints, and more — anything with a DOI registered through Crossref.

**Q: Why are some papers missing abstracts?**
A: Only about 30-40% of papers in Crossref include abstracts. This depends on whether the publisher deposits abstract text when registering the DOI. There is no workaround on the scraper side.

**Q: Why do I get fewer results than expected?**
A: Crossref returns up to 1,000 results per keyword. If your search term is very broad, the API may still limit results. Try more specific keywords or use multiple related search terms to cover the topic.

## Is it legal to scrape Crossref?

Crossref is a non-profit organization that provides open, freely accessible metadata for scholarly works. The Crossref REST API is public, requires no authentication, and is explicitly designed for programmatic access to bibliographic data.

Crossref metadata -- titles, authors, DOIs, citation counts, and publication dates -- is factual bibliographic information that publishers voluntarily deposit. The API includes a "polite pool" that provides faster access to clients who identify themselves, which this scraper uses.

Crossref's [Terms of Use](https://www.crossref.org/operations-and-sustainability/terms-of-use/) permit free use of their metadata. The scraper does not access full-text content, which remains on publisher websites under their own licensing terms.

## Other academic and research scrapers

- [ClinicalTrials.gov Scraper](https://apify.com/automation-lab/clinicaltrials-scraper) -- Scrape clinical trial data from ClinicalTrials.gov.
- [OpenAlex Scraper](https://apify.com/automation-lab/openalex-scraper) -- Extract scholarly works and author data from OpenAlex.
- [Semantic Scholar Scraper](https://apify.com/automation-lab/semantic-scholar-scraper) -- Search papers and citations on Semantic Scholar.
- [arXiv Scraper](https://apify.com/automation-lab/arxiv-scraper) -- Scrape preprints and research papers from arXiv.