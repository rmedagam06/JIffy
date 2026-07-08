# IB Biology Question Dataset (2025 syllabus, first assessment 2025)

Question bank powering the Jiffy scrolling drill cards, adapted to IB Biology.
Questions are organized **per subtopic** so a student can pick a single topic to study.

## Structure

```
dataset/
  index.json            # manifest: all themes/subtopics, level, question counts, file paths
  theme-a/
    A1.1-water.json
    A1.2-nucleic-acids.json
    ...
  theme-b/ ...
  theme-c/ ...
  theme-d/ ...
```

Phasing: **Theme A is authored first** (all 9 subtopics). Themes B, C, D follow.

## Level tagging

IB tags content two ways, both captured here:

- **Whole subtopic** – some subtopics are HL-only (e.g. A2.1, A2.3, A3.2). The
  subtopic object's `level` is `"HL"`; otherwise `"SL/HL"`.
- **Per content statement** – inside an SL/HL subtopic, statements from the
  "Additional higher level" section produce questions tagged `"level": "HL"`.
  SL students see only `"SL"` questions; HL students see both.

## Subtopic file schema

```jsonc
{
  "id": "A1.1",
  "name": "Water",
  "theme": "A",
  "themeName": "Unity and diversity",
  "levelOfOrganization": "Molecules",
  "level": "SL/HL",              // or "HL" for HL-only subtopics
  "questions": [
    {
      "id": "A1.1-001",
      "level": "SL",             // "SL" or "HL"  (which cohort should see it)
      "statement": "A1.1.2",     // source syllabus content statement
      "category": "A1.1 Water",  // chip text shown on the card
      "scenario": "",            // optional context/stem-setter (may be "")
      "stem": "Why is water described as a polar molecule?",
      "options": [
        { "letter": "A", "text": "...", "correct": false },
        { "letter": "B", "text": "...", "correct": true  },
        { "letter": "C", "text": "...", "correct": false },
        { "letter": "D", "text": "...", "correct": false }
      ],
      "explanation": "One-sentence why, shown on reveal."
    }
  ]
}
```

Card field mapping: `category` → chip, `scenario` → context line, `stem` →
question, `options[]` → answer rows (`correct:true` is the right one),
`explanation` → the reveal bubble.

Exactly one option per question has `"correct": true`.
