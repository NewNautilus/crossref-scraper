[Crossref Scraper](https://apify.com/parseforge/crossref-scraper?fpr=data)

![ParseForge Banner](https://images.apifyusercontent.com/wTxwbnRh8X878EoDysptDr1AzClsoPHSsuMaYGmWENw/w:1800/cb:1/aHR0cHM6Ly9naXRodWIuY29tL1BhcnNlRm9yZ2UvYXBpZnktYXNzZXRzL2Jsb2IvYWQzNWNjYzEzZGRkMDY4YjlkNmNiYTMzZjMyMzk2MmUzOWFlZDViMi9iYW5uZXIuanBnP3Jhdz10cnVl.webp)

# 📖 Crossref DOI Metadata Scraper

> 🚀 **Extract citation metadata for 155M+ DOIs from Crossref in seconds.** Search by query, filter by title, author, or DOI. No coding, no API keys required.

> 🕒 **Last updated:** 2026-04-23 · **📊 30+ fields** · **📚 155M+ DOIs indexed** · **🔍 Title, author, and free-text search**

Crossref is the largest DOI registration agency, indexing over **155 million** research papers, book chapters, conference proceedings, datasets, and preprints. This scraper connects to the Crossref Works API and returns structured citation metadata including titles, authors, publication dates, journals, DOIs, citation counts, abstracts, license information, and funding details. Whether you need metadata for a single DOI or want to search across the entire Crossref database, the scraper handles pagination and rate limiting automatically.

Researchers, librarians, and data analysts use this actor to build citation databases, verify publication records, analyze research trends, and enrich existing datasets with DOI metadata. Instead of querying the Crossref API manually and parsing JSON responses, you get clean, structured data exported as JSON, CSV, or Excel. Every record includes the full title, all authors with ORCID IDs when available, journal name, volume, issue, pages, publication date, license, funder information, and reference lists.

| 🎯 Target Audience | 💡 Use Cases |
| --- | --- |
| Academic researchers | Build citation databases for literature reviews |
| University librarians | Verify and enrich publication records |
| Bibliometric analysts | Analyze citation patterns and research impact |
| Data scientists | Enrich datasets with DOI metadata |
| Publishers | Track citations and references across journals |
| Grant managers | Verify publication records from funded research |

---

## 📋 What the Crossref Scraper does

- 🔍 **Free-text search** across titles, authors, and container titles in the 155M+ DOI database
- 📝 **Title-specific search** to find publications matching exact title keywords
- 👤 **Author search** to find all works by a specific researcher
- 🎯 **Single DOI lookup** to fetch full metadata for a specific publication
- 🔧 **Filter strings** to narrow results by type, date, ORCID, publisher, and more
- 📧 **Polite pool access** by providing an email for faster Crossref response times

The scraper queries the Crossref Works API, retrieves matching records, and extracts full citation metadata for each item. Results include the publication title, all authors (with ORCID IDs), journal or container title, volume, issue, pages, publication dates, DOI, license info, funder details, reference count, citation count, and direct links. Each record is timestamped and includes the content type (journal-article, book-chapter, etc.).

> 💡 **Why it matters:** Crossref's API returns complex nested JSON that requires parsing. This scraper flattens and normalizes the data, delivering clean records ready for spreadsheets, databases, or analysis tools. Add your email to get routed to Crossref's faster "polite pool."

---

## 🎬 Full Demo

*🚧 Coming soon...*

---

## ⚙️ Input

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| **maxItems** | integer | No | Max records to collect. Free: up to 10. Paid: up to 1,000,000 |
| **query** | string | No | Free text search across titles, authors, and journals |
| **queryTitle** | string | No | Match only within publication titles |
| **queryAuthor** | string | No | Match by author name |
| **filter** | string | No | Crossref filter string (e.g., "type:journal-article,from-pub-date:2024") |
| **doi** | string | No | Fetch metadata for a single DOI (overrides query) |
| **email** | string | No | Your email for Crossref's faster "polite pool" |

**Example 1: Free-text search**

```
{
  "query": "attention is all you need",
  "maxItems": 10
}
```

**Example 2: Filtered author search with date range**

```
{
  "queryAuthor": "Hinton, Geoffrey",
  "filter": "type:journal-article,from-pub-date:2020",
  "email": "your@email.com",
  "maxItems": 100
}
```

> ⚠️ **Good to Know:** Providing an email address routes your requests to Crossref's "polite pool," which has faster response times and higher rate limits. The filter field accepts Crossref filter syntax. See Crossref API docs for all available filter options.

---

## 📊 Output

### 🧾 Schema

| Emoji | Field | Type | Description |
| --- | --- | --- | --- |
| 📝 | title | string | Full publication title |
| 👥 | authors | array | Author names with ORCID IDs when available |
| 📅 | publishedDate | string | Publication date |
| 📖 | containerTitle | string | Journal or book title |
| 🆔 | doi | string | Digital Object Identifier |
| 🔗 | url | string | Direct URL to the publication |
| 📊 | volume | string | Journal volume |
| 📄 | issue | string | Journal issue |
| 📍 | pages | string | Page range |
| 🏢 | publisher | string | Publisher name |
| 🏷️ | type | string | Content type (journal-article, book-chapter, etc.) |
| 📊 | citationCount | number | Number of times cited |
| 📋 | referenceCount | number | Number of references in the work |
| 📄 | abstract | string | Abstract text (when available) |
| 🆔 | issn | array | ISSN identifiers |
| 🆔 | isbn | array | ISBN identifiers |
| ⚖️ | license | array | License information and URLs |
| 💰 | funder | array | Funding organizations and grant numbers |
| 🏷️ | subject | array | Subject classifications |
| 📅 | depositedDate | string | Date deposited in Crossref |
| 📅 | indexedDate | string | Date indexed by Crossref |
| 🔗 | references | array | List of referenced DOIs |
| ⏰ | scrapedAt | string | Collection timestamp |
| ⚠️ | error | string | Error message if processing failed |

### 📦 Sample records

 
 
 

---

## ✨ Why choose this Actor

| Feature | Details |
| --- | --- |
| 📚 155M+ DOIs | Access the full Crossref database of research publications |
| 🔍 Multi-field search | Query by title, author, free text, or specific DOI |
| 📊 Citation counts | Track how many times each work has been cited |
| 💰 Funding data | Identify funders and grant numbers for each publication |
| 🆔 ORCID support | Author identifiers included when available |
| ⚖️ License info | Know the access rights for each publication |
| 📧 Polite pool | Faster responses when you provide an email address |

> 📊 **Search across 155M+ DOIs and collect up to 1,000,000 records per run with full citation metadata.**

---

## 📈 How it compares to alternatives

| Feature | This Actor | Manual API Calls | Generic Scrapers |
| --- | --- | --- | --- |
| Automatic pagination | ✅ | Manual | ❌ |
| Polite pool routing | ✅ | Manual | ❌ |
| Citation count included | ✅ | ✅ | ❌ |
| Funding data extraction | ✅ | ✅ | ❌ |
| Structured JSON/CSV output | ✅ | JSON only | Varies |
| Bulk collection (1M+ records) | ✅ | Manual | ❌ |
| Scheduled recurring runs | ✅ | ❌ | ❌ |

Get structured citation metadata at scale without writing API code or managing pagination.

---

## 🚀 How to use

1. **Create an Apify account** - [Sign up free with $5 credit](https://console.apify.com/sign-up?fpr=vmoqkp)
2. **Open the Crossref DOI Metadata Scraper** - Navigate to the actor page on Apify
3. **Enter your search query** - Type keywords, an author name, or a specific DOI
4. **Add optional filters** - Set date range, publication type, or provide your email for faster responses
5. **Click Start** - The actor collects matching records and delivers structured citation data

> ⏱️ **A typical run with 10 records completes in under 30 seconds.**

---

## 💼 Business use cases

| **🎓 Academic Research**   - Build citation databases for systematic reviews - Track publication records for tenure evaluations - Analyze citation patterns across research fields - Verify DOI metadata for bibliographies | **📊 Bibliometric Analysis**   - Measure research impact by citation count - Map collaboration networks through co-authorship - Track publication trends by subject area - Compare publisher output across disciplines |
| --- | --- |
| **📚 Library Services**   - Enrich catalog records with DOI metadata - Verify publication details for acquisitions - Build subject-specific reference collections - Track open access availability by license type | **💰 Research Funding**   - Verify publication records of grant applicants - Track outputs from funded research programs - Identify high-impact journals for publication strategies - Monitor open access compliance by funder |

---

---

## 🌟 Beyond business use cases

Data like this powers more than commercial workflows. The same structured records support research, education, civic projects, and personal initiatives.

| ### 🎓 Research and academia     - Empirical datasets for papers, thesis work, and coursework - Longitudinal studies tracking changes across snapshots - Reproducible research with cited, versioned data pulls - Classroom exercises on data analysis and ethical scraping | ### 🎨 Personal and creative     - Side projects, portfolio demos, and indie app launches - Data visualizations, dashboards, and infographics - Content research for bloggers, YouTubers, and podcasters - Hobbyist collections and personal trackers |
| --- | --- |
| ### 🤝 Non-profit and civic     - Transparency reporting and accountability projects - Advocacy campaigns backed by public-interest data - Community-run databases for local issues - Investigative journalism on public records | ### 🧪 Experimentation     - Prototype AI and machine-learning pipelines with real data - Validate product-market hypotheses before engineering spend - Train small domain-specific models on niche corpora - Test dashboard concepts with live input |

## 🤖 Ask an AI assistant about this scraper

Open a ready-to-send prompt about this ParseForge actor in the AI of your choice:

- 💬 [**ChatGPT**](https://chat.openai.com/?q=How%20do%20I%20use%20the%20Crossref%20DOI%20Metadata%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)
- 🧠 [**Claude**](https://claude.ai/new?q=How%20do%20I%20use%20the%20Crossref%20DOI%20Metadata%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)
- 🔍 [**Perplexity**](https://perplexity.ai/search?q=How%20do%20I%20use%20the%20Crossref%20DOI%20Metadata%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)
- 🅒 [**Copilot**](https://copilot.microsoft.com/?q=How%20do%20I%20use%20the%20Crossref%20DOI%20Metadata%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)

## ❓ Frequently Asked Questions

### 💳 Do I need a paid Apify plan to run this actor?

No. You can start right now on the free Apify plan, which includes **$5 in free monthly credit**. That is enough to run this actor several times and explore the output before committing to anything. Paid plans unlock higher limits, more concurrent runs, and larger datasets. [Create a free Apify account here](https://console.apify.com/sign-up?fpr=vmoqkp) to get started.

### 🚨 What happens if my run fails or returns no results?

Failed runs are not charged. If the source site changes, proxies get rate-limited, or a specific input matches nothing, re-run the actor or open our [contact form](https://tally.so/r/BzdKgA) and we will investigate. You can also check the run log in the Apify console to see why the run stopped.

### 📏 How many items can I scrape per run?

Free users are limited to **10 items per run** so you can preview the output and confirm the actor works for your use case. Paid users can raise `maxItems` up to **1,000,000** per run. [Upgrade here](https://console.apify.com/sign-up?fpr=vmoqkp) if you need full scale.

### 🕒 How fresh is the data?

Every run fetches live data at the moment of execution. There is no cache or delay: the records you get reflect what the source returned at that moment. Schedule the actor to maintain a rolling snapshot of the data you need.

### 🧑‍💻 Can I call this actor from my own code?

Yes. Apify exposes every actor as a REST endpoint and ships first-class SDKs for [Node.js](https://docs.apify.com/sdk/js) and [Python](https://docs.apify.com/sdk/python). You can start a run, read the dataset, and handle webhooks from your own app in a few lines. All you need is your Apify API token.

### 📤 How do I export the data?

Every Apify dataset can be downloaded in one click from the console as CSV, JSON, JSONL, Excel, HTML, XML, or RSS. You can also pull results programmatically via the [Apify API](https://docs.apify.com/api/v2) or stream them into BigQuery, S3, and other destinations through built-in integrations.

### 📅 Can I schedule the actor to run automatically?

Yes. Use the Apify scheduler to run the actor on any cadence, from hourly to monthly. Results are saved to your dataset and can be delivered to webhooks, email, Slack, cloud storage, or automation tools such as Zapier and Make.

---

## 🔌 Automating Crossref Scraper

Integrate the Crossref Scraper into your workflow using the Apify API or client libraries.

**Node.js:**

```
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });
const run = await client.actor("parseforge/crossref-scraper").call({
  query: "attention is all you need",
  maxItems: 50,
  email: "your@email.com"
});
const { items } = await client.dataset(run.defaultDatasetId).listItems();
console.log(items);
```

**Python:**

```
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")
run = client.actor("parseforge/crossref-scraper").call(run_input={
    "query": "attention is all you need",
    "maxItems": 50,
    "email": "your@email.com"
})
items = list(client.dataset(run["defaultDatasetId"]).iterate_items())
print(items)
```

- 📖 [Apify API reference](https://docs.apify.com/api/v2)
- 🐍 [Python client docs](https://docs.apify.com/api/client/python)
- 📦 [Node.js client docs](https://docs.apify.com/api/client/js)

**Schedules:** Set up recurring runs to track new publications matching your query, monitor citation count changes, or build growing bibliometric datasets. Configure daily, weekly, or monthly schedules from the Apify Console.

## 🔌 Integrate with any app

- 🔗 **Make (Integromat)** - Connect citation data to Google Sheets, Notion, or any of 1,500+ apps
- 🔗 **Zapier** - Trigger workflows when new citation records are collected
- 🔗 **Slack** - Get notified when a Crossref data run completes
- 🔗 **Airbyte** - Stream citation metadata into your data warehouse
- 🔗 **GitHub** - Store citation datasets in repositories for version control
- 🔗 **Google Drive** - Automatically save CSV exports to shared folders

---

## 🔗 Recommended Actors

| Actor | Description |
| --- | --- |
| [PubMed Citation Scraper](https://apify.com/parseforge/pubmed-citation-scraper) | Extract publication metadata from PubMed for biomedical research |
| [OpenCitations Scraper](https://apify.com/parseforge/open-citations-scraper) | Collect citation networks and bibliographic metadata |
| [Open Library Scraper](https://apify.com/parseforge/open-library-scraper) | Search and download book data from the Internet Archive |
| [NASA Reports Scraper](https://apify.com/parseforge/nasa-reports-scraper) | Collect technical reports from NASA's NTRS database |
| [ROR Scraper](https://apify.com/parseforge/ror-scraper) | Collect research organization data from the Research Organization Registry |

> 💡 **Pro Tip:** Combine the Crossref Scraper with the PubMed Scraper to get both citation metadata and full biomedical abstracts for the same publications.

---

**🆘 Need Help?** [**Open our contact form**](https://tally.so/r/BzdKgA) and we will get back to you within 24 hours. We are happy to help with custom setups, integrations, or feature requests.

---

> **Disclaimer:** This actor is not affiliated with, endorsed by, or connected to Crossref. It accesses publicly available data through the Crossref Works API. Use responsibly and in accordance with Crossref's Metadata Terms of Use.