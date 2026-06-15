---
title: "FAQ Schema & Structured Data — Visa Content"
description: "Implement FAQ, HowTo, and Article structured data for AI Overview visibility and rich snippets"
---

# FAQ Schema & Structured Data — Visa Content

## Objective
Implement proper structured data (schema markup) on all visa guides. Schema markup is the #1 technical factor for appearing in AI Overviews, featured snippets, and rich results.

## Schema Types for Visa Content

| Schema Type | When to Use | Benefit |
|-------------|------------|---------|
| **FAQPage** | ALL visa guides (10+ questions) | AI Overview, rich snippet, voice search |
| **HowTo** | Step-by-step application guides | Step-rich snippet, AI Overview |
| **Article** | ALL visa guides | Standard rich snippet, authorship |
| **BreadcrumbList** | ALL pages | Breadcrumb in SERP |
| **Product** | Service/consultation pages | Price, review stars |
| **Organization** | Site-wide | Knowledge Panel, brand info |
| **Review** | Client testimonials | Star ratings in SERP |
| **WebPage** | ALL pages | Core metadata |

## FAQ Schema Implementation

### Structure
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is Canada PR for Indians?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Canada PR (Permanent Residence) is a status that allows Indian citizens to live, work, and study anywhere in Canada. It's the first step toward Canadian citizenship and is primarily achieved through the Express Entry system."
      }
    },
    {
      "@type": "Question",
      "name": "What is the minimum CRS score for Canada PR in 2026?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "The minimum CRS score varies by draw. In 2026, general draws have ranged from 470-530 points. Category-based draws (French language, healthcare, STEM) may have lower thresholds."
      }
    }
    // ... 8-13 more questions
  ]
}
```

### Rules for FAQ Schema
```markdown
✓ Each question must be unique (no duplicates across pages)
✓ Answer must be 40+ characters (meaningful content)
✓ Question must match actual user queries (from PAA, keyword research)
✓ Plain text answers preferred (minimal HTML)
✓ Minimum 10 questions per FAQ schema
✓ Maximum 15 questions recommended (too many = link bloat)
✓ Questions must actually appear in the visible page content
✗ Don't hide schema content that isn't visible on page
✗ Don't use FAQ schema for promotional content
```

## HowTo Schema Implementation

### Structure
```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "How to Apply for Canada PR from India",
  "description": "Step-by-step guide for Indian citizens applying for Canada Permanent Residence",
  "totalTime": "P6M",
  "estimatedCost": {
    "@type": "MonetaryAmount",
    "currency": "INR",
    "value": "85000"
  },
  "image": "https://btwvisas.com/images/canada-pr-process.jpg",
  "step": [
    {
      "@type": "HowToStep",
      "position": 1,
      "name": "Check Your CRS Score",
      "text": "Use the Comprehensive Ranking System (CRS) calculator to determine your eligibility score. A score of 470+ is typically competitive in 2026.",
      "url": "https://btwvisas.com/crs-calculator"
    },
    {
      "@type": "HowToStep",
      "position": 2,
      "name": "Take Language Tests",
      "text": "Take approved language tests (IELTS for English or TEF for French). Indian applicants need a minimum CLB 7 in all abilities.",
      "image": "https://btwvisas.com/images/ielts-test.jpg"
    }
    // ... remaining steps
  ]
}
```

### Rules for HowTo Schema
```markdown
✓ Minimum 5 steps per HowTo
✓ Each step has actionable text (not just heading)
✓ Optional: add images to key steps
✓ Optional: add URLs to relevant steps (tool pages, etc.)
✓ Estimated total time and cost included
✓ Description summarizes the process
✗ Don't add steps that don't appear in visible content
✗ Don't use HowTo for non-process content
```

## Article Schema Implementation

### Structure
```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Canada PR Visa for Indians 2026: Complete Guide",
  "description": "Complete guide to Canada PR for Indian applicants. Covers eligibility, CRS score, fees in INR, documents, and step-by-step application process.",
  "author": {
    "@type": "Person",
    "name": "Author Name",
    "url": "https://btwvisas.com/author/author-name",
    "knowsAbout": ["Canadian Immigration", "Express Entry", "Visa Applications"]
  },
  "datePublished": "2026-01-15",
  "dateModified": "2026-05-29",
  "image": "https://btwvisas.com/images/canada-pr-guide-2026.jpg",
  "publisher": {
    "@type": "Organization",
    "name": "BTWVisas",
    "logo": {
      "@type": "ImageObject",
      "url": "https://btwvisas.com/logo.png"
    }
  }
}
```

## Implementation Methods

### Method 1: JSON-LD (Recommended)
Add to `<head>` or before `</body>`:
```html
<script type="application/ld+json">
[FAQ JSON, HowTo JSON, Article JSON — all valid JSON]
</script>
```

### Method 2: Manual Schema Testing
Use Google's Rich Results Test to validate:
```
https://search.google.com/test/rich-results
```

## Schema Validation Checklist

- [ ] All JSON-LD is valid JSON (no trailing commas, proper quoting)
- [ ] All URLs are absolute (https://btwvisas.com/... not relative /page)
- [ ] FAQ questions match visible page content
- [ ] HowTo steps match visible numbered steps
- [ ] Article dates are accurate (datePublished <= dateModified)
- [ ] Author URL points to real author page
- [ ] Logo URL points to real logo image
- [ ] No duplicate question IDs across FAQ schema
- [ ] All schema validated with Google Rich Results Test
- [ ] Schema for every guide (FAQ + HowTo if applicable + Article)

## Output
For each visa guide:
- Complete FAQ JSON-LD (10-15 Q&A pairs)
- Complete HowTo JSON-LD (if applicable)
- Complete Article JSON-LD
- Google Rich Results Test validation screenshot/pass
- Schema implementation instructions (where to place in HTML)

## Quality Check
- [ ] Valid JSON (no syntax errors)
- [ ] Google Rich Results Test: PASS (no errors, no warnings)
- [ ] 10+ FAQ questions that users actually search for
- [ ] 5+ HowTo steps (if applicable)
- [ ] Article schema with author and organization
- [ ] Questions and answers match visible content
- [ ] All dates current and accurate
- [ ] Images referenced exist and are optimized
