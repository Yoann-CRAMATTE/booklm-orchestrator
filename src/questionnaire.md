# Questionnaire Logic

This file describes the interactive questionnaire Claude should execute when skill is launched.

## CRITICAL: Language Detection First

**BEFORE ANY QUESTIONS:**

Claude must detect user's native/working language:

1. **Analyze first interaction**:
   - What language did user use to invoke skill? (e.g., `/booklm-orchestrator`)
   - What language are they typing in?
   - French? English? Russian? Chinese? Spanish? German? Italian? Other?

2. **Store language choice**:
   ```
   user_language = [detected from interaction]
   If unclear → Ask: "Quelle langue préfères-tu? / What language do you prefer?"
   ```

3. **ALL subsequent interactions in user's language**:
   - Questions → User's language
   - Explanations → User's language
   - Output document → User's language
   - Concept names → Keep technical terms, explain in user's language

---

## Flow: Questions to Ask User

**Welcome message (IN USER'S LANGUAGE):**

**Example French:**
```
Bienvenue dans BookLM-Orchestrator!

Je vais vous aider à transformer votre cours en contenu pédagogique structuré 
prêt pour BookLM (ou tout autre générateur basé sur IA).

Commençons par rassembler les informations sur votre cours et vos objectifs.
```

**Example English:**
```
Welcome to BookLM-Orchestrator!

I'll help you transform your course into structured educational content 
ready for BookLM (or any LLM-based content generator).

Let's start by gathering some information about your course and goals.
```

**[Repeat for other languages as needed]**

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

**Ask (IN USER'S LANGUAGE):**

**French example:**
```
Quel format de sortie souhaitez-vous?

1. Podcast (conversationnel, épisodes chronométrés)
2. Slides (visuel, format présentation)
3. Guide d'étude (Q&R, explications détaillées)
4. Flashcards (mémoire, paires Q&R)
5. Vidéo (script + descriptions visuelles)
6. Mix (plusieurs formats à la fois)

Choisissez 1-6 (ou plusieurs pour Mix: ex. "1, 2, 3")
```

**English example:**
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
- **Go directly to Question 3** (FORMAT-SPECIFIC QUANTIFICATION)
- Proceed based on format choice

---

## Question 3: Format-Specific Quantification

**CRITICAL**: Ask for EXACT number, not ranges. Adapt language to user.

### If Podcast:

**Ask (IN USER'S LANGUAGE):**

French:
```
Combien de minutes par épisode de podcast?
(Exemple: 30, 45, 60, 90 minutes?)

Ton nombre exact:
```

English:
```
How many minutes per podcast episode?
(Example: 30, 45, 60, 90 minutes?)

Your exact number:
```

**Processing**: User provides number (e.g., "60") → Store: podcast_duration = 60 min

---

### If Slides:

**Ask (IN USER'S LANGUAGE):**

French:
```
Combien de slides au total?
(Exemple: 15, 25, 50 slides?)

Ton nombre exact:
```

English:
```
How many slides total?
(Example: 15, 25, 50 slides?)

Your exact number:
```

**Processing**: User provides number (e.g., "30") → Store: slides_total = 30

---

### If Study Guide:

**Ask (IN USER'S LANGUAGE):**

French:
```
Combien de pages au total?
(Exemple: 10, 20, 40 pages?)

Ton nombre exact:
```

English:
```
How many pages total?
(Example: 10, 20, 40 pages?)

Your exact number:
```

**Processing**: User provides number (e.g., "25") → Store: guide_pages = 25

---

### If Flashcards:

**Ask (IN USER'S LANGUAGE):**

French:
```
Combien de flashcards au total?
(Exemple: 50, 100, 150 cartes?)

Ton nombre exact:
```

English:
```
How many flashcards total?
(Example: 50, 100, 150 cards?)

Your exact number:
```

**Processing**: User provides number (e.g., "80") → Store: flashcards_total = 80

---

### If Video:

**Ask (IN USER'S LANGUAGE):**

French:
```
Combien de minutes de vidéo au total?
(Exemple: 15, 30, 60 minutes?)

Ton nombre exact:
```

English:
```
How many minutes of video total?
(Example: 15, 30, 60 minutes?)

Your exact number:
```

**Processing**: User provides number (e.g., "45") → Store: video_duration = 45 min

---

### If Mix (multiple formats):

**Ask (IN USER'S LANGUAGE):**

French:
```
Pour chaque format choisi, donne ton nombre exact:
- Podcasts: combien de minutes par épisode?
- Slides: combien de slides?
- Guides: combien de pages?
- Flashcards: combien de cartes?
- Vidéos: combien de minutes total?

(Réponds juste pour les formats sélectionnés)
```

English:
```
For each selected format, give your exact number:
- Podcasts: how many minutes per episode?
- Slides: how many slides?
- Guides: how many pages?
- Flashcards: how many cards?
- Videos: how many minutes total?

(Answer only for selected formats)
```

**Processing**: Store each value separately for multi-format generation

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
