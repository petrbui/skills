# Changelog

All notable changes to GapHunter are documented here.

Format: [Keep a Changelog](https://keepachangelog.com) · Versioning: [Semantic Versioning](https://semver.org)

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
- Install command corrected (`npx skills add petrbui/GapHunter -g`).

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
