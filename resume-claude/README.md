# resume-claude

从 Claude Code 会话继续工作。可用描述、路径或 native session id 定位会话，并会把外部会话记录当作不可信的惰性历史处理。

## 目录

- `SKILL.md` —— 薄壳：设置 `TOOL=claude`
- 运行时不在这里：`CORE.md` 与 `session_reader.py` 由同级技能 `resume-codex` 提供，路径为 `../resume-codex/references/resume-session/`
- `LICENSE` —— 上游 Apache-2.0

## 来源 / Attribution

This skill is copied from the **Grok Build / grok CLI bundled platform skills**, published by **SpaceXAI (xAI)**.

- Upstream project: [xai-org/grok-build](https://github.com/xai-org/grok-build) — "SpaceXAI's coding agent harness and TUI"
- Upstream commit at time of copy: `37949780c144e37df692e3d669051a21fec24f20` (2026-09-09)
- Original file: `~/.grok/bundled/skills/resume-claude/SKILL.md`, a **bundled** platform skill delivered by grok CLI's bundle sync (bundle version `public-2026-09-09-r2`, fetched from the `cli-chat-proxy` endpoint `/v1/subagents/bundle`)
- Copied on: 2026-09-11
- License: [Apache-2.0](LICENSE), Copyright 2023-2026 SpaceXAI

> These skill bodies are **not** part of the open-source repository tree, and they are **not** compiled into the CLI binary either. The repository open-sources only the bundle client (archive extraction + cache) and the skill-discovery machinery; the content itself ships as a versioned, auth-gated server-side bundle that the CLI syncs into `~/.grok/bundled/`. `grok inspect --json` reports them with `"source": {"type": "bundled"}`.

## 与上游的差异 / Adaptation

上游 `SKILL.md` 只改了一行路径（其余正文一字未改）：

```diff
-`SHARED_DIR="${SKILL_DIR}/../shared/resume-session"`
+`SHARED_DIR="${SKILL_DIR}/../resume-codex/references/resume-session"`
```

上游把共用运行时放在技能目录的**兄弟**目录（`skills/shared/resume-session/`）。三个 resume 技能共用同一份 reader（`CORE.md` + 80KB 的 `session_reader.py`），所以只存一份、由同级技能 `resume-codex` 承载，本技能用相对路径指过去 —— 三个技能目录需要放在一起（同级）。

| 文件 | 上游 SHA-256 | 本仓库 |
| --- | --- | --- |
| `SKILL.md` | `2895371698c2e57887e60a261ba30525212da80aa08ffe9bf8f8c32a22a6003e` | `3564d4758919ea37bd23f449a7d88cf26939c5f9e3887fbc287e3bd43d4ea8f5`（仅上面那一行路径不同） |
| 运行时 `CORE.md` / `session_reader.py` | `f15d9c0163b103095a293f8d025fb8a490634ac95dafc85aed56d4b502cf7944` / `342853ca19f8d9f10dd171890ee1bbacec2350ea90221cb4ad6925cda2380a58` | 由 `resume-codex` 承载，与上游一致，未改动 |
