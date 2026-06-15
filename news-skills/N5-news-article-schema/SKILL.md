---
title: "N5: News Article Schema & Google News Compliance — Visa News"
description: "Implement NewsArticle structured data, news sitemaps, and Google News Publisher Center requirements for visa news articles"
---

# N5: News Article Schema & Structured Data

## Objective
Ensure every news article is properly marked up with `NewsArticle` schema and meets Google News technical requirements. Without this, news articles won't appear in Google News, Top Stories, or Google Discover.

## Schema Type: NewsArticle

Every news article MUST use `NewsArticle` schema. Do NOT use `Article` or `BlogPosting` for time-sensitive news content.

### Complete NewsArticle Schema Template

```json
{
  "@context": "https://schema.org",
  "@type": "NewsArticle",
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://btwvisas.com/visa-news/uk-student-visa-fee-increase-2026"
  },
  "headline": "UK Increases Student Visa Financial Requirement for Indians — Effective June 2026",
  "url": "https://btwvisas.com/visa-news/uk-student-visa-fee-increase-2026",
  "datePublished": "2026-05-29T10:00:00+05:30",
  "dateModified": "2026-05-29T14:30:00+05:30",
  "description": "UK Home Office raises student visa maintenance requirement from £1,334 to £1,483 per month. Indian students must show additional £1,341 for 9-month courses.",
  "image": {
    "@type": "ImageObject",
    "url": "https://btwvisas.com/images/visa-news/uk-student-visa-2026.jpg",
    "width": 1200,
    "height": 675
  },
  "author": {
    "@type": "Person",
    "name": "Author Name",
    "url": "https://btwvisas.com/authors/author-name"
  },
  "publisher": {
    "@type": "Organization",
    "name": "BTWVisas",
    "url": "https://btwvisas.com",
    "logo": {
      "@type": "ImageObject",
      "url": "https://btwvisas.com/logo.png",
      "width": 600,
      "height": 60
    }
  },
  "dateCreated": "2026-05-29T09:00:00+05:30",
  "articleSection": "Policy Change",
  "inLanguage": "en",
  "keywords": "UK student visa, financial requirement, Indian students, visa fee increase, UK visa 2026",
  "about": {
    "@type": "Thing",
    "name": "UK Student Visa Financial Requirement"
  },
  "dateline": "New Delhi, India",
  "printColumn": "Visa News",
  "isAccessibleForFree": true,
  "hasPart": [
    {
      "@type": "FAQPage",
      "name": "Frequently Asked Questions",
      "mainEntity": [
        {
          "@type": "Question",
          "name": "How much more do Indian students need to show?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Indian students must show an additional £1,341 (approx. ₹1.45 lakhs) for a typical 9-month course."
          }
        }
      ]
    }
  ]
}
```

### Required vs. Optional Fields

| Field | Required | Notes |
|-------|----------|-------|
| `@type` | ✅ | Must be `NewsArticle` |
| `headline` | ✅ | Must match or be very close to the page H1 |
| `url` | ✅ | Canonical URL |
| `datePublished` | ✅ | When the article was first published (ISO 8601) |
| `dateModified` | ✅ | When the article was last updated (ISO 8601) |
| `description` | ✅ | Same as meta description |
| `image` | ✅ | Google requires images ≥ 1200px wide |
| `author` | ✅ | Person type with name and url |
| `publisher` | ✅ | Organization with name and logo |
| `articleSection` | ✅ | Section name (see below) |
| `inLanguage` | ✅ | Language code |
| `mainEntityOfPage` | ✅ | WebPage reference |
| `dateline` | ⚠️ Strongly recommended | Location of reporting |
| `printColumn` | ⚠️ Strongly recommended | Column/section name |
| `keywords` | 🟢 Optional | Comma-separated keywords |
| `about` | 🟢 Optional | What the article is about |
| `hasPart` | 🟢 Optional | Embedded FAQ or Q&A |
| `isAccessibleForFree` | 🟢 Optional | Set to `true` if free |

## Google News Image Requirements

Google News is strict about images. Follow these rules:

| Requirement | Specification |
|-------------|--------------|
| **Minimum width** | 1200px |
| **Aspect ratio** | 16:9 (landscape) or 4:3 |
| **Format** | JPEG, PNG, WebP |
| **Max file size** | 5MB |
| **No overlay text** | No text, logos, or watermarks on the image |
| **No promotion** | No "Apply Now" overlays or gifs |
| **Attribution** | Copyright/privacy notices should be in metadata, not on image |
| **Relevance** | Must be directly relevant to the article content |

## News Sitemap

Create a separate News Sitemap for Google News indexing.

### News Sitemap Template

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
        xmlns:news="http://www.google.com/schemas/sitemap-news/0.9">
  <url>
    <loc>https://btwvisas.com/visa-news/uk-student-visa-fee-increase-2026</loc>
    <news:news>
      <news:publication>
        <news:name>BTWVisas</news:name>
        <news:language>en</news:language>
      </news:publication>
      <news:publication_date>2026-05-29T10:00:00+05:30</news:publication_date>
      <news:title>UK Increases Student Visa Financial Requirement for Indians — Effective June 2026</news:title>
      <news:genres>Blog</news:genres>
      <news:keywords>UK student visa, visa fee, Indian students</news:keywords>
      <news:stock_tickers></news:stock_tickers>
    </news:news>
  </url>
</urlset>
```

### News Sitemap Rules

- Include ONLY articles published in the last 48 hours (Google ignores older)
- Max 1,000 URLs per News Sitemap
- Submit via `robots.txt` or Google Search Console
- Update the News Sitemap daily (or more frequently for breaking news)
- Remove articles older than 3 days from the News Sitemap

## Google News Publisher Center Requirements

To appear in Google News, your publication must:

1. **Be added to Google News:** Submit via Google News Publisher Center
2. **Have a clear publication name:** Consistent across site, schema, and Publisher Center
3. **Have a logo:** 600x60px minimum, transparent background preferred
4. **Have original content:** Google News penalizes aggregation-only sites
5. **Have bylines:** Clear author names on every article
6. **Have a contact page:** With physical address and contact information
7. **Have a privacy policy:** Linked in footer

## articleSection Values (Use Consistently)

Use one of these standardized section values for classification:

| Section | Description |
|---------|-------------|
| `Policy Change` | New rules, eligibility changes, policy updates |
| `Fee Update` | Visa fee changes, currency adjustments, service charges |
| `Processing Time` | Wait time changes, premium processing updates |
| `New Visa Launch` | New visa categories or pathways |
| `Application Process` | Form changes, biometric updates, document requirements |
| `Embassy News` | Embassy/consulate openings, closures, jurisdiction changes |
| `Roundup` | Weekly/bi-weekly digest articles |
| `Breaking News` | Urgent, immediate-effect announcements |

## Implementation Checklist

```html
<!-- In the <head> of every news article page: -->
<!-- 1. JSON-LD NewsArticle Schema -->
<script type="application/ld+json">
{ ... NewsArticle schema ... }
</script>

<!-- 2. Open Graph for Social Sharing -->
<meta property="og:type" content="article" />
<meta property="og:title" content="..." />
<meta property="og:description" content="..." />
<meta property="og:image" content="..." />
<meta property="article:published_time" content="2026-05-29T10:00:00+05:30" />
<meta property="article:author" content="..." />

<!-- 3. Twitter Card -->
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:title" content="..." />
<meta name="twitter:description" content="..." />
<meta name="twitter:image" content="..." />

<!-- 4. Meta Tags for News -->
<meta name="date" content="2026-05-29T10:00:00+05:30" />
<link rel="canonical" href="https://btwvisas.com/visa-news/..." />
```

## 🧠 Daily "Find News" Workflow Integration

When you say **"find news"** (N0 orchestrator), this runs automatically after writing:

```
For EVERY article created in Step 3 (N3/N4):

1. I generate the complete NewsArticle JSON-LD:
   - Fill datePublished = now, dateModified = now
   - Author = from author registry
   - Publisher = BTWVisas
   - articleSection = based on content type
   - image = use article feature image

2. I add to News Sitemap if article is < 48 hours old

3. I add Open Graph + Twitter Card meta tags

4. I validate with Google Rich Results Test mentally:
   - headline present ✓
   - datePublished with timezone ✓
   - image ≥ 1200px ✓
   - author with URL ✓
```

**Time spent in daily workflow:** ~3 min per article (generated from template)

## Output
For each news article:
- Complete `NewsArticle` JSON-LD schema
- News Sitemap entry
- Open Graph + Twitter Card meta tags
- Properly sized and formatted feature image (1200x675px, no text overlay)

## Quality Check
- [ ] `NewsArticle` schema validated with Google Rich Results Test
- [ ] `datePublished` and `dateModified` in ISO 8601 format with timezone
- [ ] Feature image ≥ 1200px wide, 16:9 ratio, no text overlay
- [ ] Author is a real person with a profile URL
- [ ] Publisher logo meets Google specs (600x60px)
- [ ] News Sitemap submitted via robots.txt or Search Console
- [ ] Open Graph tags present on the page
- [ ] Canonical URL set correctly
- [ ] Article listed in Google News Publisher Center
