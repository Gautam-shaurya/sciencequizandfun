# 🔬 ScienceQuest

A gamified science quiz website for students. Pick Biology, Chemistry, Mathematics or Physics, choose a chapter, answer questions with instant feedback, and earn XP, stars and badges.

**Live site:**

> Made with ❤️ By Shaurya

---

## Features

- **Onboarding:** display name, avatar and theme (no email, password or personal data).
- **Four subjects** with colour identities: Biology (green), Chemistry (purple), Mathematics (blue), Physics (orange).
- **Chapter pages** with question counts, best score, stars and progress bars.
- **Quiz engine:** shuffled questions and options, instant feedback, explanations for every answer, progress bar, restart, and exit confirmation.
- **Gamification:** XP, star ratings, daily challenge, day streak and five achievements.
- **Mascots:** four original SVG mascots (Dr. Bio, Chem, Professor Math, Dr. Newton) that react to correct and wrong answers.
- **Four themes:** light, dark, pastel and arcade.
- **Responsive:** works on phones and desktops, and respects reduced-motion settings.
- **Fair scoring:** replaying a chapter only awards XP for beating your previous best, so scores cannot be farmed.

## Question bank

Questions follow the NCERT-based syllabus. Current counts:

| Subject | Questions | Chapters with questions |
|---|---|---|
| Biology | 59 | 8 |
| Chemistry | 70 | 8 |
| Mathematics | 20 | 3 |
| Physics | 10 | 2 |

The bank is still growing. Chapters are not yet complete for every subject. Import notes and corrections are in `question-banks/`.

## Project structure

```
index.html                 The whole app (HTML, CSS, JavaScript and question data)
DEPLOY.md                  Step-by-step hosting and custom domain guide
tests/quiz.test.js         Automated tests (Node.js)
question-banks/
  source/                  Original question files, kept unchanged
  REVIEW_REPORT*.md        Audit reports: corrections, exclusions, items to review
  import_*.py, pcm_lib.py  One-time import scripts (not needed to run the site)
```

## Run locally

No installation is needed. Double-click `index.html`, or run a local server:

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Run the tests

Requires [Node.js](https://nodejs.org). The tests load `index.html`, check every question, and play each imported chapter.

```bash
node tests/quiz.test.js
```

The tests check:
- each question has four distinct options, a valid answer key and an explanation
- no duplicate or near-duplicate questions
- the correct answer is preserved after shuffling
- answer feedback, XP awards and replay protection

## Deploy

The site is a single static file, so any static host works (Netlify, Vercel, GitHub Pages). See `DEPLOY.md` for the full steps, including connecting your own domain and HTTPS.

Quick version: upload `index.html` to Netlify (drag and drop), or turn on **GitHub Pages** in the repository settings and select the main branch.

## Adding questions

Questions live in the `D` array inside `index.html`. Each question is:

```js
[ "Question text", ["Option A", "Option B", "Option C", "Option D"], correctIndex, "Explanation", "ID", "Topic", "Difficulty" ]
```

`correctIndex` is 0 to 3. Use plain Unicode for symbols (H₂O, x², √, Δ, °). After editing, run `node tests/quiz.test.js` to validate.

## Privacy

Everything is stored only in the visitor's own browser (`localStorage`): display name, avatar, theme, a random anonymous ID, XP and quiz history. Nothing is sent to any server, and there is no analytics or advertising.

## Known limitations

- Progress is saved per browser and does not sync between devices.
- **The leaderboard is demo-only.** It shows sample players and local scores. A shared leaderboard needs a backend that has not been built yet.
- No sound, no admin panel, no maths-rendering library (symbols are Unicode text).
- Question difficulty is provisional ("Medium") for imported questions.
- Syllabus coverage is partial and has not been verified against the official NCERT site.

## Credits

Original mascot artwork and code by Shaurya. Questions are original educational content written for this project.

Made with ❤️ By Shaurya
