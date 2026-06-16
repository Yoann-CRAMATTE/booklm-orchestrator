# Format Handler Module

## Purpose
Apply format-specific customizations and optimizations to instruction blocks.

## Supported Formats

| Format | Optimized For | Key Features |
|--------|---------------|-------------|
| **Podcast** | Audio, conversational | Time-constrained, narrative, TTS-friendly |
| **Slides** | Visual, presentation | Concise bullets, speaker notes, 1 concept/slide |
| **Study Guide** | Reading, comprehension | Q&A structure, detailed, examples |
| **Flashcards** | Memory, testing | Question-answer pairs, spaced repetition |
| **Video** | Visual + audio | Script, scene descriptions, B-roll suggestions |

---

## Core Functions

### `formatForPodcast(block, duration)`
Optimizes instruction for audio podcast format.

**Features**:
- Conversational language
- Audio-optimized text (TTS-friendly)
- Pacing and transition cues
- Duration-aware scaling

### `formatForSlides(block, slideCount)`
Converts instruction to slide format.

**Features**:
- Bullet-point structure
- One concept per slide minimum
- Speaker notes
- Visual element placeholders

### `formatForGuide(block)`
Creates detailed study guide format.

**Features**:
- Q&A section structure
- Detailed explanations
- Key formulas/summaries
- Real-world examples

### `formatForFlashcards(block)`
Generates flashcard Q&A pairs.

**Features**:
- Question-answer pairs
- Multiple difficulty levels
- Spaced repetition hints
- Retrieval cues

### `formatForVideo(block, duration)`
Produces video script and descriptions.

**Features**:
- Voiceover script
- Scene descriptions
- B-roll suggestions
- Visual transition notes

---

## Format Rules

### Podcast Rules
- Max 2-3 sentences per paragraph (for spoken pacing)
- Avoid technical jargon or explain inline
- Include transition phrases ("Now that we've covered...", "Let's move to...")
- Audio timestamps for navigation
- Clear topic introduction & conclusion per segment

### Slide Rules
- 3-5 bullet points maximum per slide
- 1 concept minimum, 2 maximum per slide
- Visual element placeholders (diagrams, images, charts)
- Speaker notes (detailed explanation)
- 1-2 slides per key concept

### Study Guide Rules
- Question → Answer structure
- Answers include examples and explanations
- Key terms in bold or highlighted
- Summary boxes for formulas/critical info
- End-of-section review questions

### Flashcard Rules
- Front: Clear, testable question
- Back: Concise answer + memory cue
- Multiple difficulty levels (beginner, intermediate, advanced)
- Spaced repetition hints (when to review)
- Related concept cross-references

### Video Rules
- Script is conversational, natural speech
- Scene descriptions precise (no ambiguity)
- B-roll suggestions include timing
- Voiceover sync with visual changes
- Graphics/text overlay specifications

---

## Extension Points

To add a new format:
1. Create `formatFor{Format}()` function
2. Define format-specific rules
3. Add template in `templates/`
4. Register in format registry
5. Update questionnaire

---

## Notes
- Phase 1: Podcast format focus
- Phase 2: Slides, guides, flashcards
- Phase 3: Video format + audio testing

---

**Status**: Specification (implementation pending)  
**Last Updated**: June 2026
