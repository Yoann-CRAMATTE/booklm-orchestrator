# Segmenter Module

## Purpose
Calculate optimal segmentation of analyzed course based on format, duration, and pedagogical constraints.

## Core Functions

### `calculateOptimalSegments(metadata, preferences)`
Computes the ideal number and boundaries of segments.

**Input**: CourseMetadata + UserPreferences  
**Output**: SegmentPlan[]

### `estimateSegmentDuration(segment, format)`
Estimates how long a segment will take in a given format (podcast minutes, reading time, etc.).

**Input**: Segment + Format  
**Output**: Duration (number in minutes/hours)

### `validateSegmentCompleteness(segment)`
Checks that a segment is pedagogically complete and self-contained.

**Input**: Segment + CourseMetadata  
**Output**: boolean + ValidationReport

### `optimizeForPedagogy(segments)`
Adjusts segment boundaries to respect pedagogical constraints.

**Input**: SegmentPlan[]  
**Output**: OptimizedSegmentPlan[]

---

## Constraints Handled

### Pedagogical Constraints
- ✅ Concept completeness (concepts aren't split across segments)
- ✅ Prerequisite ordering (prerequisites before dependents)
- ✅ Autonomy (each segment stands alone)

### Format Constraints
- ✅ Podcast: duration within ±10% of target
- ✅ Slides: ~1-2 slides per concept
- ✅ Guides: ~1-2 pages per concept
- ✅ Flashcards: one Q&A pair per concept

### Content Constraints
- ✅ Chapter boundaries respected
- ✅ No orphaned sections
- ✅ Balanced difficulty across segments

---

## Algorithm Details

(Implementation details to be added during development)

---

## Notes
- Phase 1: Basic chapter-level segmentation
- Phase 2: Concept-level granularity + dependency constraints
- Phase 3: ML-based optimization for specific audiences

---

**Status**: Specification (implementation pending)  
**Last Updated**: June 2026
