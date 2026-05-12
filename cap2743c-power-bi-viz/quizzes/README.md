# Quizzes

QTI (Question and Test Interoperability) zip files for direct import into Canvas. These are instructor-facing — students never see this folder; they take the quizzes inside Canvas.

## Quizzes in this course

| File | When | Covers | Points |
|---|---|---|---|
| `Quiz01_Foundations.qti.zip` | Session 3 | Ch 1 (model-to-message) + Ch 2 pt 1 (basic visuals) | 10 |
| `Quiz02_FormatInteract.qti.zip` | Session 6 | Ch 3 (formatting + accessibility) + Ch 4 pt 1 (filters, slicers) | 10 |
| `Quiz03_AnalyticsAI.qti.zip` | Session 9 | Ch 5 (analytics, visual calcs, Smart Narrative) + Ch 6 (AI visuals, Copilot) | 10 |
| `Quiz04_DistributeGovern.qti.zip` | Session 11 | Ch 7 (distribution, mobile) + Ch 8 (workspaces, RLS) | 10 |

## How to import into Canvas

1. In Canvas, navigate to the course → **Settings** → **Import Course Content**
2. Content type: **QTI .zip file**
3. Source: upload the appropriate `Quiz##_*.qti.zip` from this folder
4. **Question bank**: leave default or select an existing bank
5. Click **Import**
6. After import, edit the imported quiz to set:
   - **Attempts allowed:** 3
   - **Time limit:** none (untimed)
   - **Quiz type:** Graded Quiz
   - **Show correct answers:** After each attempt
   - **Score to keep:** Highest

## Quiz format standards

All quizzes follow the same pattern (consistent with the prereq course):

- 5 questions per quiz, 2 points each
- Multiple choice + short answer mix
- 1 ungraded confidence check at the end ("How confident do you feel about this topic?")
- Immediate feedback on every question — not just right/wrong, but a 1-sentence explanation
- No trick questions, no "all of the above," no "which of the following is NOT"
- Retakable, untimed, highest score kept

## Authoring notes

QTI files are generated using the same workflow as CAP2791C. Source `.txt` files for each quiz (with questions, options, correct answers, and feedback) are kept in `instructor/quiz-source/` and converted to QTI before import.
