---
title: "N2: Breaking News Triage & Urgency Scoring — Visa News"
description: "Classify incoming visa news by urgency, impact for Indian travelers, and required action — prevent noise, prioritize what matters"
---

# N2: Breaking News Triage & Urgency Scoring

## Objective
Build a triage system that separates genuine breaking visa news from noise. Every incoming news item is classified by urgency, Indian-audience impact, and required action. This prevents wasted effort on low-impact stories and ensures critical updates are published within hours.

## News Classification Framework

### Dimension 1: Urgency Level

| Level | Label | Definition | Time to Publish | Example |
|-------|-------|------------|-----------------|---------|
| **🔴 Critical** | Breaking Now | Immediate policy change affecting current applicants | Within 2-4 hours | "UK increases financial requirement for Student Visa effective tomorrow" |
| **🟡 High** | Today's News | New announcement with future effective date | Within 24 hours | "Canada announces new PR pathway launching next month" |
| **🟢 Medium** | This Week | Development with moderate impact, non-urgent | Within 3 days | "Schengen introduces digital visa application pilot" |
| **🔵 Low** | Roundup Material | Minor update, clarification, or routine change | Weekly digest | "VFS center in Pune updates service hours" |
| **⚪ Ignore** | Noise | No Indian audience impact, unverified rumor, duplicate | Do not publish | "Third-party blog speculates about visa changes" |

### Dimension 2: Indian Audience Impact

| Impact | Definition | Score |
|--------|------------|-------|
| **High** | Directly changes eligibility, cost, or process for Indian applicants | 100 |
| **Medium** | Affects Indian applicants indirectly or partially | 60 |
| **Low** | Minimal or no impact on Indian travelers | 20 |
| **None** | Irrelevant to Indian audience | 0 |

### Dimension 3: Action Required

| Action | When | Output |
|--------|------|--------|
| **🚨 Publish Breaking Article** | 🔴 Critical + High/Medium impact | Full news article within 2-4 hours |
| **📰 Publish Standard Article** | 🟡 High + Any impact | Standard news article within 24 hours |
| **📋 Add to Digest** | 🟢 Medium / 🔵 Low | Include in weekly roundup |
| **🔗 Update Existing Guide** | Policy change on an existing guide topic | Flag evergreen guide for update |
| **🗑️ Skip** | ⚪ Ignore | No action |

## Triage Process

### Step 1: Detect
Monitor these channels continuously (or at least twice daily):

```
Primary Channels (check daily):
├── T1 source feeds (RSS/email alerts from embassies/immigration depts)
├── Google News alerts for ["visa" + "India" + "update" + "rule change"]
├── VFS Global / TLScontact announcements page
└── IATA travel centre updates

Secondary Channels (check weekly):
├── Twitter/X lists of immigration lawyers/officials
├── Reddit r/visas, r/immigration (trending only)
├── WhatsApp/Telegram visa groups (cross-verify before acting)
└── Industry newsletters (e.g., Fragomen, BAL)
```

### Step 2: Classify
For each detected item, answer:

```
1. Is this from a T1/T2 source?                          [Yes/No]
2. Does it change visa policy, fee, process, or eligibility? [Yes/No]
3. Does it affect Indian passport holders/applicants?     [Yes/No]
4. Is there an effective date mentioned?                  [Yes/Date]
5. Is this already covered by another news source?        [Yes/No/Maybe]
```

### Step 3: Score & Route

```
TRIAGE SCORE = Urgency (weight 50%) + Indian Impact (weight 40%) + Source Tier (weight 10%)

Routing:
- Score ≥ 80 → 🔴 Breaking — Publish ASAP
- Score 60-79 → 🟡 Standard Article — Publish today
- Score 40-59 → 🟢 Digest Material — This week
- Score 20-39 → 🔵 Low — Digest only
- Score < 20 → ⚪ Ignore
```

### Step 4: Confirm
Before publishing any 🔴 or 🟡 item:

```
□ Official source URL obtained and verified
□ Cross-checked with at least 1 other source
□ Effective date confirmed
□ Indian-specific impact analyzed
□ No contradiction with existing content
```

## Triage Decision Tree

```
Is it from a T1 or T2 source?
├── YES → Does it affect Indian applicants?
│   ├── YES → Is the change effective immediately or within 30 days?
│   │   ├── YES → 🔴 CRITICAL — Publish within 2-4 hours
│   │   └── NO  → 🟡 HIGH — Publish within 24 hours
│   └── NO  → 🟢 MEDIUM — Add to digest
└── NO → Is it corroborated by a T1 source?
    ├── YES → Follow same flow as above (label as "confirmed by [source]")
    └── NO → Can we confirm within 24 hours?
        ├── YES → Flag for follow-up, don't publish yet
        └── NO  → ⚪ IGNORE — Not worth the risk
```

## Breaking News Checklist (🔴 Critical)

When a 🔴 item is identified:

```
□ 1. Confirm source credibility (T1/T2)
□ 2. Cross-verify with second source
□ 3. Determine Indian-specific impact
□ 4. Identify which existing guides need updating
□ 5. Draft news article (see N3: Inverted Pyramid Writing)
□ 6. Add NewsArticle schema (see N5: News Article Schema)
□ 7. Internal review and publish
□ 8. Cross-link to relevant evergreen guides (see N6: News-to-Guide Bridging)
□ 9. Push notification / social alert (see N10: Social Snippet)
□ 10. Flag impacted guides for update
```

## 🧠 Daily "Find News" Workflow Integration

When you say **"find news"** (N0 orchestrator), this is the FIRST skill I load:

```
1. I search the web and collect 10-15 candidate news items
2. For EACH candidate, I run the triage:
   - Source tier? (N1 check)
   - Indian audience impact? (high/medium/low/none)
   - Urgency? (breaking/today/this week/noise)
3. I score each using the triage formula
4. I select the TOP 5 items that pass the filter
5. I route each:
   🔴→ Standalone article (ASAP)
   🟡→ Standalone article (today)
   🟢🔵→ Weekly digest
   ⚪→ Skip
6. I present you the 5 picks with my routing recommendation
```

**Time spent in daily workflow:** ~5 minutes (classify 10-15 candidates → pick top 5)

## Output
For each news item processed:
- Triage score and classification (🔴/🟡/🟢/🔵/⚪)
- Source verification status
- Indian impact analysis (2-3 sentences)
- Recommended action (article / digest / update / ignore)
- Deadline for publication

## Quality Check
- [ ] No 🔴 items published without T1 source or 2x corroboration
- [ ] Indian impact explicitly stated (not assumed)
- [ ] Triage score recorded before publication decision
- [ ] Existing content checked for contradiction
- [ ] Cross-linking to guides completed at publish time
- [ ] Source URLs archived for compliance
