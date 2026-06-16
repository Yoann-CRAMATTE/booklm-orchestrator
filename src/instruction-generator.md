# Instruction Generator Module

## Purpose
Generate BookLM-optimized instruction blocks for each segment.

## Core Functions

### `generateInstruction(segment, format, template)`
Creates a complete instruction block for a segment.

**Input**: SegmentPlan + Format + Template  
**Output**: InstructionBlock

### `optimizeForTTS(text)`
Transforms text to be audio-friendly (short sentences, clear punctuation).

**Input**: string (text)  
**Output**: string (TTS-optimized)

### `createBookLMPrompt(block)`
Wraps instruction in copy-paste-ready format for BookLM Custom Instructions field.

**Input**: InstructionBlock  
**Output**: string (BookLM prompt)

---

## Template Selection

- **Podcast**: Conversational, narrative structure, time-constrained
- **Slides**: Bullet-point focus, one concept per slide
- **Study Guide**: Q&A structure, detailed explanations
- **Flashcards**: Question-answer pairs, memory-optimized
- **Video**: Scene descriptions, voiceover script, B-roll notes

---

## Output Structure

Each InstructionBlock includes:
- Segment metadata (chapters, pages, duration)
- Ordered list of key concepts (by importance)
- Common misunderstandings to address
- Real-world examples to include
- Style and tone guidelines
- Copy-paste-ready BookLM prompt

---

## TTS Optimization Rules

- ❌ Avoid: "e.g.", "$100K", "12/31/2026"
- ✅ Use: "for example", "one hundred thousand dollars", "December 31, 2026"
- ✅ Break long sentences (max ~20 words)
- ✅ Use clear punctuation (commas, periods, em-dashes)

---

## Notes
- Phase 1: Basic podcast instructions
- Phase 2: Slides, guides, flashcards templates
- Phase 3: Format-specific optimizations + audio testing

---

**Status**: Specification (implementation pending)  
**Last Updated**: June 2026
