# Segmenter Module

Takes analysis from `analyzer.md` and user preferences from `questionnaire.md`.

Calculates optimal segmentation based on:
- Target format (podcast, slides, guide, flashcards, video)
- Target duration/size
- Target audience
- Pedagogical dependencies
- Concept completeness

---

## Segmentation Process

### Input Data Needed

From questionnaire:
- Format choice(s)
- Duration/size preference
- Target audience
- Content priority (all, specific chapters, key themes)
- Style preference

From analyzer:
- Complete concept list
- Concept dependencies
- Learning progression order
- Pedagogical density per section
- Chapter/section boundaries
- Difficult points

---

### Step 1: Determine Number of Segments

**Do this:**
- Based on format, estimate required number of segments
- Factor in target duration/size

**Calculation:**

**For Podcast:**
- User selected: Short/Medium/Long/Very Long
- Convert to minutes: 10-15 / 25-35 / 40-60 / 60+
- Estimate words per minute for podcast: ~150 wpm (conversational speed)
- Count total words in course
- Calculate: Total words ÷ (target minutes × 150) = number of episodes

Example: 80-page course ≈ 40,000 words
- Target: 25-35 min episodes
- Assume 30 min target
- 40,000 ÷ (30 × 150) = 40,000 ÷ 4,500 ≈ 9 segments needed
- Consolidate: Maybe 4 episodes if denser, 5-6 if sparse

**For Slides:**
- User selected: Concise/Moderate/Detailed/Very Detailed
- Convert to target slides: 15 / 30 / 50 / 75
- Concepts per slide: 1-2 concepts/slide
- Calculate: Total concepts ÷ 1.5 = slides needed
- Compare to target, adjust

**For Study Guide:**
- User selected: Concise/Moderate/Detailed/Very Detailed
- Convert to target pages: 7 / 15 / 30 / 60
- Concepts per page: 2-4 concepts/page
- Calculate: Total concepts ÷ 3 = pages needed
- Compare to target, adjust

**For Flashcards:**
- User selected: Concise/Moderate/Comprehensive/Exhaustive
- Convert to target cards: 30 / 60 / 100 / 150
- Cards should be: 1 per concept (beginner) + 2-3 per concept (variations)
- Calculate: Total concepts × 2 = cards needed
- Compare to target, adjust

**For Video:**
- User selected: Short/Moderate/Detailed
- Convert to minutes: 15 / 60 / 120
- Same calculation as podcast but adjust for script format

**Output:** Target number of segments

---

### Step 2: Determine Segment Boundaries

**Option A: Chapter-Level Segmentation** (simpler)
- Each segment = 1 chapter or parts of chapter
- Respects natural document boundaries
- Usually cleaner, easier to follow

**Option B: Concept-Level Segmentation** (more precise)
- Group concepts into coherent segments
- Respect dependency order
- Each segment covers complete concepts

**Decision Rule:**
- If course has clear chapters with 3-5 concepts each → use chapters
- If chapters are too long (10+ concepts) → split by concepts
- If chapters are too short (1-2 concepts) → combine chapters

**Do this:**
- Identify chapter/concept groupings
- Ensure each segment:
  - Has complete, standalone concepts (no split concepts)
  - Has prerequisites before dependents (dependency order)
  - Is pedagogically coherent (related concepts together)
  - Fits target size/duration
  - Is roughly balanced with other segments

**Output:**
```
Segment 1: [Title]
  - Chapters: [X-Y]
  - Concepts: [concept A, B, C]
  - Duration estimate: [X minutes for podcast, or Y slides, etc.]
  - Dependencies: [prerequisites needed before this segment]

Segment 2: [Title]
  ...
```

---

### Step 3: Validate Segmentation

**Check:**
1. No concepts are split across segments
2. All prerequisites come before dependents
3. Each segment is roughly balanced in size
4. Total adds up to target (±20%)
5. Logical progression (learning order makes sense)
6. No orphaned content (everything is assigned)

**If issues found:**
- Adjust boundaries
- Re-group concepts
- Consolidate or split segments
- Recheck balance

---

### Step 4: Adjust for Audience & Style

**Consider:**
- Beginner audience: May need MORE segments (shorter, easier chunks)
- Advanced audience: Can handle longer, denser segments
- Academic style: Formal boundaries (chapters), longer segments
- Conversational style: Natural breakpoints, medium segments
- Special notes: Any user preferences affect grouping

**Adjust if needed:**
- Add intermediate summary segments
- Break dense sections into more segments
- Combine lightweight sections

---

### Step 5: Create Final Segmentation Plan

**Output:**
```
SEGMENTATION PLAN
=================

Total Segments: [N]
Average Size: [X minutes / Y slides / Z pages]
Format: [Podcast / Slides / Guide / Flashcards / Video / Mix]

Segment 1: [Title]
  Location: Chapters [X-Y] (pages [X-Y])
  Concepts: [1. Name, 2. Name, 3. Name]
  Estimated Duration: [X minutes for podcast / Y slides / Z pages]
  Prerequisites: None (this is first segment)
  Summary: [1-2 sentence summary of what segment covers]

Segment 2: [Title]
  Location: Chapter [Z] (pages X-Y)
  Concepts: [1. Name, 2. Name]
  Estimated Duration: [X minutes / Y slides / Z pages]
  Prerequisites: Segment 1 (introduces foundational concepts)
  Summary: [1-2 sentence summary]

[... continue for all segments ...]

Pedagogical Notes:
- [Dependency note 1]
- [Balance note 1]
- [Potential issue and resolution]

Total Estimated Duration: [Total minutes / slides / pages]
Variance from Target: [±X%]
```

---

## Important Notes for Claude

### Segment Quality Rules

**Each segment should:**
- Cover complete concepts (not split concepts across segments)
- Stand alone pedagogically (could be understood independently)
- Respect learning order (prerequisites before applications)
- Be roughly balanced (no mega-segments next to tiny ones)
- Have clear title (describes what user will learn)
- Fit target format (right duration/slides/pages/etc.)

### Common Pitfalls to Avoid

- Splitting a concept across 2 segments (confusing)
- Putting advanced concept before its prerequisite (wrong order)
- Making one segment twice as long as others (imbalanced)
- Ignoring natural chapter/topic boundaries unnecessarily
- Creating segments too short (less than 5 min podcast, <3 slides, <1 page)
- Creating segments too long (more than 60 min podcast, >15 slides, >10 pages)

### Duration Estimation Rules

**Podcast estimate:**
- Conversational speech: ~150 words per minute
- Count segment concepts + explanations + examples
- Rough estimate: 1 concept ≈ 3-5 min of podcast

**Slides estimate:**
- 1-2 concepts per slide
- Count total concepts
- Examples: 10 concepts ≈ 8-10 slides

**Study Guide estimate:**
- 2-4 concepts per page
- Count total concepts
- Examples: 15 concepts ≈ 5-8 pages

**Flashcards estimate:**
- 2-3 cards per concept (beginner + variations)
- Count total concepts
- Examples: 20 concepts ≈ 50-60 cards

**Video estimate:**
- Same calculation as podcast (script + narration)

---

## Output to Next Phase

This segmentation becomes input to `generator.md`

The generator needs:
- List of all segments with titles
- Concepts covered in each segment
- Duration/size estimates
- Target audience and style
- Any special notes

---

**Status**: Ready for Claude execution (Phase 1)
**Next Step**: Pass segmentation plan to `generator.md`
