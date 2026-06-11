[Crossref Scraper](https://apify.com/openclawmara/crossref-scraper?fpr=data)

# 🔗 Crossref Scraper — DOI Metadata for 150M+ Scholarly Works

**Structured metadata, citation counts, and author affiliations from the world's largest DOI registry. $0.004 per article.**

Scrape [Crossref](https://www.crossref.org) — the DOI registration agency for scholarly publishers — for titles, authors, DOIs, publication dates, journal info, citation counts, references, and funder data across 150M+ articles, books, datasets, and preprints.

Uses the official Crossref REST API. No auth required. Free for non-commercial use under Crossref's public data policy.

## 🚀 What does this Actor do?

Crossref is the backbone of academic citation infrastructure — almost every journal article, conference paper, book chapter, and dataset has a Crossref DOI. This Actor turns Crossref into a programmable source in two modes:

- **Search** — Full-text search by keyword across 150M+ works, with year range, citation count, and sort filters.
- **DOI lookup** — Bulk-fetch metadata for a list of DOIs you already have (bibliographies, reference lists, dataset citations).

Unlike Google Scholar (no API) or Semantic Scholar (focused on citations), Crossref is the **authoritative publisher metadata** — it's where the citation count originates, where the DOI resolves, and where the funder data lives.

## 💡 Use Cases

### 1. Systematic literature review automation

Pull every paper on a topic within a year range and feed the metadata into a structured review table.

```
{
  "searchQueries": ["retrieval augmented generation"],
  "maxResults": 500,
  "fromYear": 2022,
  "toYear": 2026,
  "sortBy": "published"
}
```

### 2. Citation graph building

You have a list of DOIs (from a bibliography, a dataset, a search result). Pull full metadata + reference lists.

```
{
  "dois": [
    "10.1038/s41586-023-06747-5",
    "10.1126/science.aap8731",
    "10.48550/arXiv.1706.03762"
  ]
}
```

### 3. Research analytics dashboard

Track publication volume and citation trends for a field, author, or publisher over time.

```
{
  "searchQueries": ["large language models"],
  "maxResults": 1000,
  "fromYear": 2020,
  "sortBy": "is-referenced-by-count",
  "minCitations": 10
}
```

### 4. Publisher / journal monitoring

Feed a Slack channel new publications in a domain, weekly.

```
{
  "searchQueries": ["CRISPR gene editing"],
  "maxResults": 100,
  "fromYear": 2026,
  "sortBy": "published"
}
```

## 📊 Output Example

```
{
  "doi": "10.1038/s41586-023-06747-5",
  "title": "A foundation model of transcription across human cell types",
  "authors": [
    { "given": "Xi", "family": "Fu", "affiliation": ["Columbia University"] },
    { "given": "Shentong", "family": "Mo", "affiliation": ["Carnegie Mellon University"] }
  ],
  "publishedDate": "2025-01-15",
  "publishedYear": 2025,
  "containerTitle": "Nature",
  "publisher": "Springer Science and Business Media LLC",
  "type": "journal-article",
  "volume": "637",
  "issue": "8047",
  "page": "965-973",
  "isReferencedByCount": 142,
  "referencesCount": 67,
  "url": "https://doi.org/10.1038/s41586-023-06747-5",
  "abstract": "The human genome contains...",
  "subject": ["Multidisciplinary"],
  "funder": [
    { "name": "National Institutes of Health", "award": ["R01HG012875"] }
  ],
  "issn": ["0028-0836", "1476-4687"],
  "license": [{ "URL": "https://creativecommons.org/licenses/by/4.0/" }]
}
```

## ⚙️ Input Parameters

| Parameter | Type | Description |
| --- | --- | --- |
| `searchQueries` | array | Keywords/phrases (e.g. `["CRISPR gene editing", "large language models"]`) |
| `dois` | array | Specific DOIs to fetch metadata for (e.g. `["10.1038/s41586-023-06747-5"]`) |
| `maxResults` | int | Results per query (default 50, max 1000) |
| `sortBy` | enum | `relevance` (default), `published`, `is-referenced-by-count` |
| `fromYear` | int | Only articles published from this year |
| `toYear` | int | Only articles published up to this year |
| `minCitations` | int | Only include articles with ≥ N citations (default 0) |

## 📤 Output Fields

| Field | Description |
| --- | --- |
| `doi` | Digital Object Identifier (canonical) |
| `title` | Article title |
| `authors[]` | `{ given, family, affiliation[] }` per author |
| `publishedDate`, `publishedYear` | ISO date + year |
| `containerTitle` | Journal / conference / book name |
| `publisher` | Publisher name |
| `type` | `journal-article`, `book-chapter`, `proceedings-article`, `dataset`, `preprint`, etc. |
| `volume`, `issue`, `page` | Bibliographic location |
| `isReferencedByCount` | Citation count (from Crossref) |
| `referencesCount` | Number of references in the article |
| `url` | DOI resolver URL |
| `abstract` | When available (~30% of articles) |
| `subject[]` | Subject categories |
| `funder[]` | Funder + award/grant IDs |
| `issn[]` | Journal ISSNs |
| `license[]` | Open-access license info when present |

## 💰 Pricing & Performance

- **Pay-per-event:** **$0.004 per article**.
- **Typical cost:** $4 for 1000 articles — a full systematic review for the price of a coffee.
- **Speed:** ~100–150 articles/minute via the official Crossref REST API.
- **No auth required** — Crossref API is fully open (with polite-pool pacing for sustained usage).
- **Bulk-friendly** — up to 1000 results per search query.

## 🔌 Integrations

- **Vector DBs (Pinecone, Weaviate, Qdrant, pgvector)** — embed titles + abstracts for semantic scholarly search.
- **LangChain / LlamaIndex** — power a "research assistant" RAG over a year-range corpus.
- **Neo4j / graph DBs** — build a citation network: `author → paper → references → paper`.
- **Zapier / Make / n8n** — weekly "new papers in my field" digest to Slack, email, or Notion.
- **Systematic review tools (Covidence, Rayyan)** — bulk-import metadata from a search.
- **Airbyte / Fivetran** — load structured metadata into a data warehouse for bibliometrics.

## 🧭 DOI Prefix Reference

- `10.1038` — Nature Publishing Group
- `10.1126` — AAAS (Science)
- `10.1145` — ACM
- `10.1109` — IEEE
- `10.48550` — arXiv preprints (yes, arXiv has DOIs too)
- `10.1101` — bioRxiv / medRxiv
- `10.21105` — Journal of Open Source Software
- Full prefix list: [https://www.crossref.org/getting-started/prefix/](https://www.crossref.org/getting-started/prefix/)

## ❓ FAQ

**Why use Crossref over Google Scholar?**
Google Scholar has no official API and aggressively blocks scrapers. Crossref has a free, well-documented REST API that returns canonical metadata — the same data Google Scholar uses under the hood.

**Crossref vs Semantic Scholar?**
Crossref = **authoritative publisher metadata** (title, authors, DOI, journal, date, basic citation count). Semantic Scholar = **enriched citation graph + influential-citation signal**. Use both for a complete picture — this Actor's `dois[]` mode pairs perfectly with the Semantic Scholar scraper.

**Does every article have an abstract?**
About 30% do. Crossref's abstract coverage depends on the publisher's metadata submission. For guaranteed abstracts, follow up with arXiv / PubMed / Semantic Scholar.

**Can I pull references (who this paper cites)?**
Partially — `referencesCount` is always returned; the full reference list is included when the publisher deposits it with Crossref (roughly half of articles). For guaranteed reference lists, use OpenCitations or the publisher's native API.

**What's the difference between `published` sort and `fromYear` filter?**
`sortBy: published` orders results newest-first. `fromYear`/`toYear` restricts the year range. Use them together for "newest papers in the last 3 years."

**Rate limits?**
Crossref requests you identify yourself for sustained high-volume usage (polite pool). The Actor handles this automatically — you just set `maxResults` and wait.

## 🔗 Companions

- [arXiv Paper Scraper](https://apify.com/Helpermara/arxiv-paper-scraper) — Preprints before they're officially published.
- [Semantic Scholar Scraper](https://apify.com/Helpermara/semantic-scholar-scraper) — Citation graphs and influence metrics.
- [ORCID Scraper](https://apify.com/Helpermara/orcid-scraper) — Author profiles and disambiguated publication histories.
- [DBLP Scraper](https://apify.com/Helpermara/dblp-scraper) — Computer science bibliography with clean author data.

## 🔑 Keywords

Crossref scraper, Crossref API, DOI lookup, DOI metadata, scholarly articles API, academic paper metadata, citation count scraper, bibliometrics data, systematic review automation, literature review scraper, journal article scraper, publisher metadata, publication tracking, citation graph, research analytics, scientific publication data, open science metadata, Crossref bulk export, DOI resolver API, scholarly search API, RAG over research papers.

## 📝 Changelog

- **v1.0** — Initial release. Keyword search + DOI lookup modes, year range filter, citation count filter, 3 sort modes, up to 1000 results per search.