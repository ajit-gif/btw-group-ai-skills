---
title: "Create Visa Guide — Full Workflow Orchestrator"
description: "Orchestrates the complete visa guide content pipeline from research to final output"
trigger: "create visa guide"
mode: "primary"
temperature: 0.3
---

# Create Visa Guide — Orchestrator Skill

## Trigger
When the user says **"create visa guide"** or mentions creating a visa content piece, invoke this orchestrator.

## Objective
Produce a complete, publication-ready visa guide (in `.md` and `.docx` formats) that:
- Ranks in Google search + AI Overviews
- Targets Indian audiences applying for visas
- Balances informational + commercial intent
- Complies with EEAT and 2026 Google standards
- Includes Indian-audience-optimized CTAs

## Workflow Pipeline (Execute in Order)

### Phase 1: Foundation Research
1. **Keyword Research** → `.opencode/skills/01-keyword-research/SKILL.md`
2. **User Intent Mapping** → `.opencode/skills/02-user-intent-mapping/SKILL.md`
3. **Competitor Content Analysis** → `.opencode/skills/03-competitor-analysis/SKILL.md`
4. **SERP Analysis** → `.opencode/skills/04-serp-analysis/SKILL.md`
5. **Topic Cluster Strategy** → `.opencode/skills/05-topic-cluster-strategy/SKILL.md`

### Phase 2: Content Engineering
6. **Latest Updates (2026)** → `.opencode/skills/06-latest-updates/SKILL.md`
7. **Meta Title & Meta Description** → `.opencode/skills/07-meta-title-description/SKILL.md`
8. **Content Generation** → `.opencode/skills/08-content-generation/SKILL.md`
9. **Keyword Placement** → `.opencode/skills/09-keyword-placement/SKILL.md`

### Phase 3: Quality & Trust
10. **EEAT SEO Checking** → `.opencode/skills/10-eeat-checking/SKILL.md`
11. **Fact, Data, Stats Verification** → `.opencode/skills/11-fact-data-stats-verification/SKILL.md`
12. **Internal Linking (btwvisas.com)** → `.opencode/skills/12-internal-linking/SKILL.md`

### Phase 4: AI & User Optimization
13. **AI Overview & LLM Optimization** → `.opencode/skills/13-ai-overview-llm-optimization/SKILL.md`
14. **FAQ Schema & Structured Data** → `.opencode/skills/14-faq-schema-structured-data/SKILL.md`
15. **Indian Audience CTA Optimization** → `.opencode/skills/15-indian-audience-cta/SKILL.md`
16. **Mobile-First Readability Check** → `.opencode/skills/16-mobile-first-readability/SKILL.md`

### Phase 5: Final Polish
17. **Grammar Check / Plagiarism Check** → `.opencode/skills/17-grammar-plagiarism-check/SKILL.md`
18. **Human Touch** → `.opencode/skills/18-human-touch/SKILL.md`
19. **Content Differentiation** → `.opencode/skills/19-content-differentiation/SKILL.md`

### Phase 6: Production & Verification
20. **Link Verification** — Test EVERY btwvisas.com URL using `curl -s -o /dev/null -w "%{http_code}" <url>`:
    - 200 OK → safe to add as hyperlink
    - 301/302 → follow redirect. If final destination is 200, acceptable
    - 404 → DO NOT link. Replace with phone/email plain text or alternative working page
21. **.docx Conversion** — Run the converter script to produce Word output:
    ```powershell
    python "visa guide/convert_md_to_docx.py" "visa guide/markdown/{filename}.md" "visa guide/word/{filename}.docx"
    ```
22. **Final Verification** — Open the .docx and check:
    - Headings are using Word heading styles (not plain text)
    - Bold/italic formatting preserved
    - Hyperlinks are clickable
    - Tables are properly formatted
    - Every link leads to a live, working page

## Output Requirements

### File Formats
| Format | Location | Description |
|--------|----------|-------------|
| `.md` | `visa guide/markdown/{visa-type}-visa-guide.md` | Master markdown with all formatting |
| `.docx` | `visa guide/word/{visa-type}-visa-guide.docx` | Word document for client/submission |

### Converter Script
Located at: `visa guide/convert_md_to_docx.py`
Usage: `python convert_md_to_docx.py <input.md> [output.docx]`
Handles: **bold**, *italic*, `code`, [links](url), headings, lists, tables, blockquotes, horizontal rules

### Content Structure (Every Visa Guide Must Include — Verified Structure)
```
# {Country} Visa for Indians 2026: Fees, Process & Types — BTWVisas

> AI Overview Extraction Block (visible blockquote)
> - Definition of the visa
> - Key 2026 updates
> - Quick facts (fee, processing, requirements)

## Quick Overview Table
- 10-row table with visa type, fee, processing, centers, etc.

## What is [Visa Type]?
- Definition-first paragraph
- Indian context
- BTWVisas linked from homepage (branded anchor, verify link works first)

## Do Indians Need a Visa?
- Yes/No answer
- What's available (✓) and not available (✗)
- Transit policies, territory-specific policies

## Visa Types
- Full table of all types
- Per-type sub-sections with details

## Fees (3 tables)
- Official fees (INR)
- Service charges
- Total estimated costs

## Documents Required
- Core documents checklist
- Per-visa-type documents

## Application Process
- 5 numbered steps (online form → pre-approval → center → track → collect)

## Centers / Offices in India
- Table with address, jurisdiction, contact

## Processing Times
- Table with service, timeline, fee

## Biometrics
- Requirements + exemptions with dates

## Success Tips
- Financial docs (MOST CRITICAL)
- Rejection reasons table
- Form tips, timing, document prep

## Why Trust This Guide?
- Trust signals table + testimonial

## FAQ (15-17 questions)
- Covering fees, processing, documents, rejection, transit, biometrics

## 2026 Updates — What's Changed
- Before/After comparison table

## Related Resources
- Only verified working links (official embassy/source sites)
- BTWVisas as plain text (phone, email)

## Conclusion + CTA
- Next steps (numbered)
- Phone/email as plain text (for non-working CTA pages); Visa Guide hub linked for next steps
```

### Quality Gates (Must Pass Before Output)
- [ ] All facts verified from official government sources
- [ ] EEAT score acceptable (expertise, experience, authority, trust)
- [ ] Keywords placed naturally (no stuffing)
- [ ] Readability score: Grade 8-10 (Flesch-Kincaid)
- [ ] Plagiarism score: <5%
- [ ] AI Overview optimized (definition, step, FAQ formats present)
- [ ] Mobile-friendly formatting (short paragraphs, bullet points)
- [ ] Indian CTA included and localized
- [ ] **ALL btwvisas.com URLs tested: 200/301→200 linked, 404 NOT linked**
- [ ] **.docx generated and formatting verified (headings, bold, links, tables)**
- [ ] **Broken (404) pages replaced with working alternatives or phone/email CTAs**
- [ ] **Anchor text is varied — no two links share the same text for the same target**
