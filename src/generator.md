# Generator Module

Takes segmentation plan from `segmenter.md` and user preferences.

For each segment, generates format-specific instruction blocks ready to copy-paste into BookLM.

---

## Generation Process

### Input Data Needed

From questionnaire:
- Selected format(s) (Podcast, Slides, Guide, Flashcards, Video)
- Target audience
- Conversational style
- Any special notes

From analyzer:
- Complete concept information with definitions and examples
- Difficult points noted
- Real-world applications

From segmenter:
- List of all segments with concepts per segment
- Segment duration/size estimates

---

## For Each Segment:

### Step 1: Gather Segment Information

**Collect:**
- Segment title
- Concepts covered (list with definitions)
- Examples from course
- Difficult points in this segment
- Target audience level
- Target duration/size
- Conversational style preference
- Any special notes

---

### Step 2: Select Appropriate Template

Based on format chosen:
- **Podcast** → Use `templates/instruction-podcast.md`
- **Slides** → Use `templates/instruction-slides.md`
- **Study Guide** → Use `templates/instruction-guides.md`
- **Flashcards** → Use `templates/instruction-flashcards.md`
- **Video** → Reference video template structure

---

### Step 3: Fill Instruction Block

For **Podcast** format:

1. **Title**: Descriptive, engaging (e.g., "Fundamentals of Decentralization")

2. **Duration**: State target duration clearly (e.g., "35 minutes")

3. **Chapters Covered**: List exact chapters/sections from source

4. **Audience**: State clearly (e.g., "Master's students", "Beginners", "Professionals")

5. **Key Concepts** (in order of importance):
   - List 3-7 key concepts for this segment
   - Each with brief description
   - Order them: most important first
   - Use definitions from course, not general knowledge

6. **Points to Explain Well**:
   - What needs special emphasis?
   - What might be confusing?
   - What should be clarified with examples?
   - Specific points from course analysis

7. **Common Misunderstandings to Address**:
   - What mistakes does analysis identify?
   - What confused students in the past?
   - What common confusions exist?

8. **Real-World Examples to Include**:
   - Which examples from course fit?
   - Any additional relevant applications?
   - Concrete, relatable examples

9. **Conversational Style**: State clearly (Academic/Natural/Debate/Socratic)

10. **Explanation Depth**: Concise/Medium/Detailed based on audience

11. **Tone & Emphasis**:
    - Key takeaways for this segment
    - What should listener remember?
    - What connections to emphasize?

12. **Copy-Paste Section for BookLM**:
    - Write concise instructions for BookLM
    - Reference the concepts and emphasis points above
    - Make it specific and actionable
    - Short enough to paste (but complete)
    - Format: Clear, numbered or bulleted

---

### For **Slides** Format:

1. **Title & Metadata**: Slides #, title, total slides, chapters, audience

2. **Slide Breakdown**:
   - Slide 1: Title slide (title, subtitle, visual)
   - Slide 2: Roadmap/overview
   - Slides 3-N: Concept content (1-2 concepts per slide)
   - Final slide: Summary

3. **Speaker Notes**: Detailed explanation for each slide

4. **Visual Elements**: Placeholder descriptions for diagrams, charts, images

---

### For **Study Guide** Format:

1. **Title & Metadata**: Guide #, chapters, audience

2. **Learning Objectives**: What should reader understand?

3. **Key Definitions**: All important terms defined

4. **Core Concepts**: Q&A format with full explanations

5. **Common Questions & Answers**

6. **Practice Questions**: For self-assessment

---

### For **Flashcards** Format:

1. **Card Set**: Difficulty levels (Beginner/Intermediate/Advanced)

2. **Cards**: 
   - Front: Question or prompt
   - Back: Answer with memory cue
   - Organized by difficulty

---

### For **Video** Format:

1. **Script**: Voiceover script (conversational, timed)

2. **Scene Descriptions**: What's happening visually

3. **B-Roll Suggestions**: What should be shown

4. **Visual Transitions**: How scenes change

---

## Step 4: Optimize for Format & Audience

**For each block:**

- **Audio optimization** (if podcast/video):
  - Break long sentences
  - Replace symbols with words (e.g., "$50K" → "fifty thousand dollars")
  - Add natural transitions
  - Ensure TTS-friendly

- **Audience appropriateness**:
  - Beginner: Explain basics, define terms, simple examples
  - Advanced: Assume background, use technical terms, complex examples
  - Professional: Focus on application, practical relevance

- **Style application**:
  - Academic: Formal, precise, structured
  - Natural: Conversational, accessible, friendly
  - Debate: Multiple perspectives, balanced
  - Socratic: Question-led, discovery-based

---

## Step 5: Quality Check Each Block

**Before finalizing:**

- ✅ All concepts from segment are covered
- ✅ Concepts are in logical order (prerequisites first)
- ✅ Key difficult points are addressed
- ✅ Examples are concrete and relevant
- ✅ Duration estimate is realistic
- ✅ Audience level is appropriate
- ✅ Style is consistent
- ✅ Instructions are clear and actionable
- ✅ Copy-paste section is complete and ready

**If issues:**
- Revise block
- Recheck against segment requirements
- Retest appropriateness

---

## Repeat for All Segments

Generate instruction block for each segment using same process above.

---

## Output Format

For each segment, create complete block containing:

```
## [FORMAT] #{segment_number}: [Segment Title]

[Format-specific metadata: duration, chapters, audience, etc.]

**Key Concepts:**
1. [concept] - [brief description]
2. [concept] - [brief description]
[...]

**Points to Explain Well:**
- [point 1]
- [point 2]
[...]

**Real-World Examples:**
- [example 1]
- [example 2]
[...]

**Style**: [conversational style]

---

## COPY-PASTE FOR BOOKLM

[Instruction text ready for BookLM Custom Instructions field]

---
```

All blocks flow together for final output stage.

---

## Important Notes for Claude

### Instruction Quality

**Good instructions:**
- Specific (exact concepts to cover)
- Complete (don't require guessing)
- Audience-appropriate (right depth)
- Style-consistent (matches tone)
- Example-rich (concrete illustrations)
- Actionable (BookLM can follow)

**Bad instructions:**
- Vague ("explain this well")
- Incomplete (missing key points)
- Wrong audience level (too simple or complex)
- Inconsistent style
- Missing examples
- Unclear what to do

### BookLM Prompt Best Practices

**DO:**
- Be specific about what to cover
- List concepts in priority order
- Include tone/style guidance
- Mention target audience
- Note emphasis areas
- Include examples

**DON'T:**
- Use vague language ("cover the main topics")
- Assume BookLM knows course context
- Give contradictory instructions
- Overload with too many details
- Use jargon BookLM might misunderstand

---

## Output to Next Phase

All instruction blocks (one per segment) flow into `output.md`

Output module needs:
- All instruction blocks (for all segments)
- Segmentation summary
- Any analysis notes
- User preferences (for usage guide)

---

**Status**: Ready for Claude execution (Phase 1)
**Next Step**: Pass all blocks to `output.md` for DOCX/TXT generation
