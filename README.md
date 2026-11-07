# Spelling Champion

A 30-week spelling practice app for kids, built as the sister app of Root Detective. It has the same design, fonts, components and progress system. It is one `index.html` with no build step and works offline. The voice can play recorded MP3s from `audio/`.

## Pages
- **Home**: greeting from the trophy mascot, pills for 🔥 days in a row, ⭐ words mastered, 🏅 badges and 🔓 week reached, then one **Next up** card that follows the week's plan. Below that are this week's words (tap one to hear it) and the Practice tiles.
- **Plan**: the Monday–Friday plan for the current week, with check marks, and all 30 weeks along a winding road. Tap a week to make it your week, open its flashcards or take its final test.
- **Flashcards**: Root Detective's card. It has position dots, a 3D flip, swipe (the card and its Listen button move together), Back / Flip / Next, "I know this", Shuffle and "Next to flip". The front shows the word. The back shows the spelling pattern, the meaning, the sentence, the Chinese and Korean meanings and the letters.
- **Daily review**: a 10-question quiz on the words due today (missed, weak or not practised lately), plus the list of every missed word with a "Practice these words" round.
- **Activities**: Spell it, Build it, Rhyme time, Sound sort, ABC order, Proofread (10 passages a week, each with 6 misspellings; every passage comes up once before any repeats).
- **Games**: Quiz (hear the word or read the sentence, then pick the right spelling), Meanings (read a meaning and pick the word, see a word and pick its meaning, or pick the word that fits a sentence; the Chinese and Korean can be shown as a hint), Match (word ↔ meaning), Memory (word ↔ rhyme or simple definition) and Speed round (60 seconds of "Is this spelled right?").
- **Tests**: the Pretest and the Final test for the current week.
- **Progress**: name, streak, stats, passes per activity this week, tests by week, words that need work, 42 badges and a day-by-day history.

Header: Sound on/off and Display options (text size, easier reading, calm mode, read-aloud buttons).

## Rules
- **Weeks unlock in order.** Week N+1 opens when week N's **Final test is passed with 80%** (20 of 25 for week 1). The pretest doesn't count.
- **Each new week opens in steps** (a week that's already passed, or has no words yet, is fully open):
  1. **Pretest.** Until it's taken, only Home, Plan, Tests and Progress are open. It doesn't count toward passing.
  2. **Flashcards.** Then only the flashcards open; each card counts once both of its sides have been seen.
  3. **Required activities.** Then only Spell it, Build it, Rhyme time, Sound sort, ABC order and Proofread open (plus the flashcards). Each must be **passed 3 times** with that week's words.
  4. **Final test.** It opens once all six are done, and so does everything else (Quiz, Meanings, Match, Memory, Speed round).
- **Daily review** is open at every step, once a day: after today's review it says to come back tomorrow.
- Locked tabs and tiles show a lock badge; opening one explains what to do first.
- Each activity sticks to the current week until it has been passed 3 times with that week's words, then goes back to all weeks. A note above the activity shows the count.
- Spell it, Build it and Proofread show the answer after 3 wrong tries.
- Pass marks: Spell it 8/10, Build it 6/8, Quiz 8/10, Rhyme time and Sound sort 80%, ABC order 2 of 3 sets, Proofread 5 of 6, Match 2 misses or fewer, Memory 12 turns or fewer, Speed round 10 right.
- A word is **mastered** after 3 or more first-try correct answers with 80% or better accuracy.
- Weeks without words show as "coming soon" everywhere. The activities keep using the earlier weeks.

## Adding a week
Fill in the week's entry in `WEEK_DATA` near the top of the script in `index.html`. The comment above it explains the format. Only `words` is required. Rhyme time, Sound sort and Proofread appear for a week once its `rhymes`, `sort` or `proof` is filled in. Misspellings written in a `proof` passage are also used as Quiz and Speed round options.

## Voice and recorded audio
All speech goes through Root Detective's `SPEAK` module, copied unchanged. A line plays from `audio/<key>.mp3` only if every piece of it is listed in `audio/index.json`. Otherwise the device voice reads it. A word's `say` field changes what the voice says, both alone and inside its sentence.

To make recordings, open the app and run `ALL_LINES()` in the browser console. It returns `[text, kind]` for every text the app can speak. `kind` is `word` (one word said alone), `sent` (a sentence) or `other` (dictation, test lines, card backs, rhyme feedback). For each text, take `SPEAK.chunks(text)`, then save each chunk as `audio/${SPEAK.key(chunk)}.mp3` and add the key to `keys` in `audio/index.json`. `audio/silence.mp3` unlocks sound on iPad and iPhone.

## Saving progress
Progress is saved in this browser on this device, in `localStorage`:
- `sc-history`: name and one record per day
- `sc-state`: current week, known words, missed words
- display, sound and badge keys

Progress from the first version (`spellingchampion_v1`) is brought over automatically the first time the new version opens.

## Credits
- Font: URW Gothic © 2013–2015 (URW)++ Design & Development, used under the SIL Open Font License 1.1.
- Design, components and the voice module come from Root Detective.
