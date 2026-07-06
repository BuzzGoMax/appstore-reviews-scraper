[Appstore Reviews Scraper](https://apify.com/thewolves/appstore-reviews-scraper?fpr=data)

![](https://images.apifyusercontent.com/Yx-NYEtcxmPSh-SALNATnEa0urUx_tv-pvQjwQ0iieo/w:1800/cb:1/aHR0cHM6Ly93d3cuZHJvcGJveC5jb20vc2NsL2ZpL3BydzE3am90dmV2Z3dzNTExYmo0Yy9hcHBzdG9yZS1yZXZpZXdzLmpwZWc_cmxrZXk9OWEwYnd4ZnZqYm05ejQ4bDh0cnJ5OWU0OSZkbD0x.webp)

# 🥃 Apple App Store Reviews Scraper API: Extract iOS App Reviews, Ratings & User Feedback by Country

The **App Store Reviews Scraper** by [The Wolves](https://apify.com/thewolves?fpr=yhdrb) is an Apify Actor that extracts user reviews, star ratings, review titles, app version data, reviewer profiles, and country-specific feedback from any Apple App Store listing. This **app store review scraper api** delivers 12 structured fields per review at speeds of **100-200 reviews per second** — with no proxy configuration required on your end.

**$0.10 per 1,000 reviews.** Extract iOS app reviews from the Apple App Store at scale. Target specific apps by ID or URL, filter by country, and collect reviews with titles, version data, and reviewer profiles. Flexible input — use App IDs with a country code, or paste direct App Store URLs.

Built by **The Wolves** — a pack of data scientists with over a decade of experience in web scraping and API development. We build scrapers the way data teams actually need them: rich output, precise filtering, and pricing that scales.

> **Apple API Limitation:** Maximum **500 reviews per country** per app. This is an Apple platform restriction that applies universally. To maximize coverage, run extractions across multiple countries.

**Pricing:** $0.10 per 1,000 reviews | **100-200 reviews/second** | **No proxy setup required**

---

## Table of Contents

1. What Does the App Store Reviews Scraper Do?
2. Features and Capabilities
3. Pricing
4. Input Parameters
5. Output Format and Data Fields
6. Custom Map Function
7. AI Agent Integration via MCP
8. The Wolves Scraper Pack
9. Demo Mode and Free Testing
10. Automated Scheduling and Monitoring
11. Quick Start Guide
12. Use Cases and Industries
13. Troubleshooting
14. Frequently Asked Questions
15. Contact

---

## What Does the App Store Reviews Scraper Do?

**App Store review extraction** is the automated process of collecting user reviews, ratings, feedback text, and metadata from iOS app listings on the Apple App Store. The App Store hosts over 1.8 million apps with millions of user reviews — making it a critical source of structured user feedback for iOS and macOS applications.

The **Wolves App Store Reviews Scraper** extracts structured review data from any App Store listing at scale. Each review includes the **review title** (a headline that often captures the user's core sentiment), **app version data** (which version the reviewer was using), and **country-specific feedback** — data points that are essential for global app intelligence and release-by-release tracking.

The dual input system gives you flexibility: use **App IDs with a country code** when you know exactly which apps and markets to target, or paste **direct App Store URLs** when working from browser searches or shared links.

### What You Get From Every Review

**Review Content and Rating**

- Full review text and review title (headline)
- Star rating (1-5)
- Publication date (ISO 8601)
- Direct review URL on iTunes

**App and Version Context**

- App ID (numeric App Store identifier)
- App version at time of review
- Country code of the App Store locale
- Parent review ID (for threaded review context)

**Reviewer Profile**

- Reviewer username
- Reviewer profile URL on iTunes

---

## Features and Capabilities

### Input Flexibility

| Input Type | Example | Best For |
| --- | --- | --- |
| **App ID + Country** | `appIds: ["389801252"]`, `country: "us"` | Targeting specific apps in specific markets |
| **Direct URL** | `https://apps.apple.com/us/app/instagram/id389801252` | Scraping from an App Store listing URL |

### Core Capabilities

- **High-Speed Extraction** — 100-200 reviews per second
- **Dual Input System** — Use App IDs with country codes, or paste direct App Store URLs
- **Global Coverage** — Extract reviews from any App Store country locale
- **Review Titles** — Capture both title and body text (unique to App Store reviews)
- **App Version Tracking** — See which version each reviewer was using
- **Parent Review IDs** — Thread context for review relationships
- **Reviewer Profiles** — Username and iTunes profile URL for each reviewer
- **No Proxy Required** — The scraper handles proxy rotation internally
- **Custom Map Function** — Transform output with custom JavaScript before saving
- **Multiple Export Formats** — JSON, CSV, Excel direct download
- **API Integration** — RESTful API for Python, Node.js, or any HTTP client

### Known Limitations

- **500 reviews per country** — Apple's API returns a maximum of 500 reviews per country per app. This is an Apple platform restriction, not a scraper limitation. To maximize coverage, run extractions across multiple countries.

---

## Pricing

### Pay-Per-Review Pricing

No subscriptions, no rentals, no minimum commitments. You pay only for the reviews you extract:

| Metric | Price |
| --- | --- |
| **Per 1,000 reviews** | $0.10 |
| **Per review** | $0.0001 |
| **Per 100,000 reviews** | $10.00 |

> **Example:** Extracting 500 reviews from 10 countries (5,000 reviews total) costs **$0.50**. Monitoring reviews from your top 20 competitor apps monthly keeps costs well under **$5.00**.

---

## Input Parameters

| Field | Type | Description | Default |
| --- | --- | --- | --- |
| `appIds` | array | App IDs from the App Store URL (exclude any trailing "id" part). Required if using `country` | `[]` |
| `country` | string | App Store country code to fetch reviews from. Required if using `appIds` | `us` |
| `startUrls` | array | Direct App Store URLs — scraping begins immediately from these endpoints | `[]` |
| `maxItems` | number | Maximum number of reviews to output | `Infinity` |
| `customMapFunction` | string | JavaScript function to transform each review object (transformation only, not filtering) | `null` |

### Input Examples

**Single App — US Store:**

```
{
    "appIds": ["389801252"],
    "country": "us",
    "maxItems": 500
}
```

**Multiple Apps — Competitive Comparison:**

```
{
    "appIds": ["389801252", "686449807", "835599320"],
    "country": "us",
    "maxItems": 500
}
```

**Direct URL — No App ID Needed:**

```
{
    "startUrls": [
        "https://apps.apple.com/ca/app/tiktok/id835599320"
    ],
    "maxItems": 500
}
```

**Multi-Country — Same App:**
Run separate extractions for each country to collect up to 500 reviews per locale. For example, extract US reviews first, then UK, then Canada — each run targets a different country code.

---

## Output Format and Data Fields

Each extracted review is a structured JSON object containing 12 fields. Here is a sample:

```
{
    "parentId": "10954854441",
    "id": "10954854441",
    "date": "2024-02-18T19:48:09-07:00",
    "userName": "@rorry59",
    "userUrl": "https://itunes.apple.com/ca/reviews/id648414842",
    "version": "33.2.1",
    "score": 5,
    "title": "Entertaining",
    "text": "What I like about TikTok the most is that ppl are allowed to bring their stories to a wide audience. Also some stories are very entertaining.",
    "url": "https://itunes.apple.com/ca/review?id=835599320&type=Purple%20Software",
    "country": "CA",
    "appId": "835599320"
}
```

### Complete Field Reference

| Field | Type | Description |
| --- | --- | --- |
| `parentId` | string | Parent review identifier (for threaded review context) |
| `id` | string | Unique review identifier |
| `date` | string | ISO 8601 review publication date |
| `userName` | string | Reviewer's display name |
| `userUrl` | string | Reviewer's iTunes profile URL |
| `version` | string | App version the reviewer was using |
| `score` | number | Star rating (1-5) |
| `title` | string | Review title (headline) |
| `text` | string | Full review body text |
| `url` | string | Direct link to the review on iTunes |
| `country` | string | App Store country code |
| `appId` | string | Numeric App Store application ID |

### Data Fields by Use Case

| Use Case | Key Fields |
| --- | --- |
| **iOS App Sentiment Analysis** | `text`, `title`, `score`, `date`, `country` |
| **App Store Optimization (ASO)** | `score`, `text`, `title`, `version`, `country` |
| **Release Impact Tracking** | `version`, `score`, `text`, `date` |
| **Competitive Benchmarking** | `appId`, `score`, `text`, `title`, `date` |
| **Global Market Research** | `country`, `score`, `text`, `date`, `appId` |
| **NLP Training Data** | `text`, `title`, `score` (as label) |

---

## Custom Map Function

Transform each review before it's saved to the dataset. The `customMapFunction` parameter accepts a JavaScript function that reshapes every review object. Use this to extract specific fields, rename properties, or compute derived values.

**Important:** The custom map function is for **transformation only**, not filtering. Do not use it for filtering purposes.

### Example: Flatten for Sentiment Analysis

```
(review) => ({
    app: review.appId,
    rating: review.score,
    headline: review.title,
    body: review.text,
    date: review.date,
    version: review.version,
    country: review.country,
    reviewer: review.userName
})
```

### Example: Extract for Cross-Platform Comparison

```
(review) => ({
    platform: "App Store",
    appId: review.appId,
    rating: review.score,
    text: review.text,
    title: review.title,
    date: review.date,
    country: review.country,
    reviewer: review.userName
})
```

---

## AI Agent Integration via MCP

Apify provides a hosted **Model Context Protocol (MCP) server** at `mcp.apify.com` that allows AI agents and LLM-based applications to discover and run Apify Actors as tools — including this App Store Reviews Scraper.

### What This Means

If you're building AI agents using Claude Desktop, VS Code with MCP support, or any framework that implements the MCP specification, you can give your agent the ability to extract App Store reviews autonomously. The agent can call this scraper as a tool, receive structured JSON results, and use them in downstream analysis — all without manual intervention.

### How to Connect

Add this scraper to your MCP client configuration:

```
https://mcp.apify.com?tools=thewolves/appstore-reviews-scraper
```

Or use the CLI for local development:

```
$npx @apify/actors-mcp-server --tools thewolves/appstore-reviews-scraper
```

### Use Cases for AI Agent Integration

- **Automated app monitoring** — An AI agent extracts new reviews after each app update, summarizes sentiment trends, and flags critical issues for the development team.
- **Cross-platform analysis** — Combine App Store reviews with Google Play reviews using the [Google Play Reviews Scraper](https://apify.com/thewolves/google-play-reviews-scraper?fpr=yhdrb) in a single agent workflow for unified iOS + Android reporting.
- **Multi-step research pipelines** — Extract reviews, classify by topic, compute satisfaction scores by version, and generate product recommendations — all in one agent session.

For full setup instructions, see the [Apify MCP documentation](https://docs.apify.com/platform/integrations/mcp).

---

## The Wolves Scraper Pack

All tools below are built and maintained by [The Wolves](https://apify.com/thewolves?fpr=yhdrb) — a pack of data scientists with over a decade of experience building high-performance scrapers and APIs. Powerful, easy to use, and priced for scale.

| Tool | Platform | Price | Best For |
| --- | --- | --- | --- |
| **App Store Reviews Scraper** | Apple App Store | $0.10/1K reviews | iOS app intelligence **(You are here)** |
| **[Google Play Reviews Scraper](https://apify.com/thewolves/google-play-reviews-scraper?fpr=yhdrb)** | Google Play | $0.10/1K reviews | Android app intelligence |
| **[TripAdvisor Reviews Scraper](https://apify.com/thewolves/tripadvisor-reviews-scraper?fpr=yhdrb)** | TripAdvisor | $0.50/1K reviews | Hospitality intelligence |
| **[Trustpilot Reviews Scraper](https://apify.com/thewolves/trustpilot-reviews-scraper?fpr=yhdrb)** | Trustpilot | $0.50/1K reviews | B2B/SaaS reputation analysis |

### App Store Reviews vs. Google Play Reviews

| Feature | App Store (This Tool) | Google Play |
| --- | --- | --- |
| **Platform** | iOS / macOS | Android |
| **Review titles** | Yes (headline + body) | Title field often null |
| **Parent review IDs** | Yes (`parentId` field) | No |
| **Max reviews per country** | 500 (Apple limitation) | No hard limit |
| **Speed** | 100-200 reviews/second | 100-200 reviews/second |
| **Country filtering** | `country` parameter | `country` parameter |

---

## Demo Mode and Free Testing

Free plan users can test this **App Store reviews scraper** in Demo Mode with a maximum of **10 items** per run. Demo Mode is designed to validate the output format, data quality, and field coverage before committing to larger runs.

**Demo Mode Limitations:**

- Maximum 10 reviews per run
- API access not available on Free plan
- Full functionality requires a [paid Apify plan](https://apify.com/pricing?fpr=yhdrb)

**How to Test:**

- Run the scraper with `maxItems: 10` to preview the output structure
- Verify that review titles, version data, and country codes are present
- Test with both `appIds` + `country` and `startUrls` input methods
- Confirm the `customMapFunction` works with your transformation logic

---

## Automated Scheduling and Monitoring

App reviews appear continuously. For **app publishers**, **game studios**, and **product managers**, automated recurring runs ensure you capture new user feedback as it's posted.

### Why Schedule Review Extraction?

- **Release monitoring** — Track user sentiment after each app update by comparing reviews before and after version changes
- **Continuous feedback loop** — Feed fresh reviews into product analytics dashboards
- **Competitor tracking** — Monitor competitor iOS app reviews weekly for feature gaps and user complaints
- **Rating trend analysis** — Detect rating drops before they impact App Store ranking
- **Agency reporting** — Automated data collection for client app performance dashboards

### How to Set Up Scheduled Runs

1. Open the Actor in Apify Console
2. Configure your input parameters (appIds, country, maxItems)
3. Click **Schedule** and set frequency (daily, weekly, after each release)
4. Optionally add a **webhook** to push new data to your pipeline

### Webhook Integration

Combine scheduled runs with webhooks to build fully automated review monitoring:

```
Scheduled Run -> New Reviews Extracted -> Webhook fires -> Your system receives data
```

Use webhooks to trigger:

- Slack alerts for 1-star reviews mentioning crashes or bugs
- Database updates with new review data
- Dashboard refreshes with latest sentiment metrics
- Jira ticket creation for critical user-reported issues

---

## Quick Start Guide

### For Non-Technical Users (Apify Console)

1. Go to **[App Store Reviews Scraper](https://apify.com/thewolves/appstore-reviews-scraper?fpr=yhdrb)** on Apify
2. Click **Try for free**
3. Enter an App ID (e.g., `389801252` for Instagram) in the `appIds` field
4. Set `country` (e.g., `us`) and `maxItems`
5. Click **Start** and wait for results
6. **Export App Store reviews to CSV** from the Storage tab

### For Developers (Python API)

```
from apify_client import ApifyClient
client = ApifyClient("YOUR_TOKEN")
run = client.actor("thewolves/appstore-reviews-scraper").call(run_input={
    "appIds": ["389801252"],
    "country": "us",
    "maxItems": 500
})
items = client.dataset(run["defaultDatasetId"]).list_items().items
```

### For Game Studios (Competitor Analysis)

```
{
    "appIds": ["YOUR_GAME_ID", "COMPETITOR_1_ID", "COMPETITOR_2_ID"],
    "country": "us",
    "maxItems": 500
}
```

> Extract 500 reviews from each game in a single run. The `appId` field in the output identifies which game each review belongs to, making competitive segmentation straightforward.

### For Cross-Platform Analysis (iOS + Android)

Run this scraper for App Store reviews, then run the [Google Play Reviews Scraper](https://apify.com/thewolves/google-play-reviews-scraper?fpr=yhdrb) for the same app on Android. Use matching `customMapFunction` outputs to normalize fields across platforms:

```
(review) => ({
    platform: "App Store",
    rating: review.score,
    text: review.text || review.title,
    date: review.date,
    country: review.country,
    appId: review.appId
})
```

---

## Use Cases and Industries

### iOS App Sentiment Analysis and NLP

Extract hundreds of App Store reviews with full text, titles, and star ratings for training sentiment classifiers, topic modeling, or aspect-based sentiment analysis. App Store reviews uniquely include **review titles** (headlines) that often summarize the user's core sentiment — providing a natural short-text label for NLP training alongside the full review body.

**Key fields:** `text`, `title`, `score`, `date`, `version`, `country`

### App Store Optimization (ASO)

Analyze review content to identify keywords users associate with your app. Track how ratings change across versions and countries. Discover what features drive positive reviews and what pain points cause negative ones. Review titles are particularly valuable for ASO — they often contain the exact phrases users search for in the App Store.

**Key fields:** `score`, `text`, `title`, `version`, `country`

### Game Publishing and Development

Game studios can extract reviews from their own titles and competitors across multiple countries. The `version` field enables release-by-release sentiment tracking — measure whether a balance patch improved player satisfaction or whether a monetization change triggered backlash. Multi-app extraction in a single run makes competitive analysis efficient.

**Key fields:** `appId`, `score`, `text`, `version`, `date`, `country`

### Product Management and Feature Prioritization

Feed review data into product analytics to identify the most-requested features and most-reported bugs. Cross-reference with `version` to track whether fixes in new releases actually improved user satisfaction. Review titles provide quick-scan summaries of user priorities.

**Key fields:** `text`, `title`, `score`, `version`, `date`

### Cross-Platform App Intelligence

Compare user sentiment between iOS (App Store) and Android (Google Play) for the same app. Identify platform-specific issues, feature gaps, and satisfaction differences. Combine with the [Google Play Reviews Scraper](https://apify.com/thewolves/google-play-reviews-scraper?fpr=yhdrb) for unified cross-platform dashboards.

**Key fields:** `appId`, `score`, `text`, `date`, `country`

### Global Market Research

Collect reviews from multiple App Store locales to understand how user sentiment varies by country. Cultural preferences, localization quality, and regional feature availability all affect reviews. Run separate extractions per country to build a comprehensive global dataset, then segment analysis by the `country` field.

**Key fields:** `country`, `score`, `text`, `date`, `appId`

---

## Troubleshooting

### Common Issues and Solutions

| Issue | Cause | Solution |
| --- | --- | --- |
| **Only 500 reviews returned** | Apple's API limit per country | This is an Apple platform restriction — run separate extractions for different countries to collect more |
| **Getting more results than requested** | High-speed extraction overshoots slightly | You are billed only for the number you requested, not the extra results delivered |
| **Missing data in output** | Results stored in Apify dataset | Navigate to the "Storage" tab and select "Download the results" or "Open in a New Tab" |
| **Empty results** | Invalid App ID format | Ensure you're using the numeric App ID (e.g., `389801252`), not the app name or bundle ID |
| **No results with appIds** | Missing `country` parameter | The `country` field is required when using `appIds` — set it to a valid country code |

### Performance Tips

- **Start small:** Test with `maxItems: 10` (Demo Mode) to validate your setup before scaling
- **Use both input methods:** Try `appIds` + `country` for targeted extraction, or `startUrls` for URL-based scraping
- **Multi-country strategy:** Run separate extractions per country to collect up to 500 reviews from each locale
- **Multiple apps in one run:** Provide multiple App IDs in the `appIds` array for competitive analysis
- **Monitor billing:** You are billed per review extracted, not per `maxItems` setting — if fewer reviews exist, you pay only for what's delivered

---

## Frequently Asked Questions

### What App Store review data can I extract?

Extract **review text**, **review titles** (headlines), **star ratings (1-5)**, **review dates**, **reviewer usernames**, **reviewer profile URLs**, **app version at review time**, **country codes**, **App Store IDs**, **parent review IDs**, and **direct review URLs** — all in structured JSON or CSV format.

### Can I export App Store reviews to CSV?

Yes. **Download App Store reviews** directly from Apify Console in JSON, CSV, or Excel format. This is ideal for spreadsheet analysis, database import, and product analytics dashboards.

### Can I scrape reviews from multiple apps at once?

Yes. Provide multiple App IDs in the `appIds` array (e.g., `["389801252", "686449807"]`). Each app's reviews are extracted within a single Actor run, with the `appId` field identifying which app each review belongs to.

### Why is there a 500-review limit per country?

This is an **Apple platform limitation**, not a scraper limitation. Apple's API returns a maximum of 500 reviews per country per app. To maximize your dataset, run separate extractions for different countries.

### Can I use App Store URLs instead of App IDs?

Yes. Use the `startUrls` parameter with direct App Store URLs. This is useful when you're working from browser searches or shared links and don't want to extract the numeric App ID manually.

### What is the parentId field?

The `parentId` field provides threaded review context — linking reviews to their parent review when applicable. This is useful for understanding review relationships and conversation threads.

### Can I use Python to scrape App Store reviews?

Yes. Full Python support via the Apify Client library. See the Quick Start Guide for Python integration with `client.actor("thewolves/appstore-reviews-scraper")`.

### Can AI agents use this scraper?

Yes. Through Apify's **Model Context Protocol (MCP) server**, AI agents built with Claude Desktop, VS Code, or any MCP-compatible framework can call this scraper as a tool. This enables automated app monitoring, cross-platform analysis, and multi-step research pipelines. See AI Agent Integration via MCP for setup details.

### How fast is the extraction?

**100-200 reviews per second**, depending on the app listing and Apple's response times. This scraper is optimized for maximum throughput with internal proxy management.

### Do I need to set up proxies?

No. This scraper handles all proxy rotation internally. You don't need to configure, purchase, or manage any proxy infrastructure.

### How is this different from the Google Play Reviews Scraper?

The **App Store Reviews Scraper** extracts iOS app reviews with review titles, parent review IDs, and reviewer profile URLs. The **Google Play Reviews Scraper** extracts Android app reviews with developer replies and feature-specific quality ratings. Use both for cross-platform app intelligence.

---

## Contact

**Built by [The Wolves](https://apify.com/thewolves?fpr=yhdrb)** — a pack of data scientists with over a decade of experience building scrapers and APIs. We build them powerful, we build them fast, and we price them fair.

For questions, feature requests, or support:

- **Discord:** Reach out to [Tommy the Wolf](https://discordapp.com/users/tommy_the_wolf) — always available

---

**Ready to extract App Store review data at scale?** At $0.10 per 1,000 reviews with 100-200 reviews/second, review titles, version tracking, and multi-country support, this **App Store Reviews Scraper API** by [The Wolves](https://apify.com/thewolves?fpr=yhdrb) delivers the iOS app intelligence data teams need. Start scraping today.