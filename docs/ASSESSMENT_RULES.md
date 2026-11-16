# Assessment and scoring rules

## Question contract
Each question stores: type, prompt, options (when applicable), answer key, explanation, marks, negative marks, difficulty, topic IDs, source/provenance, review status and version.

## Attempt lifecycle
`created → in_progress → submitted → evaluated`
- Start time and deadline are server-generated.
- Answers are persisted incrementally.
- Submission is idempotent.
- Expired attempts follow a documented auto-submit policy.
- Submitted attempts are immutable; corrections create a new version/re-evaluation record.

## MCQ scoring
For each question:
- Correct: add configured marks.
- Incorrect: subtract configured negative marks.
- Unanswered: zero unless the exam configuration explicitly says otherwise.
- Total is calculated by deterministic backend code using decimal-safe arithmetic.

## Testing
Cover positive marks, negative marks, unanswered questions, multiple sections, partial submissions, repeated submission, expiry and rounding.
