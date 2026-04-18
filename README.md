# Tecnoempleo Scraper - Spain IT Jobs

Extract structured data from [tecnoempleo.com](https://tecnoempleo.com) — tecnoempleo.com - Spain's dedicated IT job board with 2,700+ active IT listings nationwide. Structured salary (min/max/period in EUR), skill taxonomy on every job, and incremental mode with repost detection for daily tracking.

**[Tecnoempleo Scraper - Spain IT Jobs on Apify →](https://apify.com/blackfalcondata/tecnoempleo-scraper?fpr=1h3gvi)**

---

## Key features

**Search with filters** — Search by keyword and location. Filter by work arrangement, and more.

**Detail enrichment** — Fetch full job descriptions, salary data, employer profiles, direct apply URLs for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

**Change classification** — Track unchanged, expired, cross-run repost detection across runs. Build audit trails of how listings evolve over time.

**Compact output** — Emit core fields only (AI-agent / MCP-friendly). Keeps response size small for LLM workflows.

**Description truncation** — Cap description length per listing to control output size and cost.

**Result cap** — Stop after N listings (up to 50.000). Set to 0 for the full catalog.

**Export anywhere** — Download as JSON, CSV, or Excel. Stream via Apify API, webhooks, or integrations with Make, Zapier, Airbyte, Keboola.

**Structured data** — Every listing returns the same schema with consistent field naming. All fields always present — `null` when unavailable, never omitted.

---

## Use cases

**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from tecnoempleo.com on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from tecnoempleo.com.

**Change monitoring**
Run daily or hourly in incremental mode to capture only new, updated, or expired listings. Perfect for price-tracking, churn analysis, and alerting pipelines.

**Compensation benchmarking**
Aggregate salary ranges across roles, industries, and locations on tecnoempleo.com to inform pricing decisions, hiring plans, or candidate negotiations.

**AI / LLM training data**
Structured JSON per listing is ready for RAG pipelines, embeddings, and agent workflows. Compact mode trims tokens for LLM context windows.

---

## Quick start

```json
{
  "query": "python",
  "maxResults": 10
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | — | Keyword or technology to search (e.g. 'python', 'sap', 'kubernetes'). Leave empty to browse all jobs. |
| `province` | string | — | Spanish province name (e.g. 'Madrid', 'Barcelona'). Leave empty for all provinces. |
| `en_remoto` | enum | `""` | Filter by remote / hybrid / on-site. |
| `professionalSkill` | string | — | Role category (e.g. 'Programador', 'Big Data', 'DevOps'). |
| `experience` | string | — | Minimum experience filter. |
| `salary` | string | — | Salary filter (site-specific value). |
| `workday` | string | — | Full-time / part-time / etc. |
| `contractType` | string | — | Indefinido / Temporal / Prácticas / etc. |
| `date_start` | string | — | Only return jobs posted on or after this date (YYYY-MM-DD). |
| `maxResults` | integer | `100` | Maximum total results to return (0 = unlimited, up to ~2,700 active listings). |
| `includeDetails` | boolean | `true` | Fetch full job details (HTML description, apply URL). Slower but richer output. |
| `descriptionMaxLength` | integer | `0` | Truncate description to N characters. 0 = no truncation. |
| `compact` | boolean | `false` | Core fields only — useful for AI-agent / MCP workflows. |
| `incrementalMode` | boolean | `false` | Compare against previous run state. Emits NEW/UPDATED jobs; suppresses UNCHANGED/EXPIRED unless enabled. |
| `stateKey` | string | — | Stable identifier for the tracked universe (required when incrementalMode is on). |
| `emitUnchanged` | boolean | `false` | Also emit jobs that have not changed since the last run. |
| `emitExpired` | boolean | `false` | Also emit jobs that have disappeared since the last run. |
| `skipReposts` | boolean | `false` | When incremental, skip jobs whose content matches an expired job from a prior run (cross-run repost detection). |

---

## Output fields

Every listing returns the same 50-field schema. Missing values are `null` — never omitted.

- `jobId`
- `jobKey`
- `title`
- `company`
- `companyUrl`
- `companyLogo`
- `companyId`
- `location`
- `province`
- `country`
- `workArrangement`
- `category`
- `technologies`
- `description`
- `descriptionText`
- `descriptionHtml`
- `descriptionMarkdown`
- `summary`
- `salaryText`
- `salaryMin`
- `salaryMax`
- `salaryCurrency`
- `salaryPeriod`
- `employmentType`
- `contractType`
- `hoursPerWeek`
- `experienceLevel`
- `educationLevel`
- `isUrgent`
- `isHighlighted`
- `isConfidential`
- `euWorkEligibilityRequired`
- `publishDate`
- `publishDateISO`
- `directApply`
- `url`
- `applyUrl`
- `portalUrl`
- `searchQuery`
- `contentQuality`
- `detailFetched`
- `scrapedAt`
- `source`
- `contentHash`
- `isRepost`
- `repostOfId`
- `repostDetectedAt`
- `originalPublishDate`
- `originalUrl`
- `changeType`

---

## Sample output

One object per listing. Here is a real example from a production run:

```json
{
  "jobId": "f6c1b838c92c236603368419dbfbd96a360a6791d70b05a445fe46b9da2875a3",
  "jobKey": "60d717c0e2e78364e44d",
  "title": "BI & Data Engineer",
  "company": "Geseme",
  "companyUrl": "https://www.tecnoempleo.com/geseme-trabajo/",
  "companyLogo": "https://www.tecnoempleo.com/logotipos/203877.png",
  "companyId": "203877",
  "location": "Barcelona",
  "province": "Barcelona (Híbrido)",
  "country": "España",
  "workArrangement": "HYBRID",
  "category": "Base de Datos/DBA - Big Data - Técnico de Sistemas"
}
```

*Truncated — full records contain 50 fields. See Output fields for the complete schema.*

**[Try Tecnoempleo Scraper - Spain IT Jobs now — $5 free credit, no credit card →](https://apify.com/blackfalcondata/tecnoempleo-scraper?fpr=1h3gvi)**

---

## Pricing

Pay only for what you extract. No subscription required — Apify's free $5 credit covers thousands of results.

| Event | Price (USD) |
| --- | --- |
| Actor Start | $0.01 |
| Result | $0.005 |

See the [actor on Apify](https://apify.com/blackfalcondata/tecnoempleo-scraper?fpr=1h3gvi) for current pricing.

---

## FAQ

**How do I scrape tecnoempleo.com?**
Use this actor on Apify to extract structured data from tecnoempleo.com. Configure your search query and filters in the input, then click Start — no coding required.

**How do I get tecnoempleo.com data as JSON, CSV, or Excel?**
The actor writes each listing to Apify's dataset. Download as JSON, CSV, or Excel from the Console, stream via the API, or push to Make, Zapier, Airbyte, or Keboola.

**Is it legal to scrape tecnoempleo.com?**
Web scraping of publicly available data is generally legal. This actor only accesses publicly visible information. Always check tecnoempleo.com's terms of service for your specific use case.

**How much does it cost?**
Pay-per-event pricing — you only pay for listings extracted. Apify's free $5 credit is enough to run thousands of results before you pay anything.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage. Expired listings can be tracked separately.

**Do I need an API key or credentials?**
No. Just sign up for Apify, paste your input, and click Start. No credit card required.

---

## Related products by Black Falcon Data

- [StepStone Scraper](https://apify.com/blackfalcondata/stepstone-scraper?fpr=1h3gvi) — Job listings from 18 European portals
- [Indeed Job Scraper](https://apify.com/blackfalcondata/indeed-job-scraper?fpr=1h3gvi) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://apify.com/blackfalcondata/glassdoor-job-scraper?fpr=1h3gvi) — Glassdoor listings with company ratings
- [Arbeitsagentur Scraper](https://apify.com/blackfalcondata/arbeitsagentur-scraper?fpr=1h3gvi) — Germany's official job portal (1M+ listings)
- [SEEK Scraper](https://apify.com/blackfalcondata/seek-scraper?fpr=1h3gvi) — Australia & NZ's largest job board
- [Naukri Scraper](https://apify.com/blackfalcondata/naukri-scraper?fpr=1h3gvi) — India's largest job portal

---

## Getting started with Apify

New to Apify? [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=1h3gvi) — no credit card required.

1. Sign up — $5 platform credit included
2. Open [Tecnoempleo Scraper - Spain IT Jobs](https://apify.com/blackfalcondata/tecnoempleo-scraper?fpr=1h3gvi) and configure your input
3. Click **Start** — export results as JSON, CSV, or Excel

Need more later? [See Apify pricing](https://apify.com/pricing?fpr=1h3gvi).

---

## About Black Falcon Data

Black Falcon Data builds production-grade web scrapers for job boards and marketplace data. Browse our full actor catalog at [www.blackfalcondata.com](https://www.blackfalcondata.com).

---

*Last updated: 2026 04*
