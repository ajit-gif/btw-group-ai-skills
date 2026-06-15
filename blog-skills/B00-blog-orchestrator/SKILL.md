---
title: "B00: Blog Orchestrator — Create Blog Post Workflow"
description: "Orchestrates the complete travel blog content pipeline from topic ideation to social distribution using all B01-B10 skills"
trigger: "create blog"
mode: "primary"
temperature: 0.4
---

# B00: Blog Orchestrator — Create Blog Post Workflow

## Trigger
When the user says **"create blog"**, **"create blog post"**, **"write a blog"**, or mentions creating a travel blog content piece, invoke this orchestrator.

## Objective
Produce a complete, publication-ready travel blog post (in `.md` format) that:
- Engages Indian travelers (aspirational + practical)
- Uses narrative/storytelling style (not visa-guide procedural)
- Is optimized for search and social distribution
- Crosslinks to relevant visa guides where natural
- Has visuals, social snippets, and a calendar slot

## Workflow Pipeline (Execute in Order)

### Phase 1: Plan the Blog
1. **Topic Ideation** → `.opencode/blog-skills/B01-blog-topic-ideation-trends/SKILL.md`
   - If user gave a topic → validate it (has demand? right timing?)
   - If no topic → run ideation process, present 3-5 options, let user pick
2. **Persona Assignment** → `.opencode/blog-skills/B02-travel-persona-segmentation/SKILL.md`
   - Assign primary persona (First-time, Budget, Family, Solo Female, Luxury, Student)
   - Document tone, format, and CTA style for this persona

### Phase 2: Write the Content
3. **Pick Blog Format** — Choose one based on topic + persona:

   | If topic is... | Use Format |
   |---|---|
   | Personal experience, journey, lesson learned | **B03** — Narrative Storytelling |
   | A specific city/country/region | **B04** — Destination & Experience Guide |
   | A multi-day trip plan | **B05** — Travel Itinerary Builder |
   | How much things cost | **B06** — Budget & Cost Analysis |
   | Top X list, X vs Y comparison | **B08** — Listicle & Comparison Builder |

4. **Write the draft** using the chosen format skill
   - Follow all structure templates from that skill
   - Weave in persona-appropriate tone from B02
   - Keep Indian traveler context throughout

### Phase 3: Enrich with Visuals
5. **Visual & Media Brief** → `.opencode/blog-skills/B07-visual-media-brief/SKILL.md`
   - Create briefs for hero image, 3-5 in-content images, infographics, social cards
   - Include AI generation prompts and alt text for each
   - Note: this produces briefs, not actual images (designer/AI tool executes)

### Phase 4: Distribute
6. **Social Media Snippets** → `.opencode/blog-skills/B09-social-media-cross-post/SKILL.md`
   - Extract 5 platform packs (Instagram, Pinterest, Twitter/X, LinkedIn, Facebook)
   - Platform-appropriate hooks, hashtags, and posting times

### Phase 5: Schedule
7. **Content Calendar** → `.opencode/blog-skills/B10-blog-content-calendar/SKILL.md`
   - Add blog to the monthly/weekly calendar
   - Note seasonal tie-ins and crosslink opportunities
   - Include in batch production tracking

### Phase 6: Crosslink to Visa Guides
8. **Identify crosslink opportunities** — Scan the written blog for natural places to link to:
   - Related visa guides (from `.opencode/skills/`)
   - Related news articles (from `.opencode/news-skills/`)
   - Add 1-3 contextual internal links (not forced)

## Execution Flow Diagram

```
USER: "create blog about [topic]"
         │
         ▼
┌───────────────────────────────────────────┐
│  PHASE 1: PLAN                            │
│  B01 → Topic validation/ideation          │
│  B02 → Persona assignment                 │
├───────────────────────────────────────────┤
│  PHASE 2: WRITE                           │
│  Pick format: B03 / B04 / B05 / B06 / B08 │
│  → Write full draft                       │
├───────────────────────────────────────────┤
│  PHASE 3: ENRICH                          │
│  B07 → Visual briefs (hero, in-content,   │
│        infographics, social cards)        │
├───────────────────────────────────────────┤
│  PHASE 4: DISTRIBUTE                      │
│  B09 → 5 social platform packs            │
├───────────────────────────────────────────┤
│  PHASE 5: SCHEDULE                        │
│  B10 → Calendar entry + batch tracking    │
├───────────────────────────────────────────┤
│  PHASE 6: CROSSLINK                       │
│  Link to visa guides + news articles      │
├───────────────────────────────────────────┤
│  OUTPUT: Complete blog package            │
└───────────────────────────────────────────┘
```

## Output Requirements

### File Formats
| Format | Location | Description |
|--------|----------|-------------|
| `.md` | `blogs/published/{slug}/index.md` | Master blog markdown |
| Visual Brief | `blogs/published/{slug}/visual-brief.md` | Image specs and prompts |
| Social Pack | `blogs/published/{slug}/social-pack.md` | Platform-wise snippets |

### Blog Content Structure (Must Include)
```
# {Title} — BTWVisas

## TL;DR / Quick Summary (for featured snippets)
- 2-3 line summary of what this blog covers

## Hook (First 50 words)
- Grab attention immediately

## Body
- Narrative or structured content per chosen format
- Indian traveler perspective throughout
- Costs in INR where applicable
- Short paragraphs (2-4 sentences for mobile)
- Subheadings every 200-300 words

## FAQ (if applicable — 5-8 questions)

## Conclusion + CTA
- Aligned with persona from B02
- Gentle, not salesy

## Related Blogs / Guides
- 1-3 internal links
```

### Quality Gates (Must Pass Before Output)
- [ ] Topic validated (has demand or seasonal relevance)
- [ ] Persona assigned and tone consistent throughout
- [ ] Hook grabs attention in first 50 words
- [ ] Indian traveler perspective present (not generic)
- [ ] Costs in INR where relevant
- [ ] Mobile-friendly formatting (short paragraphs, clear headers)
- [ ] Crosslinks to 1-3 visa guides or news articles
- [ ] Visual brief created (hero + 3 in-content images)
- [ ] Social snippets created (min 3 platforms)
- [ ] Calendar slot assigned
- [ ] No salesy/aggressive CTAs — gentle and helpful

## Report Back
After completing the pipeline, provide a clean summary:

```
📝 BLOG CREATED — [Title]
━━━━━━━━━━━━━━━━━━━━━━━━━━

📄 FORMAT: [B03/B04/B05/B06/B08] — [Format Name]
👤 PERSONA: [Persona Name]
📏 LENGTH: ~[X] words

📸 VISUALS BRIEFED:
  - Hero image: [Description]
  - In-content: [X] images
  - Infographic: [Yes/No]
  - Social cards: [X] platforms

📤 SOCIAL PACKS GENERATED:
  - Instagram carousel: [X] slides
  - Pinterest: [X] pins
  - Twitter/X thread: [X] tweets
  - LinkedIn: [X] post
  - Facebook: [X] post

🔗 CROSSLINKS:
  - [Visa guide 1]
  - [Visa guide 2]

📅 SCHEDULED: [Date]

━━━━━━━━━━━━━━━━━━━━━━━━━━
```
