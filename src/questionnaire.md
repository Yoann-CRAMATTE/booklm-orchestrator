# Questionnaire Logic

This file describes the interactive questionnaire Claude should execute when skill is launched.

## Flow: Questions to Ask User

**Welcome message:**
```
Welcome to BookLM-Orchestrator!

I'll help you transform your course into structured educational content 
ready for BookLM (or any LLM-based content generator).

Let's start by gathering some information about your course and goals.
```

---

## Question 1: Course Source

**Ask:**
```
How would you like to provide your course?

Option A: Upload a file (PDF, DOCX, TXT, MD)
Option B: Provide a URL link to your course
Option C: Paste the course text directly here

Which would you prefer? (Answer: A, B, or C)
```

**Processing:**
- If A: Ask for file upload
- If B: Ask for URL
- If C: Ask user to paste text (can be multi-line)

Once received, Claude should:
- Download/read the course
- Confirm size and format
- Proceed to Question 2

---

## Question 2: Desired Output Format

**Ask:**
```
What output format do you want?

1. Podcast (conversational, timed episodes)
2. Slides (visual, presentation format)
3. Study Guide (Q&A, detailed explanations)
4. Flashcards (memory-focused, Q&A pairs)
5. Video (script + visual descriptions)
6. Mix (multiple formats at once)

Choose 1-6 (or multiple for Mix: e.g., "1, 2, 3")
```

**Processing:**
- Store selected format(s)
- If podcast selected, ask Question 3
- If other format, ask modified Question 3 (about size, not duration)
- Proceed based on format

---

## Question 3: Format-Specific Details

### If Podcast:
```
What's your target podcast duration per episode?

A. Short (10-15 minutes) — snackable content
B. Medium (25-35 minutes) — single commute/workout
C. Long (40-60 minutes) — deep dive
D. Very Long (60+ minutes) — expert level

Choose A, B, C, or D
```

### If Slides:
```
How many slides do you want total?

A. Concise (10-20 slides) — quick overview
B. Moderate (20-40 slides) — standard presentation
C. Detailed (40-60 slides) — comprehensive
D. Very detailed (60+ slides) — thorough coverage

Choose A, B, C, or D (or estimate based on course length)
```

### If Study Guide:
```
How detailed should the study guide be?

A. Concise (5-10 pages) — key points only
B. Moderate (10-20 pages) — balanced coverage
C. Detailed (20-40 pages) — comprehensive
D. Very detailed (40+ pages) — exhaustive

Choose A, B, C, or D
```

### If Flashcards:
```
How many flashcards do you want?

A. Concise (20-40 cards) — key terms only
B. Moderate (40-80 cards) — solid coverage
C. Comprehensive (80-150 cards) — all important points
D. Exhaustive (150+ cards) — every detail

Choose A, B, C, or D
```

### If Video:
```
Total video duration target?

A. Short (10-15 min total) — key concepts only
B. Moderate (30-60 min total) — balanced
C. Detailed (60+ min total) — comprehensive

Choose A, B, or C
```

### If Mix:
```
For your mixed format output, specify duration/size for each:
- Podcasts: duration preference (Short/Medium/Long)?
- Slides: how many slides?
- Study Guides: how detailed?
- Flashcards: how many cards?
- Videos: total duration?

(You can answer just the formats you selected)
```

---

## Question 4: Target Audience / Education Level

**Ask:**
```
What's your target audience?

This affects explanation depth, complexity, and examples.

A. Primary school (ages 6-11)
B. Secondary school (ages 12-17)
C. Undergraduate students
D. Master's / Advanced students
E. Professionals
F. General public (no specific background)
G. Other (please describe)

Choose A-G
```

**Processing:**
- Store audience level
- Use this to guide explanation depth in instructions
- Adjust examples to match audience experience

---

## Question 5: Specific Content to Prioritize

**Ask:**
```
Do you want to cover the entire course or focus on specific content?

A. Cover the entire course
B. Focus on specific chapters (list them)
C. Focus on key themes (describe them)
D. Skip certain sections (which ones?)

Choose A-D
```

**Processing:**
- If A: Analyze entire course
- If B: Ask for chapter names/numbers, analyze those
- If C: Ask for theme descriptions, analyze related sections
- If D: Ask which sections to skip

---

## Question 6: Conversational Style

**Ask:**
```
What conversational style do you prefer?

A. Academic (formal, technical, precise language)
B. Natural (friendly, conversational, accessible)
C. Debate (discussion-based, showing multiple perspectives)
D. Socratic (question-led, helping reader discover answers)

Choose A-D
```

**Processing:**
- Store style preference
- Pass to instruction generator to guide tone

---

## Question 7: Any Special Requirements?

**Ask:**
```
Any special requirements or notes?

Examples:
- "Include lots of real-world examples"
- "Focus on practical applications"
- "Emphasize this concept: X"
- "This is for beginners, go slow"
- "Target audience has background in Y"
- "Keep it concise and direct"
- (or just press Enter to skip)

Type your notes (or press Enter if none)
```

**Processing:**
- Store any special notes
- Pass to analyzer and generator to keep in mind
- Adapt instructions based on notes

---

## Question 8: Confirm & Ready to Analyze

**Ask:**
```
Great! I have all the information I need.

Summary:
- Course: [file/URL/text received]
- Format: [selected format(s)]
- Target audience: [audience level]
- Conversational style: [style]
- Any special notes: [notes if provided]

Ready to analyze your course and generate content?
(This may take a minute or two depending on course length)

Y/N?
```

**Processing:**
- If N: Loop back to allow edits
- If Y: Proceed to analysis phase

---

## Notes for Claude Implementation

### Conversational Tone
- Be friendly and encouraging
- Use clear, simple language
- Explain why each question matters
- Offer suggestions if user seems unsure

### Flexibility
- Allow shortcuts (e.g., "I want podcast, 30 min, Master level, natural style")
- If user is confused, offer examples
- Can adjust questions based on answers
- Don't be rigid - adapt to conversational flow

### Validation
- Check file uploads are valid courses (not images, corrupted, etc.)
- Warn if file is very large (>50MB) or very short (<5 pages)
- Confirm URL is accessible before proceeding
- Suggest format if user is unsure

### Default Values
If user skips a question or says "whatever":
- Format: Podcast
- Duration: Medium (25-35 min)
- Audience: Master's level
- Style: Natural
- Content: Entire course
- Special: None

---

**Next Step:** Once questionnaire complete, proceed to `analyzer.md`

**Current Status**: Specification (ready for implementation)
