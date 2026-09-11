# resume-cursor

`/resume-cursor` 入口：从 Cursor CLI / Cursor Desktop 的最近会话继续工作。

本技能是 alias。`SKILL.md` 就是上游 grok CLI 里 `resume-cursor/SKILL.md` 的**原文**（frontmatter、description、metadata、argument-hint 一字未改），只把共用运行时的路径指向同级的 `resume-other-agent`。

## 目录

- `SKILL.md` —— 上游原文，仅改了一行路径
- `LICENSE` —— 上游 Apache-2.0

运行时不在这里，由同级技能 `resume-other-agent` 承载：`../resume-other-agent/references/resume-session/`（`CORE.md` + 80KB 的 `session_reader.py`，三个来源共用一份）。四个技能目录需要放在一起（同级）。

## 来源 / Attribution

Copied from the **Grok Build / grok CLI bundled platform skills**, published by **SpaceXAI (xAI)**. 完整的来源说明、bundle 版本与抓取方式见 [../resume-other-agent/README.md](../resume-other-agent/README.md)。

- Upstream project: [xai-org/grok-build](https://github.com/xai-org/grok-build) — "SpaceXAI's coding agent harness and TUI"
- Upstream commit at time of copy: `37949780c144e37df692e3d669051a21fec24f20` (2026-09-09)
- Original file: `~/.grok/bundled/skills/resume-cursor/SKILL.md`
- Delivered as a **bundled** platform skill by grok CLI's bundle sync — bundle version `public-2026-09-09-r2`, from the `cli-chat-proxy` endpoint `/v1/subagents/bundle`
- Copied on: 2026-09-11
- License: [Apache-2.0](LICENSE), Copyright 2023-2026 SpaceXAI

> These skill bodies are **not** part of the open-source repository tree, and they are **not** compiled into the CLI binary either — they ship as a versioned, auth-gated server-side bundle that the CLI syncs into `~/.grok/bundled/`.

## 与上游的差异 / Adaptation

`SKILL.md` 只有这一行路径不同（其余逐字未改）：

```diff
-`SHARED_DIR="${SKILL_DIR}/../shared/resume-session"`
+`SHARED_DIR="${SKILL_DIR}/../resume-other-agent/references/resume-session"`
```

上游把运行时放在三个技能目录的兄弟目录（`skills/shared/resume-session/`），并且三个 alias 各带一份自己的 `TOOL`；这里运行时由同级的 `resume-other-agent` 承载，只存一份。

| 文件 | 上游 SHA-256 | 本仓库 |
| --- | --- | --- |
| `SKILL.md` | `be6de5404df93f13510a9ef847efc4f84263590751ab9db129ab93d13606f553` | `e09d1d8a232662740f06f14d6620616388beace9d78bc3f6d3ebb078854dcc37`（仅上面那一行路径不同） |
