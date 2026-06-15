---
title: "Mobile-First Readability Check — Visa Content"
description: "Optimize visa guide content for mobile users — 80%+ of Indian audience reads on mobile"
---

# Mobile-First Readability Check — Visa Content

## Objective
Ensure every visa guide is optimized for mobile viewing. With 80%+ of Indian users accessing content on smartphones, mobile readability is not optional — it's a ranking factor (Core Web Vitals) and a user experience necessity.

## Mobile Reading Behaviors of Indian Users

| Behavior | Implication for Content |
|----------|------------------------|
| Skim, don't read | Short paragraphs, clear headings |
| Impatient (< 3 seconds to decide) | Value proposition in first 2 lines |
| Data-conscious | No auto-play videos, optimize images |
| Thumb-scrolling | Touch-friendly buttons, spaced content |
| Distracted (commuting, waiting) | Scannable content, key takeaways first |
| Low patience for popups | Non-intrusive CTAs, delayed modals |
| Prefer visual over text | Tables, icons, infographics |

## Mobile Formatting Rules

### Paragraph Length
```markdown
✓ Max 3-4 sentences per paragraph
✓ Max 50 words per paragraph
✓ Target: 2-3 sentences, 30-40 words

✗ Long paragraphs → Users leave
✗ Run-on sentences → Hard to follow on small screens
```

### Line Length & Spacing
```markdown
✓ Max 65-75 characters per line (on mobile)
✓ Line height: 1.5-1.8 (for readability)
✓ Section spacing: 2em between sections
✓ Bullet spacing: 0.5em between items
✓ No walls of text — break with subheadings
```

### Heading Structure
```markdown
H2: Every 200-300 words
H3: Every 100-150 words within H2 sections
H4: Rarely use — too deep for mobile

✓ Headings should be scannable questions or statements
✓ Users should understand the page just by reading headings
```

### Lists & Bullets
```markdown
✓ Bullet points for requirements, benefits, tips
✓ Numbered lists for step-by-step processes
✓ Max 7 items per list (cognitive load)
✓ Each item: 1-2 lines max
✓ Keep parallel structure (all verbs, all nouns, etc.)
```

### Tables on Mobile
```markdown
✓ Tables with max 3-4 columns
✓ Left-align text in first column
✓ Horizontal scroll hint for wider tables
✓ Consider card layout instead of tables on mobile

Best practice for mobile fees table:
| Fee Type | Amount (INR) |
|----------|-------------|
| Application | ₹12,500 |
| Service Fee | ₹3,200 |
| Biometrics | ₹1,800 |

(2-column tables work best on mobile)
```

### CTAs on Mobile
```markdown
✓ Minimum touch target: 48x48px (Google recommendation)
✓ Minimum 12px padding around button text
✓ CTAs placed at natural scroll breakpoints
✓ No CTAs that require horizontal scrolling to see
✓ Sticky CTA only for conclusion (not intrusive)
✓ "Tap to Call" for phone numbers (tel: links)
```

## Readability Scores

### Target Scores for Visa Content
| Metric | Target | Tool |
|--------|--------|------|
| Flesch Reading Ease | 60-70 (Plain English) | Hemingway / Readable |
| Flesch-Kincaid Grade | Grade 8-10 | Hemingway / Readable |
| Passive voice | < 10% of sentences | Hemingway |
| Sentence length avg | 15-20 words | Hemingway |
| Subheading frequency | Every 200-250 words | Manual check |
| Paragraph breaks | Every 3-4 sentences | Manual check |

### Indian English Readability Notes
```markdown
✓ Use Indian English spellings: "centre" not "center", "programme" not "program"
✓ Explain foreign concepts (e.g., "Social Insurance Number (SIN) — similar to Aadhaar")
✓ Avoid idioms that don't translate
✓ Use familiar comparisons: "size of Rajasthan", "similar to Indian PAN card"
✓ Explain acronyms on first use
```

## Mobile Page Speed Considerations

### Core Web Vitals Targets
| Metric | Target | Impact |
|--------|--------|--------|
| LCP (Largest Contentful Paint) | < 2.5 seconds | Google ranking factor |
| FID (First Input Delay) | < 100ms | Google ranking factor |
| CLS (Cumulative Layout Shift) | < 0.1 | Google ranking factor |
| TTFB (Time to First Byte) | < 800ms | User patience |
| First Contentful Paint | < 1.8 seconds | First impression |

### Content-Specific Optimizations
```markdown
- Lazy load images below the fold
- Compress all images (WebP format preferred)
- Minify CSS and JavaScript
- Reduce third-party scripts
- Use system fonts (no custom font loading delay)
- Preload key above-fold content
- Defer non-critical CSS
- Enable text compression (Gzip/Brotli)
```

## Mobile Testing Checklist

### Visual Test (On Actual Mobile or Emulator)
```markdown
- [ ] Content fits without horizontal scroll
- [ ] Font size is readable (min 16px for body text)
- [ ] Buttons are thumb-friendly (48x48px min)
- [ ] No overlapping elements
- [ ] Tables scroll horizontally (or are card-format)
- [ ] Images are responsive (don't overflow containers)
- [ ] Forms are tap-friendly (large input fields)
- [ ] CTAs are visible without excessive scrolling
- [ ] No intrusive popups covering content
```

### Content Test
```markdown
- [ ] First paragraph < 50 words (hooks immediately)
- [ ] Subheadings every 200 words (scannable)
- [ ] Bullet points used for lists (not comma-separated text)
- [ ] Max 4 sentences per paragraph
- [ ] Key info in bold (scannable highlights)
- [ ] No jargon without explanation
- [ ] FAQ is expandable/collapsible (accordion)
- [ ] Internal links have enough spacing between them
```

## Output
A mobile readiness report with:
- Flesch-Kincaid readability score (target: Grade 8-10)
- Mobile formatting audit (paragraphs, headings, lists, tables)
- Core Web Vitals check (LCP, FID, CLS)
- Mobile usability issues identified
- Readability improvements applied
- Screenshots from mobile emulator (before/after)

## Quality Check
- [ ] Flesch Reading Ease: 60-70
- [ ] Flesch-Kincaid Grade: 8-10
- [ ] No paragraphs longer than 4 sentences
- [ ] Headings every 200-250 words
- [ ] Bullet points for all lists
- [ ] Tables max 3-4 columns
- [ ] All CTAs min 48x48px touch target
- [ ] No horizontal scroll on 375px width device
- [ ] Font size 16px minimum for body text
- [ ] Content scannable by headings alone
