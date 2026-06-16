# Analyzer Module

Claude reads the course completely and extracts:
1. Document structure (chapters, sections, subsections)
2. Key concepts with definitions
3. Concept dependencies (prerequisites, relationships)
4. Pedagogical density (concepts per page)
5. Difficult points (complex concepts needing extra explanation)
6. Examples and real-world applications
7. Overall course metadata

---

## CRITICAL: Language Requirement

**Analysis must be conducted in user's language IF possible.**

- If course is French & user is French → Analyze in French
- If course is English & user is English → Analyze in English
- **Course language ≠ user language?** → Translate during analysis, keep original terms

**All analysis output (structure, concepts, dependencies) should reference user's language for clarity.**

---

## Analysis Process

### Phase 1: Document Structure Extraction

**Do this:**
- Read course from beginning to end
- Identify all chapter/section titles and hierarchy
- Note page numbers or section markers
- Create mental map of document structure

**Output:**
```
Course: [Title]
Total length: [pages/words]
Chapters:
  Chapter 1: [Title] (pages X-Y) - [brief description]
    1.1: [Section] (pages X-Y)
    1.2: [Section] (pages X-Y)
  Chapter 2: [Title] (pages X-Y)
  ...
```

### Phase 2: Concept Extraction

**Do this:**
- Go through each section systematically
- Extract key concepts (new terms, ideas, principles)
- For each concept, note:
  - Definition or explanation (as stated in course)
  - First mention location (chapter/section/page)
  - How often mentioned (frequency)
  - Examples provided
  - Real-world applications
  - Difficulty level (beginner/intermediate/advanced)

**Output:**
```
Concept 1: [Name]
  - Definition: [as stated in course]
  - First seen: Chapter X, Section Y
  - Frequency: [mentioned N times]
  - Example: [example from course]
  - Application: [real-world use]
  - Difficulty: [level]
  - Related terms: [other concepts it mentions]

Concept 2: [Name]
  ...
```

### Phase 3: Dependency Mapping

**Do this:**
- For each concept, check what other concepts it references or assumes
- Build relationships:
  - "Requires understanding X" → X is prerequisite
  - "Related to Y" → Y is sibling concept
  - "Application of principle Z" → Z is foundational
- Create concept order (what should be taught first)

**Output:**
```
Concept Dependencies:
  [Concept A] requires [Concept B] (B is prerequisite)
  [Concept A] relates to [Concept C]
  [Concept D] applies [Concept B]
  
Learning Order:
  1. [Foundational Concept 1]
  2. [Foundational Concept 2]
  3. [Intermediate Concept A] (depends on 1, 2)
  4. [Advanced Concept X] (depends on 1, 2, A)
  ...
```

### Phase 4: Pedagogical Density Evaluation

**Do this:**
- For each chapter/section, estimate "concept density"
- Calculate: How many new concepts per page?
- Score as:
  - Low: <1 concept per page (reviews, examples)
  - Medium: 1-3 concepts per page (standard teaching)
  - High: 3+ concepts per page (dense material)

**Output:**
```
Pedagogical Density:
  Chapter 1: Medium (2.5 concepts/page, easy intro)
  Chapter 2: High (4 concepts/page, dense material)
  Chapter 3: Low (0.5 concepts/page, application-focused)
  
Overall: Medium-High (course is fairly dense)
```

### Phase 5: Difficult Points & Examples

**Do this:**
- Identify concepts that seem hard to explain
- Note:
  - What makes them difficult (abstract, counterintuitive, etc.)
  - What examples course provides
  - What might need extra explanation
- Find all examples, case studies, real-world applications

**Output:**
```
Difficult Points:
  - [Concept X]: Why? [explanation]. Example in course: [reference]
  - [Concept Y]: Why? [explanation]. Suggestion: [add more examples]
  
Examples & Applications:
  - Chapter X discusses [application] in [context]
  - Chapter Y provides case study: [brief description]
  - Real-world use: [mentioned where?]
```

### Phase 6: Overall Summary

**Do this:**
- Synthesize all analysis
- Create summary of what you learned about the course

**Output:**
```
COURSE ANALYSIS SUMMARY
=======================

Title: [Course Title]
Source: [file/URL/text provided]
Total pages: [N]
Total concepts: [N]

Structure:
- [N] chapters covering [main topics]
- Organized as: [progression description]
- Recommended reading order: [same as presented? or modified?]

Pedagogical Assessment:
- Density: [Low/Medium/High]
- Complexity: [Beginner/Intermediate/Advanced]
- Key challenge: [what's hardest to understand?]

Strengths:
- [Strong area 1]
- [Strong area 2]

Could improve:
- [Area that could use more examples]
- [Area that's dense]

Recommended Segmentation:
- For podcast: [suggest N episodes with rough chapter alignment]
- For slides: [suggest N slides based on concepts]
- For study guide: [suggest structure]
- For flashcards: [suggest card count by difficulty]

Dependencies:
- [Concept A] must come before [Concept B]
- [Concept C] is foundational for [Concept D, E, F]
```

---

## Important Notes for Claude

### Be Thorough
- Read the ENTIRE course, not just skimming
- Extract ALL concepts, not just major ones
- Understand relationships between concepts
- Note exact locations (chapter, section, page if available)

### Be Accurate
- Use course's own definitions, not your general knowledge
- Quote examples as stated in course
- Don't add concepts not in the course
- Preserve course's ordering and emphasis

### Be Pedagogically Sound
- Think like an educator
- What's the learning progression?
- What requires prerequisites?
- What's genuinely difficult?
- Are examples appropriate and clear?

### Be Practical
- Keep eye on segmentation (will need this for segmenter)
- Note where chapter boundaries are
- Identify natural "breaks" between topics
- Think about how to make segments complete

---

## Output to Next Phase

This analysis becomes input to `segmenter.md`

The segmenter needs:
- Complete concept list with definitions
- Dependency relationships
- Density evaluation per chapter/section
- Learning progression order
- Difficult points to address

---

**Status**: Ready for Claude execution (Phase 1)  
**Next Step**: Pass complete analysis to `segmenter.md`
