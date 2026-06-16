# Getting Started with BookLM-Orchestrator

## Prerequisites

- Claude Code installed (CLI or IDE extension)
- A course document (PDF, DOCX, TXT, or URL)
- ~5 minutes to answer interactive questions

---

## Quick Start (5 minutes)

### 1. Launch the Skill

```bash
/booklm-orchestrator
```

Or from Claude Code web:
```
Click: Skills → BookLM-Orchestrator
```

### 2. Upload Your Course

When prompted:
```
📄 Select your course file:
   [ ] Upload PDF/DOCX/TXT
   [ ] Paste URL
```

Examples:
- PDF: "my-course.pdf"
- URL: "https://example.com/course-material"
- TXT: "course-notes.txt"

### 3. Answer 5 Questions

The skill will ask:

**Q1: What output format(s)?**
```
[ ] Podcast (recommended for first-time)
[ ] Slides
[ ] Study Guide
[ ] Flashcards
[ ] Video
[ ] Mix of formats
```

Choose: **Podcast** (simplest for now)

---

**Q2: Target podcast duration?**
```
[ ] Short (10-15 min)
[ ] Medium (25-35 min) ← Default
[ ] Long (40-60 min)
[ ] Very Long (60+ min)
```

Choose: **Medium (25-35 min)**

---

**Q3: Target audience?**
```
[ ] Undergraduate students
[ ] Master's level ← Default
[ ] Professionals
[ ] General public
[ ] Other
```

Choose: **Master's level** (or your actual audience)

---

**Q4: Which concepts to prioritize?**
```
[ ] Cover everything ← Default
[ ] Specific chapters (which?)
[ ] Key themes (which?)
```

Choose: **Cover everything**

---

**Q5: Conversational style?**
```
[ ] Academic (strict, formal)
[ ] Natural (friendly, conversational) ← Default
[ ] Debate (discussion-based)
[ ] Socratic (question-led)
```

Choose: **Natural**

---

### 4. Wait for Analysis

```
⏳ Analyzing course...
   ✓ Structure identified
   ✓ Concepts extracted
   ✓ Segments calculated
```

Takes 1-3 minutes depending on course length.

### 5. Review Output

You'll receive a **Markdown document** with:

```
📋 ANALYSIS SUMMARY
─────────────────
Pages analyzed: 120
Chapters: 8
Estimated density: Medium
Segments generated: 4

🎯 SEGMENTATION
───────────────
Segment 1: Fundamentals (35 min) | Chapters 1-2
Segment 2: Core Concepts (35 min) | Chapters 3-4
Segment 3: Advanced Topics (35 min) | Chapters 5-6
Segment 4: Applications (35 min) | Chapters 7-8

📝 INSTRUCTION BLOCKS
──────────────────────
[Each segment has a copy-paste-ready block for BookLM]

## 📗 SEGMENT 1: Fundamentals

**Duration**: 35 minutes
**Chapters**: 1-2 (Pages 1-45)
**Audience**: Master's students

**Key concepts (in order)**:
1. Definition and history
2. Core principles
3. Basic applications

**Points to emphasize**:
- Clarify common confusion between X and Y
- Give 2-3 concrete examples
- Explain practical implications

**Style**: Conversational, friendly, real-world examples

─── COPY-PASTE FOR BOOKLM ───

Focus on chapters 1-2. Explain: definition and history, core principles, basic applications. Use conversational tone with real-world examples. Clarify confusion between X and Y with 2-3 concrete examples. Target audience: Master's students. Estimated duration: 35 minutes.

─────────────────────────────

[Similar blocks for segments 2, 3, 4...]
```

### 6. Copy & Paste into BookLM

For each segment:
1. Open [BookLM](https://notebooklm.google.com/)
2. Create new notebook
3. Add your course material
4. Click "Create" → "Podcast"
5. Click "Custom instructions"
6. **Paste the block** from BookLM section
7. Hit generate!
8. Enjoy your 35-min podcast 🎙️

---

## Complete Example

### Input Course
```
Title: "Introduction to Project Management"
Length: 85 pages
Chapters:
  1. What is Project Management? (pages 1-12)
  2. Frameworks & Methodologies (pages 13-28)
  3. Planning & Scheduling (pages 29-45)
  4. Risk Management (pages 46-62)
  5. Team Leadership (pages 63-78)
  6. Monitoring & Control (pages 79-85)
```

### Output (Segmentation)
```
Segment 1: Fundamentals (25 min)
  └─ Chapters 1-2, pages 1-28

Segment 2: Planning Phase (25 min)
  └─ Chapter 3, pages 29-45

Segment 3: Risk & Leadership (25 min)
  └─ Chapters 4-5, pages 46-78

Segment 4: Execution & Control (25 min)
  └─ Chapter 6, pages 79-85
```

### BookLM Instructions Generated
```
PODCAST 1: Project Management Fundamentals

Focus on chapters 1-2. Cover:
1. Definition of project management
2. Key frameworks (Waterfall, Agile, Hybrid)
3. Methodology comparison

Explain the differences between Agile and Waterfall with real examples. Use conversational tone. Duration: 25 minutes. Audience: Professionals learning PM.

───────────────────────────

PODCAST 2: Planning & Scheduling

Focus on chapter 3. Cover:
1. Work breakdown structure (WBS)
2. Gantt charts and timelines
3. Resource allocation

Clarify how WBS differs from project scope. Use real project examples. Duration: 25 minutes. Audience: Professionals.

[... and so on]
```

---

## Tips for Best Results

### ✅ DO:
- Use complete, well-structured courses
- Include chapter titles and section headings
- Provide clear page numbers or sections
- Specify your actual target audience

### ❌ DON'T:
- Use fragmented or incomplete materials
- Upload extremely dense textbooks (>300 pages)
- Have unclear chapter structures
- Choose "anything goes" for audience

---

## Troubleshooting

### Problem: "Upload failed"
**Solution**: 
- Try a different format (PDF → DOCX, or vice versa)
- Check file size (<50 MB)
- Ensure file isn't corrupted

### Problem: "Segments seem too long/short"
**Solution**:
- Adjust podcast duration preference
- Try "Fine" granularity instead of "Balanced"
- Manually adjust segment boundaries (expert mode)

### Problem: "Missing concepts"
**Solution**:
- Check you chose "Cover everything" in Q4
- Ensure course file includes all chapters
- Run analysis again with adjusted parameters

### Problem: "BookLM prompt too long"
**Solution**:
- Copy to text editor first if clipboard is limited
- Split into 2 smaller prompts if needed
- Use "Coarse" granularity for fewer segments

---

## Next Steps

After your first podcast:

1. **Refine**: Adjust segmentation if needed
2. **Experiment**: Try different formats (slides, guides)
3. **Scale**: Process multiple courses
4. **Customize**: Use expert parameters for fine-tuning

---

## Support

Stuck? Check:
- [BEST_PRACTICES.md](./BEST_PRACTICES.md) for optimization tips
- [TROUBLESHOOTING.md](./TROUBLESHOOTING.md) for common issues
- Main [README.md](../README.md) for overview

---

**Duration**: This guide takes ~5 min to read, ~20 min for full first run.

**Next**: [BEST_PRACTICES.md](./BEST_PRACTICES.md) — Advanced tips for better results.
