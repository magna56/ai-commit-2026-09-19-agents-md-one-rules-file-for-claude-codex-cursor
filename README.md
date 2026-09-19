# AGENTS.md: One Rules File for Claude, Codex, Cursor and Copilot

**TL;DR:** Every major coding agent now reads AGENTS.md. Which file it actually uses depends on where that file sits, what else is in the repo, and which platform you are on.

Published from [The AI Commit](https://theaicommit.com/#2026-09-19/code) — Coding Agents & Productivity, 2026-09-19.

## Run

```bash
python3 code_example.py
```

## Output

```
agent is editing: packages/api/handlers/orders.py

  the usual mess
    .github/copilot-instructions.md        GitHub Copilot
    CLAUDE.md                              Claude Code, Claude (Bedrock)
    packages/api/AGENTS.md                 Codex, Cursor
    -> 3 different files in play

  consolidated (CLAUDE.md deleted)
    packages/api/AGENTS.md                 Claude Code, GitHub Copilot, Codex, Cursor
    nothing — no instructions at all       Claude (Bedrock)
    -> 2 different files in play

  consolidated, but an empty CLAUDE.md was left behind
    CLAUDE.md                              Claude Code, Claude (Bedrock)
    packages/api/AGENTS.md                 GitHub Copilot, Codex, Cursor
    -> 2 different files in play

  Bedrock-safe: AGENTS.md imports CLAUDE.md
    AGENTS.md                              GitHub Copilot, Codex, Cursor
    CLAUDE.md                              Claude Code, Claude (Bedrock)
    -> 2 different files in play

read the third layout again: deleting CLAUDE.md's CONTENTS is not enough.
the fallback is 'is there a CLAUDE.md', not 'does it say anything', so an
empty file keeps Claude Code on it while Codex and Cursor read AGENTS.md.

nearest-wins, same repo, different edit:
  packages/api/handlers/orders.py    Codex reads packages/api/AGENTS.md
  packages/web/app.tsx               Codex reads AGENTS.md
  README.md                          Codex reads AGENTS.md

```

## Code

See [`code_example.py`](code_example.py).
