---
title: "N1: News Source Registry & Credibility Scoring — Visa News"
description: "Maintain a structured database of official visa news sources with credibility scores for Indian audience relevance"
---

# N1: News Source Registry & Credibility Scoring

## Objective
Build and maintain a centralized registry of trusted visa news sources. Every source is scored for credibility, response time, Indian-audience relevance, and verification track record. No news article is published without at least one tier-1 source.

## Source Tier System

| Tier | Label | Description | Examples |
|------|-------|-------------|----------|
| **T1** | **Official Government** | Direct from embassy, immigration dept, ministry | `india.gov.in`, `canada.ca/immigration`, `uk.gov/home-office`, `uscis.gov` |
| **T2** | **Official Partners** | Authorized visa processors, IATA, UNWTO | `vfsglobal.com`, `visaforindia.org`, `iata.org` |
| **T3** | **Major News Wire** | Reuters, PTI, ANI, AP — original reporting | `reuters.com`, `ptinews.com`, `apnews.com` |
| **T4** | **Trusted Media** | Established outlets with visa/immigration desks | `timesofindia.indiatimes.com`, `hindustantimes.com`, `thehindu.com`, `bbc.com` |
| **T5** | **Industry Blogs** | Travel/visa industry analysis | Official travel industry publications, verified expert blogs |
| **✗ Untrusted** | **Do Not Cite** | Anonymous, no byline, clickbait, known misinformation | Unverified social media, anonymous forums, SEO spam sites |

## Source Entry Template

Each source in the registry must have:

```yaml
source_id: "uk-home-office-visa-news"
name: "UK Home Office — Visas and Immigration"
tier: T1
url: "https://www.gov.uk/government/organisations/home-office"
news_feed: "https://www.gov.uk/government/announcements.atom"
region: "UK"
topics: ["work-visa", "student-visa", "tourist-visa", "immigration-rules"]
language: "en"
indian_relevance: "high"     # high / medium / low
avg_response_time: "2-4 hours"  # How fast they publish policy changes
track_record: 98              # Percentage of accurate, uncorrected reports
last_verified: "2026-05-29"
notes: "Primary source for all UK visa policy changes. Cross-check with VFS Global for application-level impact."
```

## Credibility Scoring Formula

```
CREDIBILITY SCORE = (Tier Weight × 40%) + (Track Record × 30%) + (Indian Relevance × 20%) + (Response Speed × 10%)
```

| Factor | Weight | Scoring |
|--------|--------|---------|
| Tier Weight | 40% | T1=100, T2=85, T3=75, T4=60, T5=40 |
| Track Record | 30% | % of accurate stories over last 50 citations (0-100) |
| Indian Relevance | 20% | high=100, medium=65, low=30 |
| Response Speed | 10% | <1hr=100, <4hr=80, <24hr=60, >24hr=40 |

**Threshold:** Only sources with score ≥ 70 can be cited in news articles. Sources below 70 go into a "monitoring" list only.

## Source Registry Fields (Structured Database)

| Field | Type | Description |
|-------|------|-------------|
| source_id | string | Unique identifier |
| name | string | Display name |
| tier | enum | T1-T5 or Untrusted |
| base_url | string | Root URL |
| news_feed_url | string | RSS/Atom feed if available |
| api_endpoint | string | API for programmatic access (if available) |
| region | string | Country/region covered |
| topics | list | Visa topics covered |
| indian_relevance | enum | high / medium / low |
| avg_response_time | string | Typical delay between announcement and publication |
| track_record | int | % accuracy score (0-100) |
| credibility_score | int | Computed score (0-100) |
| last_verified | date | Date of last source verification |
| notes | text | Usage notes, caveats, special handling |
| contacts | list | Editor/PR contacts (if available) |

## Sourcing Rules for News

### Rule 1: Minimum Source Requirement
- **Breaking News:** At least 1 T1 source OR 2 corroborating T2-T3 sources
- **Regular News:** At least 1 T1-T2 source
- **Roundup/Digest:** At least 2 sources per item, cross-verified

### Rule 2: Cross-Verification Mandate
```
Before publishing ANY visa news:
1. Find the primary official source (T1)
2. Find at least 1 corroborating source (T2 or T3)
3. If sources conflict, DO NOT publish — flag for review
4. If only T3/T4 sources available, label as "unconfirmed" or "reporting"
```

### Rule 3: Source Attribution in Articles
```
✓ "The UK Home Office announced today that..."
✓ "According to a press release from VFS Global..."
✓ "Reuters reports that the Schengen area will..."

✗ "Sources say..." (anonymous — avoid unless verified journalist standard)
✗ "It is believed that..." (speculative — avoid)
✗ No attribution at all (unacceptable)
```

### Rule 4: Dead Link & Stale Source Check
- Verify all source URLs are still live at time of citation
- Archive key sources (save PDF or archive.org snapshot)
- Flag any source that has been silent for > 6 months for re-verification

## Source Review Schedule

| Review Type | Frequency | Action |
|-------------|-----------|--------|
| Quick check | Daily | Verify T1 sources still accessible, check for new announcements |
| Full audit | Weekly | Re-score all sources, add new sources, remove dead ones |
| Deep review | Monthly | Review track record scores, adjust tier assignments |
| Cleanup | Quarterly | Prune sources with consistently low credibility scores |

## Output
- A structured source registry (Google Sheet / JSON / Notion DB recommended)
- Each news article cites minimum source tier requirements
- Credibility score maintained and updated weekly
- Archive of cited sources (PDF or screenshots) for compliance

## 🧠 Daily "Find News" Workflow Integration

When you say **"find news"** (N0 orchestrator), here's how this skill is used:

```
1. As I collect news candidates from the web, I check each source against
   the registry to verify it's a known T1-T5 source
2. If a source is NOT in the registry:
   - I assign an estimated tier on the spot
   - Flag it for future registry addition
3. I ensure every article cites its source tier (T1-T4 only — never Untrusted)
4. Cross-verification: For any 🔴/🟡 item, I confirm the source is T1 or T2
```

**Time spent in daily workflow:** ~2 minutes (quick source check per item)

## Quality Check
- [ ] Every T1 source has been accessed and verified as live
- [ ] Credibility score calculated for each source in registry
- [ ] No Untrusted-tier sources cited in any article
- [ ] Cross-verification completed before publication
- [ ] Source archive stored for compliance/audit
- [ ] Weekly source audit on calendar
