# BookLM-Orchestrator Development Context

## Project Overview

**BookLM-Orchestrator** is a Claude Code skill that analyzes complete courses and intelligently prepares them for BookLM (or other LLM-based content generators). It segments content based on user objectives and generates optimized copy-paste instructions for BookLM.

**Main Goal**: Enable anyone to transform a course into structured educational content (podcasts, slides, guides, flashcards, videos) optimized for BookLM.

---

## Key Resources

### Public Documentation
- **[SPECIFICATION.md](../SPECIFICATION.md)** - Complete feature spec and architecture
- **[README.md](../README.md)** - User-friendly overview
- **[SKILL.md](../SKILL.md)** - Skill declaration and metadata
- **[DOCUMENTATION.md](../DOCUMENTATION.md)** - Technical deep-dive

### User Guides
- **[guides/GETTING_STARTED.md](../guides/GETTING_STARTED.md)** - First-time user walkthrough
- **[guides/BEST_PRACTICES.md](../guides/BEST_PRACTICES.md)** - Optimization tips
- **[guides/TROUBLESHOOTING.md](../guides/TROUBLESHOOTING.md)** - Problem-solving

### Technical Modules
- **[src/analyzer.md](../src/analyzer.md)** - Course analysis logic
- **[src/segmenter.md](../src/segmenter.md)** - Segmentation algorithm
- **[src/instruction-generator.md](../src/instruction-generator.md)** - Instruction block generation
- **[src/format-handler.md](../src/format-handler.md)** - Format-specific customizations
- **[src/utils.md](../src/utils.md)** - Common utilities

### Templates & Examples
- **[templates/](../templates/)** - Instruction templates for each format
- **[examples/example-input-course.md](../examples/example-input-course.md)** - Example input
- **[examples/example-output-podcasts.md](../examples/example-output-podcasts.md)** - Example output

---

## Development Roadmap

### Phase 1 (MVP) — August 2026
**Goal**: Basic course analysis and podcast segmentation

- [x] Project structure & documentation
- [ ] Implement analyzer module (course parsing, concept extraction)
- [ ] Implement segmenter module (optimal segmentation calculation)
- [ ] Implement instruction generator (podcast format)
- [ ] Generate example outputs
- [ ] User testing with real courses

**Deliverables**:
- Functional analyzer
- Intelligent segmenter
- Podcast instruction generator
- Markdown output document

### Phase 2 (Expansion) — September 2026
**Goal**: Multi-format support

- [ ] Format handlers for slides, guides, flashcards
- [ ] Enhanced interactive questionnaire
- [ ] Better concept dependency mapping
- [ ] Format-specific optimizations

### Phase 3 (Integration) — October 2026
**Goal**: External integrations

- [ ] BookLM API integration (if available)
- [ ] Video format support
- [ ] Usage analytics
- [ ] Custom format extension points

### Phase 4 (Public) — November 2026
**Goal**: Official release

- [ ] Registry listing
- [ ] Multilingual documentation
- [ ] Community feedback & iteration
- [ ] Performance optimization

---

## Cocreator & Contact

**Yoann CRAMATTE**
- Organization: Grand Belfort — Pôle Relations Usagers (DEE-GDU)
- Email: ycramatte@gmail.com
- GitHub: ycramatte

---

## Key Design Decisions

### 1. Markdown-First
- Documentation is Markdown (readable, version-controllable)
- Skill operates on Markdown (easy for users to edit)
- Output is Markdown (can be easily imported elsewhere)

### 2. Security by Default
- Private configuration in `.claude/SETUP.md` (gitignored)
- No credentials or API keys in public files
- User data privacy respected (no external calls without consent)

### 3. Template-Based
- Each format has clear template
- Templates are human-readable, easily customizable
- Instructions are copy-paste ready for BookLM

### 4. Pedagogically Sound
- Concept dependencies validated
- Segmentation respects learning progression
- Output includes pedagogical reasoning

### 5. User-Centric
- Interactive questionnaire guides setup
- Clear error messages and troubleshooting
- Expert mode for advanced users
- Examples provided for all features

---

## Important Notes for Development

### When Working on Each Module

**Analyzer** (src/analyzer.md):
- Must handle multiple document formats (PDF, DOCX, TXT, URL)
- Should identify chapter structure reliably
- Extract concepts without over-fitting to writing style
- Evaluate pedagogical density objectively

**Segmenter** (src/segmenter.md):
- Respect concept completeness (don't split concepts)
- Maintain pedagogical ordering (prerequisites first)
- Balance segment sizes for format constraints
- Provide reasoning for segment boundaries

**Instruction Generator** (src/instruction-generator.md):
- Optimize for audio when relevant (TTS-friendly)
- Make instructions actionable (not vague)
- Include concrete examples
- State emphasis clearly

**Format Handlers** (src/format-handler.md):
- Each format has specific rules (see templates/)
- Don't mix formats (one instruction block per format)
- Validate format constraints (e.g., slide count, card count)
- Provide format-specific warnings

### Testing Approach
- Use example input course for consistency
- Test with real BookLM to validate output quality
- Iterate based on BookLM generation results
- Collect user feedback for improvements

### Documentation Standards
- Keep user docs jargon-free
- Include real-world examples
- Provide step-by-step instructions
- Add troubleshooting for common issues

---

## Skills & Tools to Use During Development

### Claude Code Skills
- **[engineering:architecture](...)** - Design decisions
- **[engineering:testing-strategy](...)** - Test planning
- **[engineering:documentation](...)** - Docs quality
- **[simplify](...)** - Code cleanup

### External Tools
- BookLM (validate output quality)
- GitHub (version control, issue tracking)
- Text editors (Markdown editing)

---

## Branching Strategy (When on GitHub)

```
main                 (stable, released versions)
  └─ develop         (integration branch)
      ├─ feature/analyzer
      ├─ feature/segmenter
      ├─ feature/instruction-generator
      └─ feature/format-slides
```

---

## How to Contribute (Future)

1. Fork repository
2. Create feature branch
3. Make changes respecting design decisions
4. Test with example course
5. Update documentation
6. Submit pull request with clear description

---

## Performance Targets

- Analyzer: <10s for 100-page course
- Segmenter: <5s for optimal calculation
- Output generation: <5s for Markdown
- Total end-to-end: <30s

---

## Known Limitations (Phase 1)

- Single-language courses only (EN/FR)
- No nested concept dependencies
- No audio quality validation
- No automatic content modification (only suggests)
- Manual format templates (no AI generation yet)

---

## Success Criteria (MVP)

✅ User can upload course  
✅ Questionnaire collects requirements  
✅ Analyzer extracts concepts and structure  
✅ Segmenter produces coherent segments  
✅ Instruction generator creates BookLM-ready blocks  
✅ Example output is production-ready  
✅ Markdown output is clean and professional  
✅ Documentation is clear and complete  

---

## Quick Start for Development

1. **Understand the spec**: Read SPECIFICATION.md
2. **See an example**: Read example-input-course.md
3. **Review output**: Read example-output-podcasts.md
4. **Check architecture**: Read DOCUMENTATION.md
5. **Start with Phase 1**: Begin with analyzer module

---

**Last Updated**: June 2026  
**Project Status**: Phase 1 Development Starting  
**Next Step**: Implement analyzer module
