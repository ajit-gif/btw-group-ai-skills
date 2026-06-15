---
title: "N9: Google News / Discover Optimization — Visa News"
description: "Specific tactics for Google News inclusion, Top Stories, and Google Discover — separate from traditional SEO, focused on news-specific ranking signals"
---

# N9: Google News / Discover Optimization

## Objective
Optimize visa news content specifically for Google News (news.google.com), Top Stories in web search, and Google Discover (mobile feed). News SEO is fundamentally different from traditional SEO — it prioritizes recency, authority, bylines, and structured data over backlinks and keyword density.

## How Google News Ranking Differs from Web Search

| Factor | Traditional SEO | Google News SEO |
|--------|----------------|-----------------|
| **Primary signal** | Backlinks, authority, content quality | Recency, source authority, freshness |
| **Keywords** | Long-tail, informational intent | Headline keywords, breaking terms |
| **Content age** | Evergreen (months to years) | Hours to days (48-72 hours max) |
| **Backlinks** | Critical for ranking | Less important; timeliness matters more |
| **Bylines** | Nice to have | Required — articles without authors may be rejected |
| **Images** | Any size | ≥ 1200px, 16:9, no text overlay |
| **Structured data** | Article, FAQ, HowTo | NewsArticle (mandatory for News) |
| **URL structure** | Descriptive, keyword-rich | Doesn't matter much for News |
| **Publishing frequency** | Consistent (weekly) | High frequency (daily) |

## Google News Ranking Signals

### Signal 1: Recency & Freshness
```
The most important signal for Google News.

Rules:
□ Publish within 4 hours of the announcement for 🔴 news
□ Update articles with new information to signal freshness
□ Never publish old news as "new" — Google detects recycled content
□ Remove old articles from News Sitemap after 72 hours
□ Use datePublished (original) and dateModified (update) correctly

Tip: For a major announcement, publish a short "Developing" article
within 2 hours, then expand it as more details emerge.
```

### Signal 2: Source Authority
```
Google evaluates the publisher (btwvisas.com), not just the article.

Build news authority by:
□ Publishing consistently (minimum 3-5 news articles per week)
□ Getting cited by other news outlets (earn links from media)
□ Having a clear "About Us" page with physical address
□ Maintaining transparent correction policies (see N8)
□ Registering with Google News Publisher Center
□ Using consistent branding (name, logo) across all platforms
```

### Signal 3: Byline & Author Authority
```
Google News prefers articles with clear, verifiable authors.

Requirements:
□ Every article must have a named author (not "Staff" or "Editor")
□ Author must have a bio page with credentials
□ Author byline linked to author page via schema
□ Consider adding multiple authors for major stories:
    - Reporter: "By [Name]"
    - Contributor/Expert: "With analysis by [Immigration Expert]"
```

### Signal 4: Headline Quality
```
Google News has strict headline guidelines.

DO:
✓ Include the most important fact: "UK Raises Student Visa Financial Requirement to £1,483/month"
✓ Keep under 20 words (Google News truncates at ~110 characters)
✓ Use title case
✓ Be specific, not vague

DON'T:
✗ Clickbait: "You Won't Believe What UK Did to Visa Fees!"
✗ Vague: "Important Visa Update for Students"
✗ All caps: "BREAKING: UK VISA FEES INCREASED"
✗ Exaggeration: "Huge Shocking News for Visa Applicants"
✗ Question headlines: "Did UK Just Raise Visa Fees?"
```

### Signal 5: Article Body Quality
```
□ Lead paragraph must summarize the entire story (inverted pyramid)
□ Minimum 300 words for Google News consideration
□ No affiliate links in the article body
□ No excessive ads above the fold
□ Original reporting preferred over aggregation
□ Cite sources explicitly (Google News can detect original reporting)
```

## Google Discover Optimization

Google Discover is different from Google News. It's a mobile feed of personalized content.

### Discover vs. News

| Aspect | Google News | Google Discover |
|--------|-------------|-----------------|
| **Trigger** | User searches for news | User scrolls feed (topic interest) |
| **Content type** | Recent news only | Evergreen + news content |
| **Headline style** | Informative | Engaging + informative |
| **Images** | Required, 1200px | Critical — large, high-quality |
| **Freshness** | Essential | Less strict (days to weeks) |
| **User interest** | News topic | Broader interests (travel, visas) |

### Discover Best Practices

```
1. Use engaging, high-quality images (1200px+)
   - Bright, human-interest photos preferred
   - Avoid generic stock photos of flags/handshakes
   - No text overlay on images

2. Use engaging headlines (not just factual)
   - Good for News: "UK Raises Student Visa Maintenance to £1,483/month"
   - Good for Discover: "Applying for a UK Student Visa? Here's What Just Changed"

3. Publish consistently
   - Discover favors regularly updated publications
   - 1+ article per day minimum for Discover eligibility

4. Cover topics people follow
   - "visa for Indians" — high interest topic
   - "travel to Canada" — popular Discover topic
   - "study abroad" — recurring interest
```

## News Sitemap Management

### Daily Workflow
```
1. Generate News Sitemap with articles from last 48 hours
2. Validate the sitemap (no errors, correct URLs)
3. Submit via Google Search Console
4. Remove articles older than 48 hours (they'll be ignored anyway)

Note: Google News Sitemap is separate from your main sitemap.
Keep it focused on news content only.
```

### News Sitemap Rules Recap
- Max 1,000 URLs
- Only include articles published in last 48 hours
- Use `<news:publication_date>` correctly (ISO 8601 with timezone)
- Include `<news:genres>` — use "Blog" for most visa news, "PressRelease" only for verbatim official releases
- DO NOT include guides, pillar pages, or evergreen content

## Technical Requirements Summary

| Requirement | Specification | Impact if Missing |
|-------------|--------------|------------------|
| NewsArticle schema | JSON-LD on every news page | Won't appear in Google News |
| Author byline | Named author with bio page | Reduced inclusion rate |
| Feature image | ≥ 1200px, 16:9, no text overlay | Won't appear in Top Stories/Discover |
| News Sitemap | Submitted daily | Delayed indexing |
| datePublished | Correct ISO 8601 | Wrong dates → wrong positioning |
| dateModified | Updated when article changes | Stale articles stay in index |
| Publisher Center | Registered publication | Won't appear in Google News section |
| robots.txt | Must not block Google News bot | Won't be crawled |
| Canonical URL | Self-canonical | Duplicate content issues |

## Common Google News Rejection Reasons

| Rejection | Fix |
|-----------|-----|
| "Article does not appear to be news" | Ensure content has time-sensitive angle, update NewsArticle schema |
| "Image does not meet quality standards" | Use 1200px wide, 16:9, no text overlay |
| "No author information" | Add clear byline with author schema |
| "Duplicate content" | Ensure unique content, self-canonical |
| "Low quality content" | Increase word count (300+), add original analysis |
| "Publication not in Google News" | Register via Publisher Center |
| "Headline policy violation" | Fix headline (no clickbait, all caps, etc.) |

## Monitoring & Maintenance

| Task | Frequency | Tool |
|------|-----------|------|
| Check Google News inclusion | Daily | Search Console > Google News |
| Review Discover traffic | Weekly | Google Analytics > Discover reports |
| Validate article schema | Per article | Google Rich Results Test |
| Check News Sitemap health | Weekly | Search Console > Sitemaps |
| Review rejected articles | Monthly | Search Console > Google News > Rejected |
| Audit headlines for policy compliance | Monthly | Manual review |

## 🧠 Daily "Find News" Workflow Integration

When you say **"find news"** (N0 orchestrator), this runs alongside N5:

```
For every article created daily:
1. Headline check: < 20 words, no clickbait, title case ✓
2. Image check: ≥ 1200px, 16:9, no text overlay ✓
3. Byline check: named author with bio ✓
4. Article length: ≥ 300 words ✓
5. News Sitemap: updated with today's articles ✓

Weekly checks:
6. Review Google Search Console for rejected articles
7. Check Discover traffic in Google Analytics
8. Audit headlines for policy compliance
```

**Time spent in daily workflow:** ~2 min per article (quick checklist)

## Output
For each news article:
- Google News-compliant headline
- Properly formatted feature image (1200x675px, no text overlay)
- NewsArticle schema with all required fields
- News Sitemap entry (for articles < 48 hours old)
- Author byline with author schema

## Quality Check
- [ ] NewsArticle schema present and valid
- [ ] Headline under 20 words, no clickbait, no all caps
- [ ] Feature image ≥ 1200px wide, 16:9 ratio, no text overlay
- [ ] Author byline with link to author bio page
- [ ] Article ≥ 300 words
- [ ] News Sitemap updated (daily automation)
- [ ] Publisher Center registration current
- [ ] No rejected articles in Search Console (address any)
- [ ] Consistent publication frequency (3-5 articles/week minimum)
