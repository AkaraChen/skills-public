# resume-codex

从 Codex CLI / Codex VS Code 会话继续工作。可用描述、路径或 native session id 定位会话，并会把外部会话记录当作不可信的惰性历史处理。

本技能同时是三个 resume 技能的**运行时载体**：`references/resume-session/` 里的 `CORE.md` 与 `session_reader.py` 只存这一份，`resume-claude` 和 `resume-cursor` 都指向这里。

## 目录

- `SKILL.md` —— 薄壳：设置 `TOOL=codex`，指向本目录的 `references/resume-session/CORE.md`
- `references/resume-session/CORE.md` —— 真正的技能指令（读会话 → 产出交接摘要 → 先核对再继续）
- `references/resume-session/session_reader.py` —— 只依赖 Python 标准库的会话读取器，支持 `claude` / `codex` / `cursor`；**这份由三个 resume 技能共用**
- `LICENSE` —— 上游 Apache-2.0

## 来源 / Attribution

This skill is copied from the **Grok Build / grok CLI bundled platform skills**, published by **SpaceXAI (xAI)**.

- Upstream project: [xai-org/grok-build](https://github.com/xai-org/grok-build) — "SpaceXAI's coding agent harness and TUI"
- Upstream commit at time of copy: `37949780c144e37df692e3d669051a21fec24f20` (2026-09-09)
- Original file: `~/.grok/bundled/skills/resume-codex/SKILL.md`, a **bundled** platform skill delivered by grok CLI's bundle sync (bundle version `public-2026-09-09-r2`, fetched from the `cli-chat-proxy` endpoint `/v1/subagents/bundle`)
- Copied on: 2026-09-11
- License: [Apache-2.0](LICENSE), Copyright 2023-2026 SpaceXAI

> These skill bodies are **not** part of the open-source repository tree, and they are **not** compiled into the CLI binary either. The repository open-sources only the bundle client (archive extraction + cache) and the skill-discovery machinery; the content itself ships as a versioned, auth-gated server-side bundle that the CLI syncs into `~/.grok/bundled/`. `grok inspect --json` reports them with `"source": {"type": "bundled"}`.

## 与上游的差异 / Adaptation

上游 `SKILL.md` 只改了一行路径（其余正文一字未改）：

```diff
-`SHARED_DIR="${SKILL_DIR}/../shared/resume-session"`
+`SHARED_DIR="${SKILL_DIR}/references/resume-session"`
```

上游把共用运行时放在技能目录的**兄弟**目录（`skills/shared/resume-session/`）。这里把它收进本技能自带的 `references/`，`resume-claude` 与 `resume-cursor` 指向本目录 —— 三个技能共用同一份 80KB 的 reader，只存一处。

| 文件 | 上游 SHA-256 | 本仓库 |
| --- | --- | --- |
| `SKILL.md` | `183364634d909c92bc0569448aaf4f5a5fb3bff2cbc1456ca8ebbf0dda0cd7f7` | `a2689632cb76fecaed24938b1f5f9dd0289d02b3429a07783a3181b714bd0747`（仅上面那一行路径不同） |
| `references/resume-session/CORE.md` | `f15d9c0163b103095a293f8d025fb8a490634ac95dafc85aed56d4b502cf7944` | 与上游一致，未改动 |
| `references/resume-session/session_reader.py` | `342853ca19f8d9f10dd171890ee1bbacec2350ea90221cb4ad6925cda2380a58` | 与上游一致，未改动 |
