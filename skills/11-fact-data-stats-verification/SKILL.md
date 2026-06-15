---
title: "Fact, Data & Stats Verification — Official Sources Only"
description: "Verify every fact, data point, and statistic from official government or authoritative sources"
---

# Fact, Data & Stats Verification — Official Sources Only

## Objective
Verify that every factual claim, data point, statistic, and reference in the visa guide comes from an official, authoritative source. Remove any unverifiable claims. This is critical for EEAT and AI Overview citation.

## Source Hierarchy for Visa Content

```
TIER 1 — Official Government Sources (MUST USE)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
• .gov websites (canada.ca, gov.uk, uscis.gov, homeaffairs.gov.au)
• Embassy/consulate official websites
• Official visa application portals
• Ministry of External Affairs (India) — mea.gov.in
• Passport Seva (India) — passportindia.gov.in
• Bureau of Immigration (India) — boi.gov.in

TIER 2 — Authorized Service Providers
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
• VFS Global — vfsglobal.com (official visa processing partner)
• BLS International — blsindia.com
• TLScontact — tlscontact.com
• Official visa outsourcing partners

TIER 3 — Authoritative Secondary Sources
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
• Reputable news (Reuters, BBC, Times of India, The Hindu — only for policy news)
• International organizations (UN, WHO, IOM)
• Educational institutions (official university sites for student visa info)

TIER 4 — UNACCEPTABLE Sources
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✗ Other visa agency websites (unless quoting their verified data)
✗ Unverified forums (Reddit, Quora — use only as inspiration for user concerns, NOT as sources)
✗ Wikipedia (can use for background but not as primary source)
✗ AI-generated content without verification
✗ Personal blogs without credentials
✗ Outdated news articles (>1 year old for policy, >3 years for general)
```

## Verification Process

### Step 1: Identify Every Claim
Go through the entire visa guide and flag every factual statement:

```markdown
Examples of claims that need verification:
• "Canada PR processing time is 6-8 months"
• "US Student visa fee is $160"
• "IELTS score of 6.0 required for UK visa"
• "Bank balance must be CAD $20,635"
• "Biometrics valid for 10 years"
• "95% of Indian applicants get approved"
• "VFS centers in 9 Indian cities"
• "Application can be submitted online"
```

### Step 2: Verify Against Official Source
For each claim, find the official source:

```markdown
Claim: "Canada PR processing time is 6-8 months"
Verification:
✓ Source: IRCC official processing times tool
  URL: https://www.canada.ca/en/immigration-refugees-citizenship/services/application/check-processing-times.html
  Checked: 29 May 2026
  Result: CONFIRMED — Express Entry processing: 6 months (80% of applications)
  Note: Processing times vary by program. Specify "Express Entry" not general "Canada PR"
```

### Step 3: Document Verification Results

```markdown
## Fact Verification Log
| # | Claim | Source | Tier | Verified (Y/N) | Date | Action |
|---|-------|--------|------|----------------|------|--------|
| 1 | Canada PR processing 6-8 months | IRCC official | 1 | ✅ Y | 29/05/26 | Kept — updated to "6 months" |
| 2 | US visa fee $160 | travel.state.gov | 1 | ✅ Y | 29/05/26 | Kept |
| 3 | IELTS 6.0 for UK | gov.uk | 1 | ✅ Y | 29/05/26 | Kept — noted for different visa types |
| 4 | 95% approval rate | Not found | N/A | ❌ N | 29/05/26 | REMOVED — no official source |
```

### Step 4: Remove or Reword Unverifiable Claims

```markdown
If a statistic or claim CANNOT be verified from an official source:

OPTION 1: Remove entirely
  ❌ "95% of Indian applicants get approved for this visa"
  → Remove. No official source publishes this.
  → Replace with: "Approval rates vary. Check official statistics at [URL]"

OPTION 2: Add qualifier
  ❌ "The visa fee is $160"
  → If found: ✓ "The current visa fee is $160 as per [official source]"
  → If not found: "As of the latest available information from [source], the fee is..."

OPTION 3: Attribute to user experience (not official)
  "Many Indian applicants report that the interview focuses on..."
  → "Based on feedback from BTWVisas clients, common interview questions include..."
  → (Attribution to experience, not claimed as official statistic)
```

## Common Verification Gaps in Visa Content

| Common Issue | How to Fix |
|-------------|-----------|
| "Processing time: X months" without source | Add link to official processing tool |
| "Fee: $XXX" without date | Add "as of May 2026" and link to fee schedule |
| Approval rate claims | Remove unless from official published statistics |
| "Documents needed" without specifics | Link to official document checklist |
| "Requirements may change" warning | Add "Check official website for latest updates" |
| "X% of applicants" statistics | Only use if from official published data |
| Bank balance requirements | Verify against official financial capacity guidelines |
| Language test scores | Verify against official visa requirement page |

## Step-by-Step Verification Workflow

1. **Read through content** — Identify all factual claims
2. **Classify claims** — Fee? Time? Requirement? Percentage?
3. **Search official source** — Find the .gov/embassy page
4. **Cross-reference** — Check 2 sources minimum for critical data
5. **Document verification** — Log in verification table
6. **Update content** — Replace with verified data + citation
7. **Remove unverifiable** — Delete claims with no official source
8. **Add citations** — Append [Source: URL] after each claim
9. **Verify ALL internal links** — Test every btwvisas.com URL with webfetch/curl:
   - If URL returns 200 OK → keep as hyperlink
   - If URL times out or returns error → remove hyperlink, replace with plain text or phone/email CTA
   - Log each URL result in verification table
10. **Final check** — Re-read to ensure no unverified claims remain and no broken links exist

## Output
A verification report containing:
- Complete fact verification log (claim → source → confirmed/rejected)
- List of removed claims (with reason for removal)
- List of updated claims (old → new)
- All citations with working URLs and check dates
- Re-verification schedule (recommend quarterly review)

## Quality Check
- [ ] Every factual claim verified against official source
- [ ] No unverifiable statistics remain in content
- [ ] All citations link to Tier 1 or Tier 2 sources
- [ ] Fees, times, and requirements have "as of [date]" qualifiers
- [ ] All external links verified as working
- [ ] Unverifiable claims either removed or properly attributed
- [ ] Verification log completed and attached
- [ ] **All btwvisas.com internal links tested and confirmed live**
- [ ] **Broken btwvisas.com links replaced with plain text or official source alternatives**
- [ ] **Only verified working URLs remain in the final content**
