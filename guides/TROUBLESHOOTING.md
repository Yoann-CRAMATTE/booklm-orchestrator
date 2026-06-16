# Troubleshooting Guide

## File Upload Issues

### Error: "File format not supported"

**Cause**: File extension not recognized or file is corrupt.

**Solutions**:
1. ✅ Verify file format:
   - Supported: `.pdf`, `.docx`, `.txt`
   - Check actual extension (not just what shows in explorer)
   
2. ✅ Convert if needed:
   - PDF → Use online converter to DOCX if PDF is image-based
   - DOCX → If corrupt, try exporting as PDF from original source
   - TXT → Ensure plain text encoding (UTF-8, not binary)

3. ✅ Test file:
   - Try opening file with its application first
   - If it won't open, file is likely corrupt
   - Recreate or request fresh copy

### Error: "File size exceeds 50 MB"

**Solutions**:
1. ✅ Split large course:
   - Divide into 2-3 parts (50 MB each)
   - Process separately
   - Merge results manually

2. ✅ Compress document:
   - Remove images if unnecessary
   - Use more compression in PDF export
   - Remove appendices if not essential

3. ✅ Extract relevant sections:
   - Use PDF editor to extract only needed chapters
   - Remove blank pages, duplicate content

### Error: "URL not accessible"

**Solutions**:
1. ✅ Verify URL:
   - Copy-paste directly from browser address bar
   - Ensure full URL (includes https://)
   - Check URL is publicly accessible

2. ✅ Access issues:
   - Website may be blocking automated access
   - Try downloading file directly instead
   - Check if login required

3. ✅ Alternative:
   - Download document locally
   - Upload as file instead of URL

---

## Analysis Issues

### Problem: "Analysis timed out"

**Cause**: Course too large or complex analysis.

**Solutions**:
1. ✅ Reduce course scope:
   - Split into smaller parts
   - Remove non-essential sections
   - Process chapters separately

2. ✅ Simplify analysis:
   - Choose "Balanced" granularity instead of "Fine"
   - Select specific chapters instead of "everything"
   - Try "Coarse" granularity

3. ✅ Try again:
   - Server may have been busy
   - Sometimes retry succeeds

### Problem: "No chapters detected"

**Cause**: Course has unclear structure or unusual formatting.

**Solutions**:
1. ✅ Verify structure:
   - Course should have clear chapter headings
   - Sections should be marked (not just text runs)
   - Check table of contents is present

2. ✅ Manually mark structure:
   - Edit document to add clear headings
   - Use heading styles consistently
   - Re-upload revised version

3. ✅ Convert format:
   - Try different source format
   - Word → PDF or vice versa
   - Sometimes format conversion helps

### Problem: "Concepts seem irrelevant"

**Cause**: Course language unclear or formatting broken.

**Solutions**:
1. ✅ Verify course quality:
   - Is course material actually coherent?
   - Are there definitions and context?
   - Check for OCR errors (if scanned PDF)

2. ✅ Fix OCR issues:
   - Use PDF OCR tool to re-process
   - Scanned PDFs often have errors
   - Better quality source = better results

3. ✅ Provide more context:
   - Add manual course description
   - Specify key concepts you want included
   - Use "expert mode" to guide analysis

---

## Segmentation Issues

### Problem: "Segments too long (or too short)"

**Cause**: Duration targets don't match course material.

**Solutions**:
1. ✅ Adjust granularity:
   - Fine: More segments, shorter each (10-20 min)
   - Balanced: Medium (25-35 min) ← recommended
   - Coarse: Fewer segments, longer each (40-60 min)

2. ✅ Adjust podcast duration:
   - If chose 60+ min, segments will be longer
   - Switch to 25-35 min for standard length
   - 10-15 min for snackable content

3. ✅ Course mismatch:
   - 50-page course naturally segments differently than 200-page
   - Very short courses can't be split much
   - Very long courses may need multi-segment planning

### Problem: "Segment boundaries seem wrong"

**Cause**: Automatic segmentation may not respect your expectations.

**Solutions**:
1. ✅ Specify priorities:
   - In Q4, select specific chapters to emphasize
   - This guides segmentation better
   - More focused = better boundaries

2. ✅ Review logic:
   - Skill tries to respect chapter boundaries
   - Keeps concepts together
   - May split chapters if pedagogically warranted

3. ✅ Manual adjustment:
   - In expert mode, manually adjust boundaries
   - Use tool to recalculate after adjustment
   - Preview before accepting

### Problem: "Key concepts missing from segment"

**Cause**: Concept wasn't recognized as important.

**Solutions**:
1. ✅ Verify in source:
   - Check concept is actually in chapter
   - Ensure it's clearly marked/defined
   - Not hidden in example or appendix

2. ✅ Boost visibility:
   - In questions, mention concept explicitly
   - Use expert mode to mark as "must include"
   - Rerun analysis

3. ✅ Manual addition:
   - Edit output to add concept
   - Update BookLM instruction block accordingly
   - Note change for future reference

---

## Instruction Output Issues

### Problem: "BookLM prompt is too long"

**Cause**: Instruction block exceeds comfortable copy-paste size.

**Solutions**:
1. ✅ Split segment:
   - Use editor to break into 2 smaller blocks
   - Create separate BookLM podcasts
   - Combine similar segments

2. ✅ Shorten instruction:
   - Remove redundant points
   - Keep only essential concepts
   - Remove examples, keep core content

3. ✅ Paste incrementally:
   - Copy to text editor first
   - Paste in chunks to BookLM
   - Or upload as document to BookLM

### Problem: "Style doesn't match my expectations"

**Cause**: Conversational style chosen doesn't fit.

**Solutions**:
1. ✅ Try different style:
   - Natural (friendly) - most versatile
   - Academic (formal) - technical topics
   - Socratic (questioning) - teaching/learning
   - Debate (discussion) - controversial topics

2. ✅ Edit instruction:
   - Manually adjust tone in editor
   - Add conversational phrases
   - Or remove them for more formal tone

3. ✅ Provide guidance:
   - In expert mode, specify style preferences
   - Add style examples
   - Rerun analysis

### Problem: "Output is too technical / too simple"

**Cause**: Audience level mismatch.

**Solutions**:
1. ✅ Adjust audience:
   - Choose more accurate level
   - Undergrad = simpler explanations
   - Master's/Pro = assume knowledge
   - General public = maximum context

2. ✅ Re-generate:
   - New audience selection triggers different output
   - Concepts may shift priority
   - Examples may change

3. ✅ Manual adjustment:
   - Edit explanation level in output
   - Add/remove technical terms as needed
   - Adjust examples to suit audience

---

## BookLM-Specific Issues

### Problem: "BookLM says instruction is unclear"

**Cause**: Prompt could be clearer or more specific.

**Solutions**:
1. ✅ Clarify in BookLM directly:
   - Edit custom instruction manually
   - Add specific examples
   - Be more explicit about desired style

2. ✅ Simplify instruction:
   - Remove jargon
   - Use shorter sentences
   - Break into numbered list

3. ✅ Regenerate from skill:
   - Try different parameters
   - Use more specific audience
   - Adjust style/granularity

### Problem: "Generated podcast quality is poor"

**Cause**: Several possibilities - instruction, content, or BookLM.

**Solutions**:
1. ✅ Check instruction:
   - Does it clearly state what you want?
   - Are key concepts explicit?
   - Is duration reasonable?

2. ✅ Try different approach:
   - Different conversational style
   - More detailed or concise instruction
   - Try different podcast duration

3. ✅ Provide examples:
   - Give BookLM examples of good podcast style
   - Reference existing podcasts
   - Specify exact tone desired

4. ✅ Iterate:
   - Generate multiple versions
   - Pick best one
   - Use as base for next iteration

---

## Performance Issues

### Problem: "Skill is slow / timing out"

**Cause**: Server load, large file, or complex analysis.

**Solutions**:
1. ✅ Retry:
   - Wait a moment
   - Try again
   - May succeed on second attempt

2. ✅ Reduce complexity:
   - Use "Balanced" granularity
   - Select specific chapters instead of all
   - Reduce course size

3. ✅ Contact support:
   - If consistent timeouts
   - Skill may need optimization
   - Report with file size and parameters

### Problem: "Memory error / crash"

**Cause**: Very large file or system resource issue.

**Solutions**:
1. ✅ Restart & retry:
   - Close other applications
   - Restart Claude Code if needed
   - Retry with same file

2. ✅ Reduce file size:
   - Split course into parts
   - Remove images or appendices
   - Convert to more efficient format

3. ✅ Upgrade resources:
   - If consistent, may need more system RAM
   - Try on different machine
   - Contact support

---

## Language & Localization Issues

### Problem: "French/English mixed or incorrect"

**Cause**: Language detection or mixing.

**Solutions**:
1. ✅ Verify source language:
   - Is course actually in specified language?
   - Mixed-language documents may confuse
   - Use pure language if possible

2. ✅ Specify language explicitly:
   - In questions, explicitly state language
   - Don't rely on auto-detection
   - Rerun with explicit setting

3. ✅ Report issue:
   - If language detected incorrectly, note it
   - Helps improve language detection
   - Include example

---

## Getting More Help

### Check These First
1. [GETTING_STARTED.md](./GETTING_STARTED.md) - Basic workflow
2. [BEST_PRACTICES.md](./BEST_PRACTICES.md) - Optimization tips
3. [README.md](../README.md) - Feature overview

### Report Issues
- **GitHub Issues**: Open issue with:
  - Error message (exact text)
  - Course size/language
  - Parameters used
  - Expected vs actual result

### Share Feedback
- What worked well?
- What could improve?
- What surprised you?
- Your suggestions welcome!

---

**Last Updated**: June 2026  
**FAQ & Known Issues coming in Phase 2**
