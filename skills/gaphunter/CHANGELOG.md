# Changelog

All notable changes to GapHunter are documented here.

Format: [Keep a Changelog](https://keepachangelog.com) · Versioning: [Semantic Versioning](https://semver.org)

---

## [1.8.0] — 2026-04-30

### Changed
- **Duolingo-style teaching flow**: Replaced lecture-then-test with retrieval-first (cold challenge → targeted teach → confirm). Backed by 100+ years of cognitive science — retrieval practice boosts retention more than additional study (Roediger & Karpicke, 2006; Bjork Lab). Lessons are now shorter and targeted to what the learner actually doesn't know.
- **Targeted teach**: Lesson length now adapts to the cold challenge result — 3 sentences if the guess was close, full lesson only when completely blank.
- **Confirm question**: Replaces generic "explain it back" with a single sharp question targeting the specific gap revealed in the cold challenge.

### Added
- **Tone guidelines**: Casual, sharp colleague voice with light wit. Push back directly on vague answers — "Too vague — be specific." Don't soften bad answers.
- **Streak guilt on session close**: When streak > 3, session close appends "Don't break it tonight." — loss aversion framing.
- **Daily goal prompt**: Asked once at session start (1 / 2 / 3 concepts). Celebrates completion when hit.
- **Comeback hook**: If AMBUSHES has a recent fail, session opens with "Settle the score?" before the dashboard.
- **Surprise drop**: After any ★★★, 1-in-4 chance of an unannounced bonus (deep-dive fact or instant Ambush). Unpredictable timing creates stronger habit loop (variable ratio reinforcement).
- **Aggressive near-miss framing**: Stats block now reads "SO CLOSE — just [N] more for..." to increase urgency.

---

## [1.7.1] — 2026-04-30

### Fixed
- **Progress file hallucination on First Run**: LLMs were fabricating plausible-looking values (streak counts, mastered concepts) instead of writing the correct zero-state. Added explicit field rules with a "no exceptions" prohibition against inventing or pre-filling any field.
- **Full file rewrite on Session Start**: LLMs were reconstructing the entire progress file from the template instead of updating only the changed fields. Added a partial update rule to Session Start — only `STREAK`, `LAST`, `SESSION-START`, and `CONCEPTS-THIS-SESSION` are changed; all other lines are copied verbatim.
- **Progress File template misread as fill-in prompt**: The format reference template at the bottom of the skill used placeholder-style syntax (`[concept]★★★`) that models interpreted as an invitation to generate example values. Added an explicit "FORMAT reference only" warning and a global partial update rule covering all mid-session writes.

---

## [1.7.0] — 2026-04-30

### Added
- **Doc verification step** in teaching flow: before teaching any library/framework-specific API (React hooks, Next.js functions, npm packages), GapHunter fetches current docs via context7 to ensure accuracy.
- **Stale-data warning**: if context7 is unavailable, GapHunter warns the user *before* the lesson that the content is based on training data and may be outdated, with install hint: `claude mcp add context7 -- npx -y @upstash/context7-mcp@latest`.
- **Session close hook**: when the user signals end of session ("bye", "done", etc.), GapHunter shows a one-line goodbye with streak status and goal proximity — creates pull for the next session.

---

## [1.6.1] — 2026-04-30

### Changed
- SKILL.md compressed ~9%: achievement tables converted to compact dot-separated lists, depth calibration prose replaced with bullet list, Mode step skip note moved inline for clarity. No behavior or experience changes.

---

## [1.6.0] — 2026-04-29

### Added
- **Multi-Repo Deep Mode**: configure multiple repos (local paths and GitHub repos) via a new `REPOS:` field in the progress file.
- **Consent gate**: shown at session start when repos are configured — scan all, skip, add, or remove repos before proceeding to the dashboard.
- **First-time setup prompt**: when mode=deep and no repos are configured, GapHunter prompts to add one at session start (skippable, repeats next session).
- **GitHub repo scanning**: reads repos via `gh` CLI API — no cloning required. Handles auth failures and missing `gh` installation gracefully per-repo.
- **Local clone detection**: when adding a GitHub URL, GapHunter checks 6 common local paths for an existing clone and offers to use it instead.
- **Scan report**: after every scan shows repos scanned, files read, and approximate chars of context (correct singular/plural).
- **New commands**: `add repo`, `show repos`, `remove repo [N]`, `scan now`.

---

## [1.5.0] — 2026-04-29

### Added
- **Motivational stats block** after ★★ or ★★★: shows mastered count, gaps remaining, streak, and the single closest achievement to unlock. Not shown after ★, skip flow, or The Ambush.

---

## [1.4.0] — 2026-04-29

### Added
- **/compact tip** in the pause message — Claude Code users are reminded to run `/compact` to compress built-up chat history.

### Fixed
- Role connection now delivered before the comprehension check, not after.
- First Run now proceeds immediately to Session Start after saving the profile — no longer waits for user input.
- Install command corrected (`npx skills add petrbui/skills -g`).

### Changed
- SKILL.md compressed by 34% with no logic or experience changes — faster to load on all platforms.

---

## [1.3.0] — 2026-04-28

### Added
- `change focus to [topic]` command — switch learning focus without losing progress.
- Hero banner in README.

---

## [1.2.0] — 2026-04-28

### Added
- **Learning focus question** in onboarding: choose current stack, a new language, a specific topic, or let GapHunter suggest.
- Onboarding questions now asked one at a time with numbered options.

### Fixed
- 5 pre-launch issues: vocabulary trigger, platform language, timer bug, areas definition, filesystem fallback.
- Teaching style question now ends with a clear numbered prompt.

---

## [1.1.0] — 2026-04-28

### Added
- NotebookLM integration guide and step-by-step onboarding in README.
- Gemini CLI install instructions and developer session example.
- Prerequisite check now runs before any teaching content.

### Security
- Hardened against 8 known AI skill attack vectors: instruction override, persona jailbreaks, fake authority claims, data exfiltration, indirect prompt injection, path traversal, goal hijacking, unicode hidden text attacks.

### Fixed
- Issues discovered in independent evaluator testing.

---

## [1.0.0] — 2026-04-28

### Added
- Initial GapHunter skill.
- Star-based mastery tracking (★ / ★★ / ★★★).
- The Ambush: surprise retention tests after 3+ lessons or 30+ days.
- 30+ achievements across 5 categories (streak, mastery, breadth, speed, consistency).
- 5 teaching formats: ADHD/Dyslexia, Standard, Dense, Socratic, Visual.
- Deep Mode: code intelligence for real gap detection.
- Progress file at `~/.adaptive-teacher-progress.md`.
- Multi-platform: Claude Code, Cursor, Gemini CLI, Copilot, JetBrains AI.
