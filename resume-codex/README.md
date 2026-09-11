# resume-codex

从 Codex CLI / Codex VS Code 会话继续工作。可用描述、路径或 native session id 定位会话，并会把外部会话记录当作不可信的惰性历史处理。

## 来源 / Attribution

This skill is copied from the **Grok Build / grok CLI bundled skills**, published by **SpaceXAI (xAI)**.

- Upstream project: [xai-org/grok-build](https://github.com/xai-org/grok-build) — "SpaceXAI's coding agent harness and TUI"
- Upstream commit at time of copy: `37949780c144e37df692e3d669051a21fec24f20` (2026-09-09)
- Original file: `~/.grok/bundled/skills/resume-codex/SKILL.md`, a **bundled** skill shipped with **grok CLI v1.0.25** (macOS aarch64)
- Copied on: 2026-09-11
- License: [Apache-2.0](../shared/resume-session/LICENSE), Copyright 2023-2026 SpaceXAI

> The bundled skill bodies are **not** present in the open-source repository tree — the repo ships only the skill-discovery/bundling machinery and the user guide. These files were extracted from the released CLI distribution (`grok inspect --json` reports them with `"source": {"type": "bundled"}`).

The original skill text is preserved unchanged.

## Runtime dependency

The `SKILL.md` here is a thin wrapper: it sets `TOOL` and `SHARED_DIR="${SKILL_DIR}/../shared/resume-session"`, then reads `CORE.md` from that shared directory. `CORE.md` drives `shared/resume-session/session_reader.py`, a Python standard-library-only transcript reader.

Keep `shared/` as a sibling of the skill folders, otherwise the wrapper cannot resolve its shared runtime:

```text
resume-claude/SKILL.md        # TOOL=claude
resume-codex/SKILL.md         # TOOL=codex
resume-cursor/SKILL.md        # TOOL=cursor
shared/resume-session/CORE.md
shared/resume-session/session_reader.py
```
