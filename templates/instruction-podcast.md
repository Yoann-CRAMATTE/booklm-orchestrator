# Instruction Template: Podcast Format

## Template Structure

```markdown
## PODCAST #{segment_number}: {segment_title}

**Duration Target**: {duration} minutes
**Chapters Covered**: {chapters} (pages {page_range})
**Audience**: {audience_level}

**Key Concepts to Cover (in order of importance)**:
1. {concept_1} - {brief_description}
2. {concept_2} - {brief_description}
3. {concept_3} - {brief_description}

**Points to Explain Well**:
- {explanation_point_1}
- {explanation_point_2}
- {explanation_point_3}

**Common Misunderstandings to Address**:
- Clarify: {misconception_1} vs {correct_understanding_1}
- Clarify: {misconception_2} vs {correct_understanding_2}

**Real-World Examples to Include**:
- {example_1}
- {example_2}

**Conversational Style**: {style} (academic / natural / debate / socratic)
**Explanation Depth**: {depth} (concise / medium / detailed)
**Tone & Emphasis**:
- {emphasis_point_1}
- {emphasis_point_2}

---

## COPY-PASTE SECTION FOR BOOKLM

**IMPORTANT**: The text below follows strict audio synthesis rules (see "Audio Synthesis Constraints" above). BookLM will convert this to speech — every abbreviation spelled out, every number written as words, zero markdown formatting. This ensures clean, professional audio output.

---

Focus on {chapters}. Cover these concepts in order:

1. **{concept_1}**: {what_to_explain}
2. **{concept_2}**: {what_to_explain}
3. **{concept_3}**: {what_to_explain}

Make sure to explain:
- {explanation_need_1}
- {explanation_need_2}
- {explanation_need_3}

Address these common confusions:
- {misconception_1}
- {misconception_2}

Include these examples:
- {example_1}
- {example_2}

**Style**: {conversational_style}, with real-world examples and practical applications.

**Target Duration**: {duration} minutes

**Audience**: {audience_description}

---
```

## Example (Filled)

```markdown
## PODCAST #1: Fundamentals of Decentralization

**Duration Target**: 35 minutes
**Chapters Covered**: Chapters 1-2 (pages 12-45)
**Audience**: Master's students in Public Administration

**Key Concepts to Cover (in order of importance)**:
1. Decentralization - Transfer of powers from central government to lower levels
2. Three levels of territorial collectivities - Communes, departments, regions
3. Subsidiarity principle - Authority should be at the lowest appropriate level

**Points to Explain Well**:
- Clearly explain the difference between deconcentration and decentralization
- Provide concrete examples of each level's competencies
- Discuss financial mechanisms (grants, own resources)

**Common Misunderstandings to Address**:
- Clarify: Deconcentration (administrative delegation) vs Decentralization (transfer of power)
- Clarify: Subsidiarity (principle) vs Federalism (structure)

**Real-World Examples to Include**:
- How education responsibilities are shared across levels in France
- Waste management as example of multi-level governance
- Budget allocation between Paris and regional governments

**Conversational Style**: Natural, friendly
**Explanation Depth**: Medium (assume some political science background)
**Tone & Emphasis**:
- Emphasize differences between governance levels
- Highlight current tensions in French decentralization
- Make it relevant to Master's students' future careers

---

## COPY-PASTE SECTION FOR BOOKLM

Focus on chapters one through two. These cover French administrative structure.

Cover these concepts in this order:

One. Decentralization and Its History. Explain what decentralization means. Show how it evolved in France. Describe the movement from centralization toward distributed authority.

Two. Three Levels of Collectivities. Describe communes at the local level. Describe departments at the mid-level. Describe regions for large areas. Give specific powers for each level.

Three. Subsidiarity Principle. Explain that governance should happen at the closest possible level to citizens. It must still be effective. This is the core principle.

Make sure to explain these points clearly:

First, how deconcentration differs from decentralization. This is a very common confusion. Be explicit about the difference.

Second, specific examples. Which level handles education? Which handles roads? Which handles social services?

Third, the financial system. How does money flow between levels? How do regions fund themselves?

Address these common confusions:

Deconcentration is not the same as decentralization. They mean very different things.

Decentralization is not the same as independence. The levels still work together.

Include these real-world examples:

How a local school district works across the commune, department, and region levels.

How waste management coordination happens between governance levels.

How regional development funds get allocated.

Style: Natural, conversational tone. Use practical examples drawn from French administration.

Target duration: thirty five minutes.

Audience: Master's level students studying public administration. They are preparing for careers in local or regional government.

---
```

## Guidelines for Podcasts

### Structure
- **Opening** (1-2 min): Hook, introduce topic, roadmap
- **Body** (30-32 min): Concepts in order, examples woven throughout
- **Closing** (1-2 min): Recap, next steps, transition to next podcast

### Language
- ✅ Conversational, natural speech patterns
- ✅ Short sentences (15-20 words max)
- ✅ Explain jargon inline
- ✅ Use transitions ("Now that we've covered X...")

### Audio Optimization (CRITICAL FOR BOOKLM AUDIO QUALITY)

**⚠️ AUDIO SYNTHESIS CONSTRAINTS — FOLLOW STRICTLY**

These rules prevent BookLM's text-to-speech from generating artifacts, mispronunciations, or audio noise:

**Rule 1: Spell out ALL abbreviations**
- ❌ ONU, UNESCO, PDG, etc.
- ✅ Organisation des Nations Unies, Organisation des Nations Unies pour l'Éducation...
- Why: TTS cannot pronounce acronyms naturally; spells each letter → unnatural

**Rule 2: Write complex numbers, dates, and technical terms as words**
- ❌ 12/31/2026, €2.5M, Article 42.3
- ✅ December 31, 2026; two point five million euros; Article forty-two, point three
- Why: Numbers and special formats cause TTS to stumble or read numbers digit-by-digit

**Rule 3: ZERO Markdown formatting in final text**
- ❌ No asterisks (*), hyphens (—), hashes (#), brackets [text], backticks `code`
- ✅ Plain text only, use parentheses (like this) for emphasis
- Why: Markdown characters cause audio artifacts and noise in BookLM TTS

**Rule 4: Keep sentences SHORT — Maximum 20 words each**
- ❌ "The principle of subsidiarity, which states that governance should happen at the lowest appropriate level while still being effective, is fundamental."
- ✅ "Governance should happen at the lowest appropriate level. This is called subsidiarity. It's fundamental to modern administration."
- Why: Long sentences = rushed speech or phrasing errors in TTS

**Legacy Tips**:
- Use "for example" not "e.g."
- Use "and so on" not "etc."
- Use connectors: "First... Second... Third..." not bullet lists

### Examples
- Minimum 2-3 per podcast
- Real-world, relatable
- Support concept explanation
- Help listener remember

### Emphasis
- 1-2 key takeaways per podcast
- State explicitly ("This is crucial..." / "Remember this...")
- Repeat in different contexts
- Connect to audience's goals

---

**Template Version**: 1.0  
**Last Updated**: June 2026
