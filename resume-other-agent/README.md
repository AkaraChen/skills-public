# resume-other-agent

从另一个 coding agent（Claude Code / Codex CLI、Codex VS Code / Cursor CLI、Cursor Desktop）的最近会话继续工作。可用描述、路径或 native session id 定位会话，并会把外部会话记录当作不可信的惰性历史处理。

本技能是上游三个薄壳的合并版，同时也是它们的**运行时载体**：`resume-claude` / `resume-codex` / `resume-cursor` 三个 alias 的 `SKILL.md` 是上游原文，只把路径指到本技能。

## 目录

- `SKILL.md` —— 选定 `TOOL`（`claude` / `codex` / `cursor`），然后读本目录的 `references/resume-session/CORE.md`
- `references/resume-session/CORE.md` —— 真正的技能指令（读会话 → 产出交接摘要 → 先核对再继续）
- `references/resume-session/session_reader.py` —— 只依赖 Python 标准库的会话读取器，支持 `claude` / `codex` / `cursor`
- `LICENSE` —— 上游 Apache-2.0

## 来源 / Attribution

Copied from the **Grok Build / grok CLI bundled platform skills**, published by **SpaceXAI (xAI)**.

- Upstream project: [xai-org/grok-build](https://github.com/xai-org/grok-build) — "SpaceXAI's coding agent harness and TUI"
- Upstream commit at time of copy: `37949780c144e37df692e3d669051a21fec24f20` (2026-09-09)
- Original files: the bundled platform skills `~/.grok/bundled/skills/resume-{claude,codex,cursor}/SKILL.md` and `~/.grok/bundled/skills/shared/resume-session/{CORE.md,session_reader.py}`
- Delivered as **bundled** platform skills by grok CLI's bundle sync — bundle version `public-2026-09-09-r2`, fetched from the `cli-chat-proxy` endpoint `/v1/subagents/bundle`
- Copied on: 2026-09-11
- License: [Apache-2.0](LICENSE), Copyright 2023-2026 SpaceXAI

> These skill bodies are **not** part of the open-source repository tree, and they are **not** compiled into the CLI binary either. The repository open-sources only the bundle client (archive extraction + cache) and the skill-discovery machinery; the content itself ships as a versioned, auth-gated server-side bundle that the CLI syncs into `~/.grok/bundled/`. `grok inspect --json` reports them with `"source": {"type": "bundled"}`.

## 与上游的差异 / Adaptation

上游是三个各自独立的 bundled skill，本体都是同一个薄壳，只把 `TOOL` 写死，其余一字不差：

```text
resume-claude/SKILL.md   Set TOOL=claude.  SHARED_DIR="${SKILL_DIR}/../shared/resume-session"
resume-codex/SKILL.md    Set TOOL=codex.   同上
resume-cursor/SKILL.md   Set TOOL=cursor.  同上
```

既然唯一的差别就是这个常量，而 `session_reader.py` 本来就同时支持三种来源，这里合并成一个技能：

```text
SHARED_DIR="${SKILL_DIR}/references/resume-session"      # 运行时收进技能自带的 references/
TOOL 从 $ARGUMENTS（或上下文）推断；三种工具都不明确时先 list 再问用户，不猜
```

`SKILL.md` 按上游薄壳的形状重写（上游没有 `resume-other-agent` 这个文件），`CORE.md` 与 `session_reader.py` 原封不动：

| 文件 | 上游 SHA-256 | 本仓库 |
| --- | --- | --- |
| `references/resume-session/CORE.md` | `f15d9c0163b103095a293f8d025fb8a490634ac95dafc85aed56d4b502cf7944` | 与上游一致，未改动 |
| `references/resume-session/session_reader.py` | `342853ca19f8d9f10dd171890ee1bbacec2350ea90221cb4ad6925cda2380a58` | 与上游一致，未改动 |
| `SKILL.md` | 上游无此文件（本仓库编写，本仓库 SHA-256 `ccb616ec1646f004f3a1f8ba3d3c80f4ee93f563d348bb47234e3c05271c7e04`） | — |

被合并掉的上游三个壳，原文 SHA-256：

| 上游文件 | SHA-256 |
| --- | --- |
| `skills/resume-claude/SKILL.md` | `2895371698c2e57887e60a261ba30525212da80aa08ffe9bf8f8c32a22a6003e` |
| `skills/resume-codex/SKILL.md` | `183364634d909c92bc0569448aaf4f5a5fb3bff2cbc1456ca8ebbf0dda0cd7f7` |
| `skills/resume-cursor/SKILL.md` | `be6de5404df93f13510a9ef847efc4f84263590751ab9db129ab93d13606f553` |

## 入口

- `/resume-other-agent`（本技能）—— 通用入口，`TOOL` 运行时推断，三种工具都不明确时先 `list` 再问用户
- `/resume-claude`、`/resume-codex`、`/resume-cursor` —— 上游的三个 alias，`TOOL` 写死，`SKILL.md` 即上游原文，路径指向本技能

四个技能目录需要放在一起（同级）：alias 通过 `../resume-other-agent/references/resume-session/` 解析运行时。
