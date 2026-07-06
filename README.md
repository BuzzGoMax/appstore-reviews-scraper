[Appstore Reviews Scraper](https://apify.com/benthepythondev/appstore-reviews-scraper?fpr=data)

# App Store Reviews Scraper

Scrape customer reviews from **any iOS or macOS app** on the Apple App Store. Extract ratings, review text, author information, app version, vote counts, and more.

## Features

- **Multi-App Support**: Scrape reviews from multiple apps in one run
- **Multi-Country**: Get reviews from 50+ country App Stores
- **Rich Data**: Ratings, titles, full review text, author info, app version
- **Vote Counts**: See which reviews are most helpful
- **Fast & Reliable**: Uses official iTunes RSS API - no browser needed
- **Flexible Input**: Use App IDs or full App Store URLs

## Use Cases

### App Store Optimization (ASO)

- Analyze review sentiment for your apps
- Track competitor review trends
- Identify common user complaints and feature requests

### Sentiment Analysis

- Build datasets for ML/NLP training
- Monitor brand perception over time
- Detect emerging issues early

### Competitor Research

- Compare review volume and ratings
- Analyze competitor weaknesses
- Track feature reception

### Market Research

- Analyze app categories
- Identify market gaps
- Track industry trends

## Input Options

| Parameter | Type | Description |
| --- | --- | --- |
| `appIds` | array | App Store app IDs (e.g., "333903271" for X/Twitter) |
| `appUrls` | array | Full App Store URLs (auto-extracts app ID) |
| `countries` | array | Country codes (e.g., "us", "gb", "de") |
| `maxReviews` | number | Max reviews per app/country (default: 500) |
| `sortBy` | string | "mostRecent" or "mostHelpful" |
| `delaySeconds` | number | Delay between requests (default: 0.5) |

### Finding App IDs

App IDs can be found in App Store URLs:

- `https://apps.apple.com/us/app/x/id333903271` - ID is `333903271`
- `https://apps.apple.com/app/instagram/id389801252` - ID is `389801252`

## Example Inputs

### Scrape Reviews for One App

```
{
  "appIds": ["333903271"],
  "countries": ["us"],
  "maxReviews": 500
}
```

### Scrape Multiple Apps

```
{
  "appIds": ["333903271", "389801252", "284882215"],
  "countries": ["us"],
  "maxReviews": 200
}
```

### Scrape from Multiple Countries

```
{
  "appIds": ["333903271"],
  "countries": ["us", "gb", "ca", "au", "de"],
  "maxReviews": 100
}
```

### Using App Store URLs

```
{
  "appUrls": [
    "https://apps.apple.com/us/app/x/id333903271",
    "https://apps.apple.com/us/app/instagram/id389801252"
  ],
  "countries": ["us"],
  "maxReviews": 300
}
```

## Output Format

Each review includes:

```
{
  "review_id": "10456789123",
  "app_id": "333903271",
  "app_name": "X",
  "author_name": "JohnDoe123",
  "author_uri": "https://itunes.apple.com/us/reviews/id12345678",
  "rating": 4,
  "title": "Great app but needs improvements",
  "content": "The app works well for basic usage. However, I wish they would add dark mode and better notification controls...",
  "version": "10.15.2",
  "vote_count": 42,
  "vote_sum": 38,
  "country": "US",
  "updated_date": "2024-01-15T10:30:00-07:00",
  "app_url": "https://apps.apple.com/us/app/x/id333903271"
}
```

## Supported Countries

50+ countries including: US, GB, CA, AU, DE, FR, ES, IT, JP, CN, KR, BR, MX, IN, RU, NL, SE, and many more.

## Limitations

- **~500 reviews per app/country**: Apple's RSS API limits to 10 pages of ~50 reviews each
- **Recent reviews only**: Historical reviews beyond the most recent ~500 may not be available
- **Public reviews only**: Cannot access reviews that users have made private

## How It Works

This scraper uses Apple's official iTunes RSS API endpoints:

- `/rss/customerreviews/id={app_id}/sortBy={sort}/page={page}/json`
- `/lookup?id={app_id}` for app metadata

No browser automation needed - fast, efficient, and reliable!

## Pricing

$2.00 per 1,000 reviews scraped

## Tips

1. **Start Small**: Test with `maxReviews: 10` first
2. **Multiple Countries**: Reviews vary significantly by region
3. **Sort Options**: Use "mostHelpful" for quality insights, "mostRecent" for latest feedback
4. **Combine Apps**: Scrape competitors together for comparison analysis

## Support

For issues or feature requests, contact the developer.