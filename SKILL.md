# BookLM-Orchestrator Skill Declaration

## Metadata

```yaml
name: booklm-orchestrator
title: BookLM-Orchestrator
version: 0.1.0
description: Claude Code skill that intelligently segments courses and generates optimized instructions for BookLM (podcasts, slides, study guides, flashcards, videos).
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

BookLM-Orchestrator analyzes complete courses and intelligently prepares them for BookLM (and other LLM-based content generators). It segments content based on user objectives (podcasts, slides, study guides, flashcards, videos) and generates detailed, copy-paste-ready instructions optimized for BookLM.

**Tagline**: "Transform your course into structured educational content — all ready for BookLM."

## Primary Commands

```
/booklm-orchestrator          Launch the skill with interactive questionnaire
/booklm-orchestrator analyze  Analyze a course without segmentation
/booklm-orchestrator segment  Segment a pre-analyzed course
/booklm-orchestrator help     Show detailed help
```

## Core Features

### 1. Intelligent Course Analysis
- Identifies document structure (chapters, sections, topics)
- Extracts key concepts per section
- Evaluates pedagogical density
- Maps conceptual dependencies
- Flags difficult-to-explain concepts

### 2. Smart Segmentation
- Calculates optimal segments based on:
  - Target format (podcast, slides, etc.)
  - Target duration (for podcasts)
  - Target audience
  - Pedagogical coherence
  - Concept dependencies

### 3. Instruction Generation
- Generates copy-paste-ready blocks for BookLM
- Each block includes:
  - Content scope (chapters/pages covered)
  - Key concepts to cover
  - Emphasis points
  - Target audience & style
  - Optimized for audio/TTS when applicable

### 4. Multiple Output Formats
- Podcast instructions (15 min — 60+ min)
- Slide/presentation instructions
- Study guide instructions
- Flashcard instructions
- Video instructions
- Mixed format combinations

## Workflow

```
Step 1: Upload Course
  ↓
Step 2: Answer Interactive Questions
  ↓
Step 3: Course Analysis
  ↓
Step 4: Intelligent Segmentation
  ↓
Step 5: Instruction Generation
  ↓
Step 6: Output Delivery (Markdown + Blocks)
```

## Input Requirements

### Course Document
- **Formats**: PDF, DOCX, TXT, URL
- **Size**: Up to 50 MB
- **Languages**: French, English (extensible)
- **Content**: Complete course (lectures, textbook chapters, training material)

### User Preferences (via Interactive Questionnaire)
1. Desired output format(s)
2. Target duration (for podcasts)
3. Target audience
4. Concepts/chapters to prioritize
5. Conversational style preference

## Output Format

### Primary Deliverable: Markdown Document

```
BOOKLM-ORCHESTRATOR OUTPUT
══════════════════════════

📋 ANALYSIS SUMMARY
- Pages/chapters analyzed
- Pedagogical density estimate
- Identified dependencies
- Number of segments generated

🎯 PROPOSED SEGMENTATION
- Segment 1: [title] | chapters X-Y | duration | key concepts
- Segment 2: [title] | chapters X-Y | duration | key concepts
- ...

📝 INSTRUCTION BLOCKS (Copy-Paste Ready)
[Each segment: BookLM-optimized instruction]

📚 USAGE GUIDE
[How to use blocks, best practices, troubleshooting]
```

### Optional Exports
- CSV segment inventory
- JSON metadata (for integrations)

## Configuration Parameters

| Parameter | Default | Options |
|-----------|---------|---------|
| Output Format | Podcast | Podcast, Slides, Guides, Flashcards, Video, Mix |
| Podcast Duration | 30 min | 10-15, 25-35, 40-60, 60+ |
| Target Audience | Master | Undergrad, Master, Professional, General Public |
| Conversational Style | Natural | Academic, Natural, Debate, Socratic |
| Segmentation Granularity | Balanced | Fine, Balanced, Coarse |
| Output Language | FR | FR, EN |

## Technical Architecture

### File Structure
```
src/
  ├── analyzer.md             # Course analysis logic
  ├── segmenter.md            # Segmentation algorithm
  ├── instruction-generator.md # Block generation
  ├── format-handler.md        # Format-specific logic
  └── utils.md                # Common utilities

templates/
  ├── instruction-podcast.md
  ├── instruction-slides.md
  ├── instruction-guides.md
  ├── instruction-flashcards.md
  └── instruction-video.md

guides/
  ├── GETTING_STARTED.md
  ├── BEST_PRACTICES.md
  └── TROUBLESHOOTING.md
```

### Key Dependencies
- Claude API (for text analysis)
- Document processing (PDF/DOCX/TXT parsing)
- Markdown generation

## Use Cases

### Use Case 1: Student Podcast Revision
- **Input**: 120-page Master's course
- **Target**: 4 × 35-min podcasts for commute revision
- **Output**: 4 instruction blocks → 4 high-quality podcasts via BookLM

### Use Case 2: Teacher Multi-Format Content
- **Input**: 80-page undergraduate course
- **Target**: 3 × 25-min podcasts + 12 study guides + 50 flashcards
- **Output**: Mixed format instructions → Complete educational content suite

### Use Case 3: Professional Training Material
- **Input**: Company onboarding documentation
- **Target**: 45-min training podcast + presentation slides
- **Output**: Structured content ready for internal training platform

## Limitations & Scope

### What BookLM-Orchestrator Does
✅ Analyze course structure and identify key concepts  
✅ Calculate optimal segmentation for different formats  
✅ Generate BookLM-optimized instructions  
✅ Handle multi-format outputs  
✅ Provide pedagogical guidance  

### What BookLM-Orchestrator Doesn't Do
❌ Generate actual audio/video content (BookLM handles that)  
❌ Modify original course content  
❌ Create entirely new content from scratch  
❌ Validate factual accuracy of course material  

## Roadmap

### Phase 1 (MVP) — August 2026
- [x] Basic course analyzer
- [x] Intelligent segmenter
- [x] Podcast instruction generator
- [ ] Simple Markdown output

### Phase 2 (Expansion) — September 2026
- [ ] Slides, guides, flashcards support
- [ ] Enhanced interactive questions
- [ ] Concept dependency visualization

### Phase 3 (Integration) — October 2026
- [ ] BookLM API integration (if available)
- [ ] Video format support
- [ ] Usage analytics

### Phase 4 (Public) — November 2026
- [ ] Official registry listing
- [ ] Multilingual documentation
- [ ] User feedback iteration

## Version History

### v0.1.0 (In Development)
- Initial specification and structure
- MVP planning and design

---

**Last Updated**: June 2026  
**Status**: Alpha (Development in progress)
