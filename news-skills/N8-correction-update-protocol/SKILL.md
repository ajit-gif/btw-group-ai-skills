---
title: "N8: Correction & Update Protocol — Visa News"
description: "Workflow for publishing corrections, updates, and follow-ups without breaking SEO trust — includes editor's notes, version history, and transparency standards"
---

# N8: Correction & Update Protocol

## Objective
Establish a transparent, reader-first process for correcting errors and publishing follow-up updates. In visa news, inaccurate information can cause real harm (missed deadlines, wrong fees, application rejections). Corrections must be handled with urgency and full transparency.

## Types of Changes

| Type | Definition | Example |
|------|------------|---------|
| **Correction** | Fixing an error in the original reporting | "The fee is €90, not €100 as previously reported" |
| **Update** | New information that supplements the original article | "The effective date has been moved to July 1st" |
| **Clarification** | Adding context that was missing | "This applies to first-time applicants only" |
| **Follow-up** | A new development on the same story | "UK Home Office releases detailed guidance on the new rule" |
| **Retraction** | The original article was entirely wrong | "The announced policy change has been postponed indefinitely" |

## Severity Levels

| Level | Definition | Response Time | Action |
|-------|------------|---------------|--------|
| **🔴 Critical** | Incorrect information that could cause financial loss or application rejection | Within 2 hours | Immediate correction + notification + social post |
| **🟡 High** | Incorrect information that could cause confusion or inconvenience | Within 24 hours | Correction with editor's note |
| **🟢 Medium** | Missing context or minor inaccuracy | Within 3 days | Update with clarification |
| **🔵 Low** | Typo, formatting, or non-material error | Next working day | Fix without formal note (unless reader-facing) |

## Correction Workflow

### Step 1: Detect & Triage
```
How an error is detected:
□ Internal review before publication (prevent)
□ Reader comment or email report
□ Social media flag
□ Source issued a correction
□ Staff identified the error

Severity assessment:
□ Could this cause a reader to lose money, miss a deadline, or get rejected?
□ Is the error in a critical fact (fee, date, requirement) or minor (spelling)?
□ How many people have already read/seen the error?
```

### Step 2: Fix the Content
```
1. Make the correction in the article
2. Update the dateModified in schema
3. Add a visible correction note at the TOP of the article
4. If the headline contains the error, add "(Corrected)" or update the headline
5. Update the meta description if needed
```

### Step 3: Add Correction Note

**For 🔴 Critical corrections:**
```markdown
> ⚠️ **Correction — [Date]**
> 
> This article originally stated that the UK student visa maintenance
> requirement increased to £1,834/month. The correct figure is
> **£1,483/month**. We regret this error. The article has been corrected.
> [Source link to official announcement]
```

**For 🟡 High corrections:**
```markdown
> 📝 **Correction — [Date]**
> 
> A previous version of this article stated the effective date as
> 1 May 2026. The correct effective date is **1 June 2026**.
> We regret the error.
```

**For 🟢 Medium updates/clarifications:**
```markdown
> ℹ️ **Update — [Date]**
> 
> This article has been updated to clarify that the new rule applies
> to first-time applicants only. Existing applicants are not affected.
```

### Step 4: Notify Readers (if 🔴 Critical)
```
Channels to use:
□ Update the article (immediate)
□ Social media correction post
□ Email notification (if you have subscribers)
□ Push notification (if using an app)
□ WhatsApp/Telegram broadcast (if you have channels)

Social correction post template:
"⚠️ CORRECTION: Our earlier article on UK student visa fees
contained an error. The correct maintenance amount is £1,483/month
(not £1,834). We apologize for the error. Full correction: [URL]"
```

### Step 5: Log the Correction

```yaml
correction_id: "CORR-2026-001"
article: "UK Student Visa Financial Requirement Increase"
article_url: "https://btwvisas.com/visa-news/uk-student-visa-fee-increase-2026"
error_type: "Factual error (fee amount)"
severity: "🔴 Critical"
detected: "2026-05-29T10:30:00+05:30"
corrected: "2026-05-29T11:00:00+05:30"
root_cause: "Misread official source table row"
action_taken: "Corrected amount, added correction note, posted social correction"
preventive_action: "Added dual-verification step for all numeric values before publication"
status: "closed"
```

## Update Protocol (Non-Correction)

When new information becomes available on an existing news story:

### Step 1: Assess
```
- Is the new information significant enough to update the article?
- Or should it be a new follow-up article?
```

### Decision Matrix

| Scenario | Action |
|----------|--------|
| Minor detail added (e.g., more centers) | Update existing article |
| Major change (e.g., date moved) | Update + add "Updated" note |
| Completely new policy direction | New follow-up article + link to original |
| Original article < 48 hours old | Update is usually sufficient |
| Original article > 7 days old | Consider new article with "Update" prefix |

### Step 2: Add Update Note
```markdown
> 📰 **Update — [Date]**
> 
> [New information]. See our follow-up: [link] for full analysis.
```

### Step 3: Cross-Link
- Add a link from the original article to the follow-up
- Add a link from the follow-up to the original ("Previously: ...")
- Update Google News Sitemap if the original was in it

## Retraction Protocol

For articles that are entirely wrong:

### Step 1: Assess
```
- Is every major claim in the article wrong?
- Was the source misinformation?
- Did the policy change before the article was published?
```

### Step 2: Retract
```markdown
> 🚫 **Retraction — [Date]**
> 
> This article has been retracted because [reason]. The information
> published was based on [source]. We have confirmed that [correct
> facts]. We apologize to our readers for this error.
> 
> For accurate information, please refer to [Correct Source URL]
> or our [Visa Guide Name].
```

### Step 3: Technical Actions
- Update `robots` meta to `noindex, follow` (keep for transparency)
- Remove from News Sitemap
- Remove from Google News
- Add `301 redirect` only if there's a clear replacement article
- Keep the retracted article accessible with the retraction banner

## Version History

Maintain a simple version log at the bottom of each news article:

```markdown
---
**Version History**

v1 — 2026-05-29 10:00 — Published
v2 — 2026-05-29 11:00 — Corrected fee amount (see correction note above)
v3 — 2026-05-30 09:00 — Added official source clarification
---
```

## Preventive Measures

| Measure | Description | Frequency |
|---------|-------------|-----------|
| Pre-publication fact check | Verify all numbers, dates, and names against source | Every article |
| Dual verification | Two team members must verify 🔴 articles | 🔴 articles only |
| Source comparison | Cross-check against official .gov source before citing news wires | Every article |
| Second-read rule | All 🔴/🟡 articles get a second read before publish | 🔴/🟡 articles |
| Post-publish review | Re-read article 1 hour after publish with fresh eyes | 🔴 articles |

## 🧠 Daily "Find News" Workflow Integration

When you say **"find news"** (N0 orchestrator), this is ON-DEMAND only:

```
Used when:
- A reader reports an error in a news article
- I discover a mistake during the daily workflow
- The source has issued a correction

If a correction is needed:
1. I assess severity (🔴/🟡/🟢/🔵)
2. I fix the article and add a correction note
3. I update dateModified
4. I post social correction (if 🔴)
5. I log the correction

This skill is NOT run daily — only when an error is detected.
```

**Time spent in daily workflow:** 0 min (on-demand only)

## Output
- Corrected article with visible correction note and version history
- Correction log entry
- Social media correction post (if 🔴 Critical)
- Preventive action documented
- Follow-up article cross-linked (if applicable)

## Quality Check
- [ ] 🔴 Critical corrections published within 2 hours of detection
- [ ] Correction note visible at the top of the article (not buried)
- [ ] Version history updated
- [ ] dateModified updated in schema
- [ ] Social correction posted (if 🔴)
- [ ] Reader notified via appropriate channels (if 🔴)
- [ ] Root cause documented and preventive action in place
- [ ] Retractions: noindex set, News Sitemap removed, banner visible
