---
title: "N0: News Orchestrator — Daily 'Find News' Workflow"
description: "Orchestrates the complete daily news pipeline: search top 5 visa news → triage → write → schema → crosslink → social → calendar"
---

# N0: News Orchestrator — Daily "Find News" Workflow

## Objective
Run the complete daily news operation with a single trigger: **"find news"**. This orchestrator searches for the top 5 visa-related news items for Indians, then runs them through the entire news content pipeline using all N1-N11 skills.

## Daily Workflow Overview

```
USER: "find news"
         │
         ▼
┌────────────────────────────────────────────────────────────┐
│  STEP 1: SEARCH                                           │
│  Search web for top 5 visa news items for Indian audience  │
│  (N1 source verification, N2 triage)                       │
├────────────────────────────────────────────────────────────┤
│  STEP 2: CLASSIFY & ROUTE                                  │
│  Score each item (🔴🟡🟢🔵⚪) and decide format          │
│  (N2 triage, N11 calendar check)                           │
├────────────────────────────────────────────────────────────┤
│  STEP 3: CREATE CONTENT                                    │
│  Write articles (N3), or add to digest (N4)                │
├────────────────────────────────────────────────────────────┤
│  STEP 4: STRUCTURED DATA                                   │
│  Add NewsArticle schema + meta tags (N5, N9)               │
├────────────────────────────────────────────────────────────┤
│  STEP 5: BRIDGE TO GUIDES                                  │
│  Crosslink to evergreen guides, flag for update (N6, N7)   │
├────────────────────────────────────────────────────────────┤
│  STEP 6: DISTRIBUTE                                        │
│  Generate social snippets + alerts (N10)                   │
├────────────────────────────────────────────────────────────┤
│  STEP 7: TRACK                                             │
│  Log to calendar, schedule pruning (N11, N7)               │
├────────────────────────────────────────────────────────────┤
│  STEP 8: REPORT                                            │
│  Summary of what was created, what was skipped             │
└────────────────────────────────────────────────────────────┘
```

## Step-by-Step Execution

### Step 1: Search — Find Top 5 Visa News
Trigger: User says "find news"

Actions:
```
1. Search web for:
   - "visa news for Indians today"
   - "visa policy change [country] 2026"
   - "latest visa update Indian passport"
   - "embassy news India visa"
   - "immigration update today"

2. Collect top 10-15 results (cast wider net, then filter)

3. For each result, capture:
   - Headline
   - Source URL
   - Source name
   - Date published
   - Brief summary (2-3 sentences)
```

### Step 2: Classify & Route
Load: **N2** (Breaking News Triage) + **N1** (Source Registry)

Actions:
```
1. For each of the 10-15 candidates, check:
   - Is the source in our registry? What's its tier?
   - What's the Indian audience impact? (high/medium/low/none)
   - What's the urgency? (breaking/today/this week/noise)

2. Score each item using N2 triage formula

3. Select TOP 5 items that pass the quality filter
   (skip items with untrusted sources, no Indian impact, or duplicates)

4. Route each selected item:
   🔴 Breaking → N3 standalone article (publish ASAP)
   🟡 High     → N3 standard article (today)
   🟢 Medium   → N4 weekly digest
   🔵 Low      → N4 weekly digest
   ⚪ Ignore   → Skip
```

### Step 3: Create Content
Load: **N3** (Inverted Pyramid Writing) + **N4** (News Roundup/Digest)

Actions:
```
For each 🔴/🟡 item:
  1. Open N3 writing template
  2. Write lead (5Ws1H — 2-3 sentences max)
  3. Write critical details (key numbers, dates, impact)
  4. Write Indian-specific impact section
  5. Cite sources per N1 rules
  6. Keep 400-1,000 words depending on complexity

For 🟢/🔵 items:
  1. Accumulate into weekly digest (N4 template)
  2. Each item = ~100-150 words max
  3. Summary table at top
```

### Step 4: Structured Data & SEO
Load: **N5** (NewsArticle Schema) + **N9** (Google News/Discover SEO)

Actions:
```
For each article created in Step 3:
  1. Generate NewsArticle JSON-LD schema
  2. Set correct datePublished / dateModified
  3. Add Open Graph + Twitter Card meta tags
  4. Check headline against Google News rules (< 20 words, no clickbait)
  5. Verify feature image specs (≥1200px, 16:9, no text overlay)
  6. Add News Sitemap entry (if published < 48 hours ago)
```

### Step 5: Bridge to Evergreen Guides + 🔔 Generate Alerts
Load: **N6** (News-to-Guide Bridging) + **N7** (News Expiry & Pruning)

Actions:
```
For each article:
   1. Identify which evergreen guides are affected
   2. Check if article contains FEE, TIMING, ELIGIBILITY, or DOCUMENT changes
      → If YES: This is a 🔔 GUIDE UPDATE ALERT (see N6 alert system)
   3. Add crosslinks from news → guides (2-3 per article)
   4. Flag guides for update (🔴 = 24hrs, 🟡 = 1 week, 🟢 = 2 weeks)
   5. 📁 SAVE ALERT TO updates/YYYY-MM-DD/ folder:
      - Create one .md file per affected guide
      - Create/update README.md summary in the dated subfolder
      - File contains: old vs. new values, sections to update, deadline, source link
   6. Generate alert banner for the daily report (Step 8)
   7. Schedule pruning date based on article type (N7 expiry table)
```

### Step 6: Social Snippets & Alerts
Load: **N10** (Social Snippet & Breaking News Alerts)

Actions:
```
For 🔴 items:
  - Twitter/X snippet (within 1 hour)
  - WhatsApp broadcast (within 2 hours)
  - Telegram post (within 1 hour)
  - Push notification (if high impact)

For 🟡 items:
  - Twitter/X snippet (same day)
  - Telegram post (same day)

For all items:
  - Add to weekly email roundup (N4)
```

### Step 7: Calendar & Tracking
Load: **N11** (News Calendar & Beat Planning)

Actions:
```
1. Log today's articles in the weekly calendar
2. Note any upcoming known events (budgets, reviews, deadlines)
3. Update publishing volume tracker
4. Reschedule any missed slots from previous days
```

### Step 8: Report Back — WITH 🔔 ALERTS AT TOP

The report MUST begin with any 🔔 Guide Update Alerts BEFORE the main summary. This ensures you never miss a guide update notification.

```
╔══════════════════════════════════════════════════════════╗
║          🔔  GUIDE UPDATE ALERTS — ACTION REQUIRED      ║
╠══════════════════════════════════════════════════════════╣
║                                                          ║
║  🔴 UK STUDENT VISA GUIDE needs update:                 ║
║     ╰─ Change: Financial requirement                    ║
║     ╰─ Old: £1,334/m → New: £1,483/m                    ║
║     ╰─ Deadline: 24 hours (by tomorrow)                 ║
║                                                          ║
║  🟡 CANADA PR GUIDE needs update:                       ║
║     ╰─ Change: New Tech Talent visa category            ║
║     ╰─ Deadline: 1 week                                 ║
║                                                          ║
║  ✅ SCHENGEN VISA GUIDE — No update needed               ║
║     (crosslink-only, no data change)                     ║
║                                                          ║
╚══════════════════════════════════════════════════════════╝

📰 DAILY NEWS REPORT — [Date]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ ARTICLES CREATED: 3
  - 🇬🇧 UK Student Visa Fee Increase → Published
  - 🇨🇦 Canada PR Pathway → Published
  - 🇪🇺 Schengen e-Visa Update → Published

📋 ADDED TO DIGEST: 2 items
  - 🇦🇺 Australia processing time update
  - 🇯🇵 Japan eVisa expansion

📤 SOCIAL SNIPPETS POSTED: 3
  - Twitter: 2
  - Telegram: 3
  - WhatsApp: 1 (breaking only)

📅 NEXT SCHEDULED: Friday digest
📋 PENDING GUIDE UPDATES: 2 (🔴 1, 🟡 1)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

💡 TIP: Say "update guide [name]" to update a flagged guide now.
    Say "remind me later" to push deadline to next session.
    📂 All alerts saved to: updates/2026-05-29/
```

## Output
- 3-5 news articles/digest items created per day
- All articles have schema, crosslinks, and social snippets
- Evergreen guides flagged for updates
- Calendar updated
- Daily summary report

## Quality Check
- [ ] Minimum 3 items published per day (target 5)
- [ ] All 🔴 items published within 2-4 hours of discovery
- [ ] Every article has NewsArticle schema
- [ ] Every article links to at least 1 evergreen guide
- [ ] Sources verified against N1 registry
- [ ] Indian impact section in every article
- [ ] Social snippets created for 🔴/🟡 items
- [ ] Guides flagged for update (with deadlines)
- [ ] Calendar updated
