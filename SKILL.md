---
name: booklm-orchestrator
description: Analyze complete courses, intelligently segment them, and generate optimized instructions for BookLM (podcasts, slides, guides, flashcards, videos). Use when users want to transform courses into structured educational content.
license: MIT
---

# BookLM-Orchestrator

Transform your course into structured educational content — all ready for BookLM.

## What This Skill Does

BookLM-Orchestrator analyzes complete courses and intelligently prepares them for BookLM generation. The skill:

1. **Analyzes** your course (structure, concepts, dependencies)
2. **Segments** it optimally (respecting pedagogical flow)
3. **Generates** format-specific instructions (podcast, slides, guides, flashcards, video)
4. **Outputs** copy-paste-ready blocks for BookLM

## How to Use

Type `/booklm-orchestrator` and answer the interactive questionnaire:

- **Provide your course**: Upload PDF/DOCX/TXT, paste content, or provide URL
- **Choose format**: Podcast, slides, study guide, flashcards, video, or mix
- **Specify target**: Duration (for podcasts) or sizing (for other formats)
- **Select audience**: Primary school through professional level
- **Preference**: Conversational style (academic, natural, debate, socratic)

The skill then:
1. Reads your complete course
2. Extracts structure, concepts, and dependencies
3. Calculates optimal segmentation
4. Generates instruction blocks for each segment
5. Delivers professional DOCX/TXT output

## Output Example

```
# BOOKLM-ORCHESTRATOR OUTPUT

Cours: Droit de la Décentralisation

---

INSTRUCTIONS:
For each episode below:
1. Copy the full text of the block
2. Create a new podcast in BookLM
3. Paste into "Custom Instructions"
4. Generate

---

## EPISODE 1: Foundations — What is Decentralization?
[Instruction block optimized for BookLM TTS]

## EPISODE 2: Constitutional Principles
[Instruction block optimized for BookLM TTS]

... (all episodes)
```

## Key Features

✅ **Language Detection**: Questionnaire adapts to user's language (FR/EN/RU/ZH/ES/etc.)  
✅ **Format-Specific Quantification**: Exact numbers (minutes, slides, pages, cards)  
✅ **Pedagogical Segmentation**: Respects learning progression and concept dependencies  
✅ **TTS Optimization**: Audio rules for clear BookLM speech synthesis  
✅ **Multi-Format Support**: Podcasts, slides, study guides, flashcards, videos  
✅ **Copy-Paste Ready**: Instructions directly into BookLM Custom Instructions  

## Supported Formats

| Format | Duration/Size | Output |
|--------|---|---|
| **Podcast** | 10-15, 25-35, 40-60, 60+ min | Audio instruction blocks |
| **Slides** | 15, 30, 50, 75 slides | Presentation instructions |
| **Study Guide** | 7, 15, 30, 60 pages | Q&A instructional blocks |
| **Flashcards** | 30, 60, 100, 150 cards | Memory instruction blocks |
| **Video** | 15, 60, 120 min | Script + scene instructions |

## Example Use Cases

**Student**: "Transform my 120-page Master's course into 4×35-min podcasts for revision"  
**Teacher**: "Create multi-format content (podcasts + slides + study guides) from undergraduate course"  
**Professional**: "Build training material (podcast + slides) from company onboarding docs"

## Input Requirements

- **Course**: PDF, DOCX, TXT, Markdown, or URL (up to 100 MB)
- **Language**: French, English, Russian, Chinese, Spanish, others supported
- **Content**: Complete course (lectures, textbooks, training materials, notes)

## Output Format

- **Primary**: Professional DOCX or TXT document
- **Contains**: Analysis summary, segmentation table, instruction blocks, usage guide
- **Blocks**: Formatted for direct copy-paste into BookLM Custom Instructions

## Technical Details

**Architecture**:
- Questionnaire (interactive Q&A with language detection)
- Analyzer (course parsing, concept extraction, dependency mapping)
- Segmenter (optimal segment calculation respecting pedagogy)
- Generator (format-specific instruction blocks)
- Output (DOCX/TXT delivery)

**Design Principles**:
- Markdown-first (documentation and execution both in Markdown)
- Pedagogically sound (respects learning progression)
- Copy-paste ready (no additional formatting needed)
- Language-aware (detects and adapts to user language)
- Format-specific (each output type optimized for its medium)

## Status

**Phase 1 MVP**: COMPLETE
- ✅ Core architecture (questionnaire → analyzer → segmenter → generator → output)
- ✅ Language detection and multilingual support
- ✅ All 5 formats supported
- ✅ TTS audio optimization rules
- ✅ GitHub repository (open source, MIT license)

**Current Testing**: Phase 1 validation with BookLM (June 2026)

**Roadmap**:
- Phase 2: Advanced segmentation options, enhanced templates
- Phase 3: BookLM API integration (if available)
- Phase 4: Public release and community feedback

## Links

- **Repository**: https://github.com/Yoann-CRAMATTE/booklm-orchestrator
- **Issues**: https://github.com/Yoann-CRAMATTE/booklm-orchestrator/issues
- **Documentation**: See README.md in repository

## Author

Yoann CRAMATTE  
Grand Belfort — Pôle Relations Usagers (DEE-GDU)  
Email: ycramatte@gmail.com
