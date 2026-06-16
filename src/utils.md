# Utils Module

## Purpose
Common utility functions and helpers used across modules.

## Core Functions

### `generateMarkdown(blocks, metadata)`
Creates final Markdown document from instruction blocks.

**Input**: InstructionBlock[] + CourseMetadata  
**Output**: string (Markdown)

**Structure**:
- Analysis Summary (pages, chapters, density, segments)
- Segmentation Overview (table of segments)
- Instruction Blocks (one per segment, copy-paste ready)
- Usage Guide (how to use, best practices)

### `exportCSV(segments)`
Exports segment list as CSV for tracking.

**Input**: SegmentPlan[]  
**Output**: CSV string

**Columns**:
- Segment ID
- Title
- Chapters Included
- Page Range
- Key Concepts
- Estimated Duration
- Complexity

### `exportJSON(metadata)`
Exports full analysis as JSON for integrations.

**Input**: CourseMetadata + SegmentPlan[]  
**Output**: JSON string

### `estimateDuration(text, format)`
Estimates how long content will take in a given format.

**Input**: string (text) + Format  
**Output**: number (minutes)

**Rules**:
- Podcast: ~150 words per minute (conversational speech)
- Reading: ~250 words per minute
- Practice: 2x reading time

### `validatePedagogy(segments)`
Comprehensive pedagogical validation across segments.

**Input**: SegmentPlan[]  
**Output**: ValidationReport

**Checks**:
- ✅ Concept completeness
- ✅ Dependency ordering
- ✅ Segment autonomy
- ✅ No orphaned content
- ⚠️ Complexity balance
- ⚠️ Duration consistency

### `sanitizeForBookLM(text)`
Removes or replaces problematic content for BookLM input.

**Input**: string (text)  
**Output**: string (sanitized)

**Conversions**:
- Special symbols → descriptions
- Excessive formatting → clean markdown
- Code snippets → inline or description

---

## Helper Functions

### `extractChapterInfo(metadata, chapterId)`
Gets chapter information from metadata.

### `getConceptByName(concepts, name)`
Looks up concept by name.

### `calculateReadingTime(text)`
Estimates reading time for given text.

### `optimizeForAudio(text)`
Makes text audio-friendly (basic version, see instruction-generator for full).

### `formatDuration(minutes)`
Converts minutes to readable duration ("35 min", "1h 15m").

---

## Constants

```
MIN_PODCAST_DURATION = 10 // minutes
MAX_PODCAST_DURATION = 120 // minutes
WORDS_PER_MINUTE_PODCAST = 150
WORDS_PER_MINUTE_READING = 250
MIN_SEGMENT_COMPLEXITY = 1
MAX_SEGMENT_COMPLEXITY = 5
```

---

## Notes
- Phase 1: Basic utilities for markdown output
- Phase 2: Enhanced CSV/JSON exports
- Phase 3: Integration helpers for external APIs

---

**Status**: Specification (implementation pending)  
**Last Updated**: June 2026
