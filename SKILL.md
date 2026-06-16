# BookLM-Orchestrator Skill Declaration

## Metadata

```yaml
name: booklm-orchestrator
title: BookLM-Orchestrator
version: 0.1.0
description: Claude Code skill that analyzes complete courses, intelligently segments them, and generates optimized instructions for BookLM (podcasts, slides, study guides, flashcards, videos). Full interactive workflow.
author: Yoann CRAMATTE
organization: Grand Belfort DEE-GDU
license: MIT
repository: https://github.com/ycramatte/booklm-orchestrator
homepage: https://github.com/ycramatte/booklm-orchestrator
keywords:
  - booklm
  - education
  - course-segmentation
  - podcast-generation
  - learning-paths
  - artificial-intelligence
languages:
  - fr
  - en
status: alpha
```

## Overview

BookLM-Orchestrator analyzes complete courses and intelligently prepares them for BookLM. Interactive questionnaire gathers user requirements. Claude reads the complete course, analyzes structure and concepts, calculates optimal segmentation, and generates format-specific instructions ready to copy-paste into BookLM.

**Tagline**: "Transform your course into structured educational content — all ready for BookLM."

## Primary Command

```
/booklm-orchestrator
```

Launches complete interactive workflow:
1. Questionnaire (course + preferences)
2. Course analysis
3. Intelligent segmentation
4. Instruction generation
5. Output delivery (DOCX/TXT)

## Interactive Workflow

### Step 1: Launch & Questionnaire

User types: `/booklm-orchestrator`

Claude asks:
```
1. Provide your course:
   [ ] Upload PDF / DOCX / TXT / MD file
   [ ] Provide URL link
   [ ] Paste course text directly

2. What is your target output format?
   [ ] Podcast (conversational, timed)
   [ ] Slides (visual, concise)
   [ ] Study Guide (Q&A, detailed)
   [ ] Flashcards (memory-focused)
   [ ] Video (script + descriptions)
   [ ] Mix (multiple formats)

3. If podcast: target duration per episode?
   [ ] Short (10-15 min)
   [ ] Medium (25-35 min)
   [ ] Long (40-60 min)
   [ ] Very Long (60+ min)

4. Target audience / education level?
   [ ] Primary school (6-11)
   [ ] Secondary school (12-17)
   [ ] Undergraduate
   [ ] Master's / Advanced
   [ ] Professional
   [ ] General public
   [ ] Other (specify)

5. Any specific concepts or chapters to prioritize?
   [ ] Cover entire course
   [ ] Specific chapters (list them)
   [ ] Key themes (describe)

6. Conversational style preference?
   [ ] Academic (formal, technical)
   [ ] Natural (friendly, conversational)
   [ ] Debate (discussion-based)
   [ ] Socratic (question-led)
```

### Step 2: Claude Analyzes Complete Course

Claude reads entire course and:
- Identifies structure (chapters, sections, subsections, pages)
- Extracts key concepts with definitions
- Maps concept dependencies (prerequisites, relationships)
- Evaluates pedagogical density (concepts per page/section)
- Identifies difficult-to-explain points
- Notes examples and real-world applications
- Creates concept hierarchy

**Output**: Complete course analysis (internal, not shown to user)

### Step 3: Intelligent Segmentation

Based on:
- Course content and structure
- User format preference
- Target duration / size constraints
- Target audience level
- Concept dependencies and prerequisites

Claude calculates:
- Optimal number of segments
- Segment boundaries (chapter or concept level)
- Prerequisite ordering
- Duration estimates per segment
- Pedagogical flow and progression

**Output**: Segmentation plan (internal)

### Step 4: Instruction Generation

For each segment, Claude generates:
- Format-specific instruction blocks
- Copy-paste-ready for BookLM
- Includes:
  - Content scope (chapters/concepts covered)
  - Key concepts in order of importance
  - Points to explain thoroughly
  - Common misunderstandings to address
  - Real-world examples
  - Style and audience specifications
  - Duration targets (if applicable)

### Step 5: Output Delivery

Claude generates final document (DOCX or TXT):
- Analysis summary (course overview, density, segments)
- Segmentation table (all segments listed with metadata)
- Instruction blocks (one per segment, ready for BookLM)
- Usage guide (how to use with BookLM, best practices)

**Format**: Professional document, cleanly formatted, downloadable

## How Skill Executes

### 1. Interactive Flow
- Claude poses structured questionnaire
- User responds with course (file/URL/text) + preferences
- Conversational, adaptive to user's needs

### 2. Course Analysis (by Claude)
- **File Parsing**: Handles PDF, DOCX, TXT, MD, URL
- **Structure Extraction**: Identifies chapters, sections, hierarchy
- **Concept Extraction**: Pulls key concepts, definitions, examples
- **Dependency Mapping**: Identifies prerequisites and relationships
- **Density Evaluation**: Scores pedagogical density per section
- **Difficulty Assessment**: Flags complex concepts

See: `src/analyzer.md` for detailed logic

### 3. Segmentation (by Claude)
- **Format Constraints**: Respects duration/size limits
- **Pedagogical Constraints**: Keeps concepts intact, respects prerequisites
- **Audience Optimization**: Adjusts complexity for target level
- **Boundary Calculation**: Chapter-level or concept-level splits
- **Flow Validation**: Ensures logical progression

See: `src/segmenter.md` for detailed logic

### 4. Instruction Generation (by Claude)
- **Format-Specific**: Different templates for podcast, slides, guides, flashcards, video
- **Copy-Paste Ready**: Text ready to paste into BookLM Custom Instructions
- **Optimized**: Audio-friendly (for TTS), visual (for slides), testable (for flashcards)

See: `src/generator.md` and `templates/` for detailed templates

### 5. Output Creation (by Claude)
- **Format**: DOCX or TXT (user preference)
- **Structure**: Analysis summary → Segmentation table → Instruction blocks → Usage guide
- **Professional**: Clean formatting, readable, downloadable

See: `src/output.md` for detailed logic

## Input Requirements

### Course Document
- **Formats**: PDF, DOCX, TXT, MD, URL
- **Size**: Up to 100 MB (or multiple files)
- **Languages**: French, English (extensible)
- **Content**: Complete course (lectures, textbook chapters, training material, notes)

### User Preferences (via Interactive Questionnaire)
1. Course source (file/URL/text)
2. Desired output format
3. Target duration (for podcasts) or sizing (for other formats)
4. Target audience level
5. Specific chapters/concepts to prioritize
6. Conversational style preference

## Output Format

### Primary Deliverable: DOCX or TXT Document

```
BOOKLM-ORCHESTRATOR OUTPUT
══════════════════════════

📋 ANALYSIS SUMMARY
- Course title and source
- Pages/chapters analyzed
- Total concepts identified
- Pedagogical density estimate
- Recommended segments count

🎯 PROPOSED SEGMENTATION
- Segment 1: [title] | chapters X-Y | duration | key concepts (3-5 listed)
- Segment 2: [title] | chapters X-Y | duration | key concepts (3-5 listed)
- ... (all segments listed)

📝 INSTRUCTION BLOCKS (Copy-Paste Ready for BookLM)

## SEGMENT 1: [Title]
**Duration**: [X minutes / Y pages]
**Chapters**: [chapters covered]
**Audience**: [target level]
**Key Concepts**: [1. concept, 2. concept, ...]
**Style**: [conversational approach]

[BookLM Custom Instructions text - ready to copy-paste]

---

## SEGMENT 2: [Title]
...

📚 USAGE GUIDE
- How to use these blocks with BookLM
- Best practices
- Tips for each format
- Troubleshooting
```

### Optional Outputs
- CSV segment inventory (metadata only)
- Plain text version (if DOCX not preferred)

## Configuration (User-Selected)

Questionnaire collects these preferences:

| Setting | Options |
|---------|---------|
| **Output Format** | Podcast, Slides, Study Guide, Flashcards, Video, Mix |
| **Podcast Duration** | 10-15 min, 25-35 min, 40-60 min, 60+ min |
| **Audience Level** | Primary, Secondary, Undergrad, Master, Professional, General Public |
| **Style** | Academic, Natural, Debate, Socratic |
| **Content Scope** | Entire course, Specific chapters, Key themes |

## Skill File Structure

```
booklm-orchestrator/
├── SKILL.md                    # This file
├── README.md                   # User overview
├── SPECIFICATION.md            # Feature spec
├── DOCUMENTATION.md            # Technical details
│
├── src/
│   ├── analyzer.md             # Logic: analyze & extract
│   ├── segmenter.md            # Logic: calculate segments
│   ├── generator.md            # Logic: generate instructions
│   ├── output.md               # Logic: create DOCX/TXT
│   └── questionnaire.md        # Logic: interactive questions
│
├── templates/                  # Format templates
│   ├── instruction-podcast.md
│   ├── instruction-slides.md
│   ├── instruction-guides.md
│   ├── instruction-flashcards.md
│   └── instruction-video.md
│
├── guides/                     # User documentation
│   ├── GETTING_STARTED.md
│   ├── BEST_PRACTICES.md
│   └── TROUBLESHOOTING.md
│
├── examples/                   # Example inputs & outputs
└── .claude/
    ├── SETUP.md               # Private (gitignored)
    └── CLAUDE.md              # Development context
```

## How to Use This Skill

### As User
1. Type `/booklm-orchestrator`
2. Answer questionnaire (course + preferences)
3. Wait for analysis and generation
4. Download DOCX/TXT output
5. Copy instruction blocks into BookLM
6. BookLM generates your content

### As Developer
1. Read SPECIFICATION.md for requirements
2. Review src/ files for execution logic
3. Check templates/ for format specifications
4. Run with example-input-course.md for testing

See: `.claude/CLAUDE.md` for development setup

## Example Scenarios

### Scenario 1: Student Creating Revision Podcasts
- **Input**: 120-page Master's course on Public Administration
- **Requests**: 4 × 35-min podcasts, conversational style, Master level
- **Output**: 4 instruction blocks, each ready for BookLM
- **Result**: 4 high-quality podcasts for commute revision

### Scenario 2: Teacher Building Multi-Format Content
- **Input**: 80-page undergraduate course on Project Management
- **Requests**: 3 podcasts (25 min) + 15 slides + 12 study guides, undergraduate level
- **Output**: 30 instruction blocks (multiple formats)
- **Result**: Complete educational content suite in one session

### Scenario 3: Professional Training
- **Input**: Company onboarding documentation (60 pages)
- **Requests**: 1 × 45-min podcast + slides, professional audience
- **Output**: Podcast + slide instructions
- **Result**: Training material ready for internal platform

## What Skill Does / Doesn't Do

### ✅ Does
- Analyze complete courses (structure, concepts, dependencies)
- Calculate optimal segmentation for any format
- Generate BookLM-optimized instruction blocks
- Handle multi-format outputs simultaneously
- Provide pedagogical reasoning for segmentation
- Output professional DOCX/TXT documents

### ❌ Doesn't
- Generate actual audio/video content (BookLM does that)
- Modify original course material
- Create new content from scratch
- Validate factual accuracy
- Integrate directly with BookLM API (yet)

## Development Status

### Phase 1 (MVP) — Current
- [x] Project structure & documentation
- [ ] Analyzer (course parsing, concept extraction, dependency mapping)
- [ ] Segmenter (optimal segment calculation)
- [ ] Generator (instruction blocks for all 5 formats)
- [ ] Output (DOCX/TXT generation)
- [ ] Testing with real courses

### Phase 2 (Expansion) — September 2026
- [ ] Concept dependency visualization
- [ ] Advanced interactive questionnaire
- [ ] Format-specific optimizations

### Phase 3 (Integration) — October 2026
- [ ] BookLM API integration (if available)
- [ ] Usage analytics

### Phase 4 (Public) — November 2026
- [ ] Official registry listing
- [ ] Multilingual documentation
- [ ] Community feedback integration

---

**Last Updated**: June 2026  
**Status**: Phase 1 Development (MVP in progress)  
**Questions?** See [GETTING_STARTED.md](./guides/GETTING_STARTED.md) or [TROUBLESHOOTING.md](./guides/TROUBLESHOOTING.md)
