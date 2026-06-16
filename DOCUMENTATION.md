# BookLM-Orchestrator — Technical Documentation

## Overview

This document provides comprehensive technical documentation for the BookLM-Orchestrator skill, including architecture, algorithms, implementation details, and extension points.

## Table of Contents

1. [Architecture](#architecture)
2. [Core Modules](#core-modules)
3. [Algorithms](#algorithms)
4. [Data Structures](#data-structures)
5. [API Reference](#api-reference)
6. [Extension Points](#extension-points)
7. [Testing Strategy](#testing-strategy)

---

## Architecture

### High-Level Flow

```
┌─────────────────┐
│  Course Input   │ (PDF, DOCX, TXT, URL)
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   Analyzer      │ Identifies structure, concepts, dependencies
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Segmenter      │ Calculates optimal chunks based on format & preferences
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│Instruction Gen. │ Generates BookLM-optimized blocks per segment
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Output Layer   │ Markdown document + optional exports (CSV, JSON)
└─────────────────┘
```

### Module Responsibilities

| Module | Responsibility | Input | Output |
|--------|-----------------|-------|--------|
| **Analyzer** | Extract structure, concepts, dependencies | Raw document | CourseMetadata + ConceptMap |
| **Segmenter** | Calculate optimal segments | CourseMetadata + UserPreferences | SegmentPlan[] |
| **InstructionGen** | Create BookLM-friendly blocks | SegmentPlan + Template | InstructionBlock[] |
| **FormatHandler** | Format-specific customization | InstructionBlock + Format | FormattedBlock |
| **Output** | Generate final document | FormattedBlock[] | Markdown + Optional exports |

---

## Core Modules

### 1. Analyzer Module (`src/analyzer.md`)

**Purpose**: Understand course structure and identify key pedagogical elements.

**Key Functions**:
- `parseDocument(file)` → DocumentTree
- `extractConcepts(section)` → Concept[]
- `evaluatePedagogicalDensity(section)` → DensityScore
- `mapDependencies(concepts)` → DependencyGraph
- `identifyDifficultPoints(content)` → DifficultPoint[]

**Algorithm**:
1. Parse document structure recursively
2. For each section, extract entities (terms, definitions, examples)
3. Score pedagogical density (concept concentration per page)
4. Build concept dependency graph (X requires understanding Y)
5. Flag complex topics (long explanations, unusual terminology)

**Output**: `CourseMetadata` structure
```
{
  title: string
  totalPages: number
  chapters: Chapter[]
  concepts: Concept[]
  dependencies: DependencyGraph
  difficultPoints: DifficultPoint[]
  estimatedReadingTime: number
  pedagogicalDensity: "low" | "medium" | "high"
}
```

### 2. Segmenter Module (`src/segmenter.md`)

**Purpose**: Calculate optimal segmentation based on format, duration, and pedagogical constraints.

**Key Functions**:
- `calculateOptimalSegments(metadata, preferences)` → SegmentPlan[]
- `estimateSegmentDuration(segment, format)` → number (minutes)
- `validateSegmentCompleteness(segment)` → boolean
- `optimizeForPedagogy(segments)` → SegmentPlan[]

**Algorithm**:
1. Calculate required number of segments based on:
   - Total content volume
   - Format (podcast durations vary)
   - Target audience complexity
2. Split content respecting:
   - Chapter boundaries (avoid mid-chapter cuts)
   - Concept completeness (each segment covers full concepts)
   - Dependency constraints (prerequisite concepts before dependent ones)
3. Balance segments:
   - Podcast: aim for target duration ±10%
   - Slides: 1-3 slides per concept
   - Guides: 1-3 pages per concept
4. Validate each segment is pedagogically autonomous

**Output**: `SegmentPlan[]`
```
{
  id: string
  title: string
  chaptersIncluded: string[]
  pageRange: [number, number]
  keyConcepts: string[]
  estimatedDuration: number
  complexity: "beginner" | "intermediate" | "advanced"
  dependencies: string[] // IDs of prerequisite segments
}
```

### 3. Instruction Generator (`src/instruction-generator.md`)

**Purpose**: Create optimized BookLM instructions for each segment.

**Key Functions**:
- `generateInstruction(segment, format, template)` → InstructionBlock
- `optimizeForTTS(text)` → string (audio-friendly version)
- `createBookLMPrompt(block)` → string (copy-paste ready)

**Algorithm**:
1. Select template based on format (podcast, slide, etc.)
2. Fill template with:
   - Segment-specific metadata (chapters, pages, duration)
   - Key concepts (ordered by importance)
   - Explanation requirements (common confusions, examples needed)
   - Audience & style guidelines
3. Optimize text for audio (if applicable):
   - Break long sentences
   - Replace problematic symbols
   - Adjust pacing indicators
4. Wrap in "Copy-Paste for BookLM" section

**Output**: `InstructionBlock`
```
{
  segmentId: string
  title: string
  format: "podcast" | "slide" | "guide" | ...
  metadata: {
    chapters: string[]
    pages: [number, number]
    duration: number
    audience: string
  }
  keyConcepts: {
    name: string
    priority: number
    explainationNeeds: string[]
  }[]
  style: {
    conversational: "academic" | "natural" | "debate" | "socratic"
    length: "short" | "medium" | "long"
    emphasisPoints: string[]
  }
  booklmPrompt: string // Ready to copy-paste
}
```

### 4. Format Handler (`src/format-handler.md`)

**Purpose**: Apply format-specific customizations and optimizations.

**Supported Formats**:
- Podcast (conversational, time-constrained)
- Slides (visual, concise)
- Study Guides (detailed, question-focused)
- Flashcards (Q&A pairs, memory-focused)
- Video (visual + narrative)

**Key Functions**:
- `formatForPodcast(block, duration)` → PodcastBlock
- `formatForSlides(block, slideCount)` → SlideBlock[]
- `formatForGuide(block)` → GuideBlock
- `formatForFlashcards(block)` → FlashcardBlock[]
- `formatForVideo(block, duration)` → VideoBlock

**Format-Specific Rules**:

**Podcast**:
- Conversational, narrative-driven
- Time-based constraints
- Audio-optimized language
- Include transitions between topics

**Slides**:
- Concise bullets (3-5 per slide)
- Visual element placeholders
- One concept per slide minimum
- Notes for speaker

**Study Guides**:
- Q&A structure
- Detailed explanations
- Real-world examples
- Key formula/summary boxes

**Flashcards**:
- Question → Answer pairs
- Short, testable content
- Multiple difficulty levels
- Spaced repetition hints

**Video**:
- Scene descriptions
- B-roll suggestions
- Voiceover script
- Visual transitions

### 5. Output & Utils (`src/utils.md`)

**Key Functions**:
- `generateMarkdown(blocks)` → string
- `exportCSV(segments)` → CSV data
- `exportJSON(metadata)` → JSON data
- `estimateDuration(text, format)` → number
- `validatePedagogy(segments)` → ValidationReport

---

## Algorithms

### Concept Dependency Mapping

**Purpose**: Identify prerequisite relationships between concepts.

**Algorithm**:
1. For each concept, analyze its explanation
2. Extract referenced concepts (mentions, examples)
3. Build directed graph: A → B means "understanding A helps with B"
4. Compute transitive closure: identify chains A → B → C
5. Flag cycles (circular dependencies) as warnings

**Output**: DependencyGraph

### Pedagogical Completeness Validation

**Purpose**: Ensure each segment is self-contained pedagogically.

**Criteria**:
- All prerequisites of included concepts are covered earlier in segment
- No dangling references to undefined concepts
- Examples are self-explanatory or fully included
- Terminology is defined within segment or in earlier segments

**Algorithm**:
1. For each segment, extract all referenced concepts
2. Check against CourseMetadata dependency graph
3. Validate that prerequisites appear before dependents
4. Generate warnings for any violations

---

## Data Structures

### CourseMetadata
```
{
  title: string
  sourceFile: string
  totalPages: number
  language: "fr" | "en"
  chapters: {
    id: string
    title: string
    pageRange: [number, number]
    sections: Section[]
  }[]
  concepts: {
    id: string
    name: string
    definition: string
    firstMentionedPage: number
    frequency: number
    difficulty: "beginner" | "intermediate" | "advanced"
  }[]
  dependencies: {
    conceptA_id: string
    conceptB_id: string
    type: "prerequisite" | "related" | "example"
  }[]
  pedagogicalDensity: {
    byChapter: { chapterId: string, density: "low" | "medium" | "high" }[]
    overall: "low" | "medium" | "high"
  }
  estimatedTotalReadingTime: number // hours
}
```

### SegmentPlan
```
{
  id: string
  order: number
  title: string
  chaptersIncluded: string[]
  pageRange: [number, number]
  keyConcepts: {
    conceptId: string
    priority: 1 | 2 | 3 // 1 = critical, 3 = nice-to-know
  }[]
  estimatedDuration: {
    podcast: number // minutes
    reading: number // minutes
    practice: number // minutes
  }
  complexity: "beginner" | "intermediate" | "advanced"
  pedagogicalNotes: string[]
  prerequisites: string[] // segment IDs
}
```

### InstructionBlock
```
{
  segmentId: string
  format: "podcast" | "slide" | "guide" | "flashcard" | "video"
  metadata: {
    chaptersIncluded: string[]
    pageRange: [number, number]
    duration: number
    audience: string
    language: "fr" | "en"
  }
  content: {
    title: string
    keyConcepts: {
      name: string
      priority: number
      explainAsNeeded: string[]
    }[]
    commonMisunderstandings: string[]
    realWorldExamples: string[]
    emphasizePoints: string[]
  }
  style: {
    conversational: "academic" | "natural" | "debate" | "socratic"
    explainationLength: "concise" | "medium" | "detailed"
    includeExamples: boolean
    includeIllustrations: boolean
  }
  booklmPrompt: string // Ready to copy-paste into BookLM Custom Instructions
}
```

---

## API Reference

(To be completed as implementation progresses)

---

## Extension Points

### Adding New Formats

1. Create format handler in `src/format-handler.md`
2. Add template in `templates/instruction-{format}.md`
3. Register in format registry
4. Update questionnaire to include new format option

### Adding Language Support

1. Update analyzer to handle language-specific parsing
2. Create templates in target language
3. Add language code to CourseMetadata
4. Update documentation

### Integrating with External APIs

1. Create integration module in `src/integrations/`
2. Implement API-specific instruction optimizations
3. Add configuration options in skill questionnaire

---

## Testing Strategy

(To be defined during Phase 1 development)

- Unit tests for core algorithms
- Integration tests for end-to-end workflows
- Pedagogical validation tests
- Audio/TTS optimization tests

---

**Last Updated**: June 2026  
**Status**: Framework documentation (implementation in progress)
