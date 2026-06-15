---
title: "N7: News Expiry & Content Pruning — Visa News"
description: "Track when news articles become stale and manage their lifecycle: redirect, merge into guides, or archive with historical markers"
---

# N7: News Expiry & Content Pruning

## Objective
News articles have a short shelf life. This skill manages the complete lifecycle: from publication → freshness → stale → archived/redirected. Prevents your site from becoming a graveyard of outdated news that hurts EEAT.

## News Article Lifecycle

```
PUBLICATION
    │
    ▼
FRESH (Days 1-3)          ← High traffic, featured in News Sitemap
    │
    ▼
ACTIVE (Days 4-14)        ← Still relevant, organic traffic
    │
    ▼
STALE (Days 15-30)        ← Low traffic, may contain dated info
    │
    ├──→ MERGE INTO GUIDE  ← Best outcome: enrich evergreen content
    ├──→ REDIRECT          ← If superseded by newer article
    └──→ ARCHIVE           ← Keep for reference, mark as "Historical"
```

## Expiry Timelines by Article Type

| Article Type | Fresh | Active | Stale | Action at Stale |
|-------------|-------|--------|-------|-----------------|
| 🔴 Breaking News | 1-2 days | 3-7 days | 8-14 days | Merge or redirect |
| 🟡 Standard Article | 2-3 days | 4-14 days | 15-30 days | Merge into guide |
| 🟢 Digest/Roundup | 3-5 days | 6-14 days | 15-30 days | Archive |
| 🔵 Minor Update | 1-2 days | 3-7 days | 8-14 days | Merge or redirect |
| ⚪ Seasonal (e.g., summer rush) | 7 days | 14-30 days | 30-90 days | Keep for next season |

## Pruning Actions

### Option A: Merge into Guide (Preferred)
When a news article contains useful information that should be permanently available:

```
When to merge:
- The policy change is permanent (not temporary)
- The guide doesn't already cover this information
- The news article has valuable detail the guide lacks

Process:
1. Open the relevant evergreen guide
2. Incorporate the news information into the appropriate section
3. Add a dated note: "As of [date], [summary of change]"
4. Update the guide's dateModified
5. Set up a 301 redirect from the news URL to the guide
6. OR keep the news article but add a prominent banner:
   "This information has been incorporated into our [Guide Name]"
```

### Option B: Redirect (When Superseded)
When a newer article covers the same story more accurately:

```
When to redirect:
- A more recent article supersedes this one
- The policy has changed again
- The information is no longer accurate

Process:
1. Create a 301 redirect from the old news URL to the newer article
2. OR redirect to the relevant evergreen guide
3. Add a note in the redirect mapping: "Superseded by [new URL] on [date]"
```

### Option C: Archive (When Historical Value)
When the article has historical reference value:

```
When to archive:
- The article documents a historical policy change worth preserving
- It provides context for understanding current policies
- It ranks well for niche historical queries

Process:
1. Add a visible banner at the top:
   "⚠️ Historical Article — This information may be outdated. 
    See our [Guide Name] for current requirements."
2. Remove from the News Sitemap
3. Remove from Google News (noindex if needed)
4. Keep in the main sitemap with lastmod date updated
5. Add `dateModified` reflecting the archival date
```

## Automated Pruning Schedule

| Check | Frequency | Action |
|-------|-----------|--------|
| **Daily** | Scan articles published > 3 days ago | Remove from News Sitemap |
| **Weekly** | Scan articles > 14 days old | Flag for pruning decision |
| **Bi-weekly** | Review all flagged articles | Execute merge/redirect/archive |
| **Monthly** | Full audit of all news content | Check for any missed articles |
| **Quarterly** | Review archived articles | Delete if no longer relevant |

## Pruning Decision Matrix

| Factor | Merge | Redirect | Archive | Delete |
|--------|-------|----------|---------|--------|
| Has unique content not in guides | ✅ | — | ✅ | — |
| Superseded by newer article | — | ✅ | — | — |
| Policy was temporary (e.g., COVID rule) | — | — | ✅ | — |
| Policy was reversed | — | ✅ | — | — |
| Content is thin / low value | — | ✅ | — | ✅ |
| Has backlinks / traffic | ✅ | ✅ | ✅ | — |
| No traffic, no backlinks | — | — | — | ✅ |

## How to Mark Archived Content

### Banner for Archived Articles
```markdown
> ⚠️ **Historical Article**
> 
> This article was published on [original date] and reflects visa rules
> at that time. Visa policies change frequently. For the most current
> information, please refer to our [Country/Type] Visa Guide.
```

### Meta Robots for Archived Articles
```html
<!-- If the article should NOT appear in search at all -->
<meta name="robots" content="noindex, follow" />

<!-- If the article should appear but not in Google News -->
<meta name="googlebot-news" content="noindex" />
```

## Pruning Log Template

| Article | Published | Age | Action | Destination | Completed | Notes |
|---------|-----------|-----|--------|-------------|-----------|-------|
| UK Student Visa Fee Increase | 2026-05-01 | 28 days | Merge | UK Student Visa Guide | 2026-05-29 | Fee info added to guide, 301 redirect set |
| Schengen e-Visa Pilot News | 2026-04-15 | 44 days | Archive | — | 2026-05-29 | Historical banner added, removed from News Sitemap |
| Canada PR Pathway Announcement | 2026-03-01 | 89 days | Redirect | Canada PR Guide 2026 | 2026-05-29 | Superseded by updated PR guide |

## 🧠 Daily "Find News" Workflow Integration

When you say **"find news"** (N0 orchestrator), this runs in the background:

```
During each daily session:
1. I check articles published 14+ days ago for pruning decisions
2. I recommend: merge / redirect / archive / keep
3. I update the pruning log

On digest day (Friday):
4. I scan all articles from the past 2 weeks
5. Flag candidates for merge into evergreen guides
6. Remove articles > 72 hours from News Sitemap
```

**Time spent in daily workflow:** ~5 min (quick scan of aging articles)

## Output
- Pruning log with decisions and completion dates
- Updated News Sitemap (articles > 3 days removed)
- Archived articles with historical banners
- Merge/redirect actions documented
- Monthly pruning report

## Quality Check
- [ ] News Sitemap contains only articles from last 48-72 hours
- [ ] No article older than 30 days is in the News Sitemap
- [ ] Every archived article has a visible historical banner
- [ ] All redirects are 301 (not 302 or meta refresh)
- [ ] Merged content is properly integrated (not just appended)
- [ ] Pruning log is up to date
- [ ] No broken links from pruning (redirects verified)
