# GapHunter

<p align="center">
  <img src="../hero.png" alt="GapHunter — Locating Knowledge Gaps" width="100%" />
</p>

<p align="center">
  <a href="https://skills.sh/petrbui/skills/gaphunter"><img src="https://img.shields.io/badge/skills.sh-gaphunter-5b21b6?logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik0xMiAyQzYuNDggMiAyIDYuNDggMiAxMnM0LjQ4IDEwIDEwIDEwIDEwLTQuNDggMTAtMTBTMTcuNTIgMiAxMiAyem0tMSAxNHYtNEg3bDUtOHY0aDRsLTUgOHoiLz48L3N2Zz4=" alt="skills.sh" /></a>
  <a href="https://github.com/petrbui/skills/stargazers"><img src="https://img.shields.io/github/stars/petrbui/skills?style=flat&label=stars" alt="GitHub Stars" /></a>
  <a href="https://github.com/petrbui/skills/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-green" alt="MIT License" /></a>
</p>

> The adaptive AI teacher that finds your weak spots and fills them —
> for developers, PMs, QA engineers, designers, and complete beginners.

Works on **Claude Code, Cursor, GitHub Copilot, Gemini CLI, JetBrains AI**, and any LLM agent.

---

## Install

```bash
npx skills add petrbui/skills -g
```

Then open your AI assistant and type:
```
Use the gaphunter skill
```

<details>
<summary>Manual install (Claude Code, Gemini CLI, other agents)</summary>

**Claude Code**
```bash
mkdir -p ~/.claude/skills/gaphunter
curl -o ~/.claude/skills/gaphunter/SKILL.md \
  https://raw.githubusercontent.com/petrbui/skills/main/gaphunter/SKILL.md
```

**Gemini CLI**
```bash
mkdir -p ~/.gemini/skills/gaphunter
curl -o ~/.gemini/skills/gaphunter/SKILL.md \
  https://raw.githubusercontent.com/petrbui/skills/main/gaphunter/SKILL.md
```

**Cursor / GitHub Copilot / JetBrains AI / Other**
Copy `SKILL.md` to your agent's skills directory.

</details>

---

## What It Does

- **Finds your gaps** — scans your git history (Light Mode) or codebase (Deep Mode) to detect what you actually use but don't fully understand
- **Teaches it** — one concept at a time, calibrated to your role and teaching style
- **Verifies retention** — comprehension check after every lesson: explain it back in your own words
- **Tracks mastery** — ★ / ★★ / ★★★ stars, saved to `~/.adaptive-teacher-progress.md`
- **Hunts weak spots** — The Ambush: surprise retests on concepts you thought you mastered
- **Keeps you coming back** — streaks, 30+ achievements, session close hook with your next goal
- **Exports to NotebookLM** — clean markdown digest after every session for review, flashcards, or the auto-podcast

---

## Who It's For

| Role | What you get |
|------|-------------|
| Junior Dev | Analogies, patience, encouragement |
| Mid-level Dev | Balanced depth, real-world examples |
| Senior Dev | Dense mode, edge cases, no hand-holding |
| Team Lead | Architecture and team implications |
| Product Manager | Business analogies, understand WHY devs say what they say |
| QA Engineer | Connect concepts to quality, testing, and deploy pipelines |
| Designer | Visual analogies, understand components and constraints |
| Complete Beginner | Zero assumed knowledge, everyday analogies only |

---

## Getting Started

**1. Install** — run the command above.

**2. Start a session** — type `Use the gaphunter skill` in your AI assistant.

**3. Answer 7 setup questions** (first run only) — role, stack, what you want to learn, experience, preferences, teaching style, and mode. Honest answers = better lessons.

**4. Learn** — type `suggest` to let GapHunter pick, or `teach me [anything]` to choose yourself.

**5. Come back tomorrow** — your streak is counting.

---

## Commands

| Say | Action |
|-----|--------|
| `teach me [concept]` | Start a lesson |
| `suggest` | GapHunter picks your next gap |
| `skip [concept]` | Quick verify → mark as known |
| `vocab [term]` | Plain-English definition, no full lesson |
| `ambush me` | Fire The Ambush now |
| `my progress` | Show dashboard |
| `export session` | Generate NotebookLM digest |
| `switch to [format] mode` | Change teaching style |
| `change focus to [topic]` | Switch learning focus without losing progress |
| `add repo [path or github:owner/repo]` | Add a repo to Deep Mode scanning |
| `show repos` | List configured repos |
| `remove repo [N]` | Remove a repo by number |
| `scan now` | Scan all repos immediately |
| `continue` | Override a pause |
| `reset profile` | Start fresh |

---

## Teaching Styles

| Style | Best for |
|-------|---------|
| 📱 ADHD/Dyslexia | Short chunks, bold terms, no walls of text |
| 📖 Standard | Balanced depth |
| ⚡ Dense | Seniors, no hand-holding |
| 🧠 Socratic | Learn by being questioned |
| 🎨 Visual | ASCII diagrams, tables, flow charts |

Switch anytime: `"switch to visual mode"`

---

## Deep Mode

For developers. GapHunter reads your actual code to find real gaps — not just what you say you know.

- **Local repos** — scans files with LSP/file tools, maps patterns to likely gaps
- **GitHub repos** — fetches via `gh` API, no cloning required (`github:owner/repo`)
- **Multi-repo** — configure as many repos as you want with `add repo`
- **Consent gate** — shown at session start, scan or skip on your terms

Requires a platform with file access (Claude Code, Cursor). Falls back to Light Mode automatically if tools are unavailable.

---

## ⏳ Learn While You Wait

AI generating code? Tests running? Build in progress?

```
teach me event-loop
```

3 minutes. One concept. Real retention. Streak maintained.

---

## 📓 NotebookLM Export

Type `export session` at the end of any session to get a clean markdown digest. Paste it into [NotebookLM](https://notebooklm.google.com) to:
- Quiz yourself on what you learned
- Generate flashcards
- Listen to the auto-podcast version

---

## Examples

See the [`examples/`](../examples/) folder for real session transcripts:
- [`session.md`](../examples/session.md) — PM learning APIs from scratch
- [`session-dev.md`](../examples/session-dev.md) — Senior dev with Deep Mode, vocab lookup, and The Ambush

---

## Safety

- Progress saved to `~/.adaptive-teacher-progress.md` — fixed path, never user-supplied
- Stores only topic names, stars, dates, achievement slugs — no code, no secrets, no personal data
- Light Mode: zero file access
- Deep Mode: never reads `.env`, credentials, keys, or secret files
- GitHub repos scanned via `gh` API only — no cloning, no local file access outside configured repos
- Delete the progress file anytime to fully reset — no data elsewhere

---

## License

MIT — free to use, fork, and share.
