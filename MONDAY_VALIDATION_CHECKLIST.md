# Lundi-Mardi: Quick Validation Sprint

**Objective**: Test Phase 1 MVP empirically. 4-5 hours total. Decision: Phase 2 go/partial/fail.

---

## LUNDI MATIN (~ 1 hour)

### BookLM Real Test — BLOC #1

**Setup (5 min)**:
- [ ] Open NotebookLM.google.com
- [ ] Sign in

**Test (20 min)**:
- [ ] Create new notebook
- [ ] Name: "BookLM-Orchestrator Test — Droit Décentralisation"
- [ ] Upload/paste: Full course "Droit de la Décentralisation"
- [ ] Wait for upload complete

**Generate (30 min)**:
- [ ] Click "Create" → "Podcast"
- [ ] Click "Custom Instructions"
- [ ] Copy ENTIRE bloc_1_audio_optimized.txt section
- [ ] Paste into Custom Instructions field
- [ ] Click "Generate"
- [ ] WAIT for BookLM to process (~2-5 min)

**Evaluate**:
- [ ] Audio generated? (Yes/No/Partial)
- [ ] Audio quality acceptable? (Listen 2-3 min)
- [ ] Matches instruction? (follows structure/concepts?)
- [ ] TTS optimization worked? (no artifacts, clear speech?)

**Record**:
```
Outcome: [ ] SUCCESS | [ ] PARTIAL | [ ] FAILURE

Details:
- Audio quality: _______________
- Instruction adherence: _______________
- TTS issues (if any): _______________
- Next step: _______________
```

---

## LUNDI AFTERNOON (~ 2-3 hours)

### Edge Case Audit — Real Courses

**Choose 2-3 test courses** (pick from your available courses):
- Pick DIFFERENT from "Droit Décentralisation"
- Vary: structure clarity, content density, domain
- Preferably: one very structured, one less structured

**For each course:**

**Run Analyzer** (30 min per course):
- Execute analyzer on course
- Record output:
  - Concepts extracted: count
  - Structure identified: chapters/sections
  - Dependencies detected: yes/no
  - Any errors/warnings?

**Run Segmenter** (15 min per course):
- Run segmenter on analyzed course
- Assume: 60-min podcast, 10 segments
- Check:
  - Segments generated? (count)
  - Segments logical? (respect structure?)
  - Any dependency violations?

**Run Generator** (15 min per course):
- Generate bloc #1 instruction for first segment
- Check:
  - Generates without errors?
  - Output is complete text? (not truncated)
  - All templates valid?

**Record**:
```
Course 1: ________________
- Analyzer: OK / ISSUES (describe)
- Segmenter: OK / ISSUES (describe)
- Generator: OK / ISSUES (describe)

Course 2: ________________
- Analyzer: OK / ISSUES (describe)
- Segmenter: OK / ISSUES (describe)
- Generator: OK / ISSUES (describe)
```

---

## LUNDI EVENING (~ 30 min)

### Quick Assessment

**Decision Matrix**:

```
BookLM Test Result:
[ ] SUCCESS       — Bloc generates, quality acceptable
[ ] PARTIAL       — Generates but issues (audio, structure, etc.)
[ ] FAILURE       — Doesn't generate or unusable

Edge Case Result:
[ ] ALL OK        — All 2-3 courses pass analyzer/segmenter/generator
[ ] MOSTLY OK     — 1-2 courses work, edge cases found
[ ] PROBLEMS      — Multiple failures on real courses
```

**Phase 2 Go/No-Go**:

If BookLM SUCCESS + Edges MOSTLY OK:
→ **PHASE 2 GREEN-LIT** (iterate learning from real usage)

If BookLM PARTIAL + Edges MOSTLY OK:
→ **PHASE 2 CONDITIONAL** (mitigate known issues, retest, go)

If BookLM FAILURE OR Edges PROBLEMS:
→ **PHASE 2 HOLD** (debug, refactor specific issues, revalidate)

---

## APRÈS VALIDATION (Mercredi+)

**Action based on outcome**:

### If GO:
- [ ] Test blocs 2-5 in parallel with BookLM
- [ ] Validate other formats start (slides template)
- [ ] Begin Phase 2 feature planning

### If CONDITIONAL:
- [ ] Fix reported issues
- [ ] Retest bloc #1
- [ ] If successful, continue to Phase 2
- [ ] If still issues, hold and debug further

### If HOLD:
- [ ] Analyze root causes
- [ ] Targeted refactor (specific failing module)
- [ ] Retest before Phase 2 decision

---

## Key Files

**Test materials**:
- Bloc #1: `examples/bloc_1_audio_optimized.txt`
- Course: `examples/example-input-course.md` (or your real course)
- Documentation: `SPECIFICATION.md` (if need context)

**Reporting**:
- Save results above
- Update memory ProjectStatus.md
- Commit any test outputs (if useful)

---

**Duration**: ~4.5 hours  
**Goal**: Real data for Phase 2 decision  
**Outcome**: Go/Partial/Hold decision by Tuesday evening
