[Crossref Scraper](https://apify.com/cloud9_ai/crossref-scraper?fpr=data)

Search and extract scholarly publication metadata from Crossref. Get DOIs, citations, authors, journals for 140M+ works.

## Features

- Extract data from [https://api.crossref.org](https://api.crossref.org)
- Multiple scraping modes: searchWorks, searchJournals
- Automatic rate limiting (50 req/sec (polite))
- Proxy support via Apify Proxy

## Input Configuration

### Modes

1. **searchWorks**: /works?query={query}&rows=20&offset={offset}
2. **searchJournals**: /journals?query={query}&rows=20&offset={offset}

### Example Input

```
{
  "mode": "searchWorks",
  "query": "example search",
  "maxResults": 20
}
```

## Output

The actor stores results in the Apify dataset. Each item contains:

- `DOI`
- `title`
- `author`
- `container-title`
- `published-print`
- `type`
- `is-referenced-by-count`
- `subject`
- `URL`
- `abstract`

## Usage Example

```
const input = {
  "mode": "searchWorks",
  "query": "example search",
  "maxResults": 20
};

const run = await ApifyClient.actor('crossref-scraper').call(input);
const { items } = await ApifyClient.dataset(run.defaultDatasetId).listItems();

console.log(items);
```

## Limits

- Maximum results per run: 1000
- Rate limiting: 50 req/sec (polite)

## Support

For issues or questions, contact the developer or open an issue on GitHub.

## License

Apache-2.0