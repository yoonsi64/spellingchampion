# Spelling Champion

A 30-week spelling practice app, built like Root Detective: one `index.html`, no build step.

## Pages
- **Home**: this week's word box, what's up next, quick practice tiles
- **Plan**: Monday–Friday plan for the current week, and all 30 weeks (tap one to make it current)
- **Cards**: flashcards with position dots, flip, known, shuffle and "Next to flip"
- **Practice**: Spell it, Build it, Rhyme time, Sound sort, ABC order, Proofread, plus the Pretest and Final test
- **Progress**: passes per activity, best test score per week
- **Review**: every word missed in any activity, with a practice round

## Rules
- Before a week's flashcards are all flipped, activities use all weeks.
- After that, each activity sticks to the current week until it has been passed 3 times, then goes back to all weeks. The tiles say "Week N only" while the limit is on.
- Spell it, Build it and Proofread show the answer after 3 wrong tries.

## Adding a week
Fill in the week's entry in `WEEK_DATA` near the top of the script in `index.html`. The format is explained in the comment above it. Only `words` is required; Rhyme time, Sound sort and Proofread appear for a week once its `rhymes`, `sort` or `proof` is filled in.

## Voice
Uses the browser's built-in voice. Recorded MP3s can be added later in `audio/` with an `audio/index.json` that maps each sentence to a file, the same way Root Detective does.
