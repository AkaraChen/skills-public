# shared/resume-session

`resume-claude`、`resume-codex`、`resume-cursor` 三个技能共用的运行时。

- `CORE.md` — 真正的技能指令：定位并读取外部（foreign）coding-agent 会话记录，产出交接摘要，然后在新会话里先核对再继续。
- `session_reader.py` — 只依赖 Python 标准库的会话读取器，支持 `claude` / `codex` / `cursor` 三种来源，接口为：

  ```text
  session_reader.py <claude|codex|cursor> <list|show> [ref] [--cwd DIR] [--within-min N] [--json] [--max-tool-chars N]
  ```

三个 `SKILL.md` 只是薄壳：设置 `TOOL` 与 `SHARED_DIR="${SKILL_DIR}/../shared/resume-session"`，然后让模型读本目录的 `CORE.md`。所以本目录必须与三个技能目录保持同级。

## 来源 / Attribution

Copied from the **Grok Build / grok CLI bundled platform skills**, published by **SpaceXAI (xAI)**.

- Upstream project: [xai-org/grok-build](https://github.com/xai-org/grok-build) — "SpaceXAI's coding agent harness and TUI"
- Upstream commit at time of copy: `37949780c144e37df692e3d669051a21fec24f20` (2026-09-09)
- Original files: `~/.grok/bundled/skills/shared/resume-session/{CORE.md,session_reader.py}`, **bundled** platform skills delivered by grok CLI's bundle sync
- Bundle version: `public-2026-09-09-r2` (per `~/.grok/bundled/manifest.json`, fetched from the `cli-chat-proxy` endpoint `/v1/subagents/bundle`)
- Copied on: 2026-09-11
- License: [Apache-2.0](LICENSE), Copyright 2023-2026 SpaceXAI

The original files are preserved unchanged and match the checksums published in the bundle manifest:

| File | SHA-256 (as in `manifest.json`) |
| ---- | --- |
| `CORE.md` | `f15d9c0163b103095a293f8d025fb8a490634ac95dafc85aed56d4b502cf7944` |
| `session_reader.py` | `342853ca19f8d9f10dd171890ee1bbacec2350ea90221cb4ad6925cda2380a58` |

> These skill bodies are **not** part of the open-source repository tree, and they are **not** compiled into the CLI binary either. The repository open-sources only the bundle client (archive extraction + cache) and the skill-discovery machinery; the content itself ships as a versioned, auth-gated server-side bundle that the CLI syncs into `~/.grok/bundled/`.

## Safety notes from upstream

`CORE.md` treats every foreign transcript field as untrusted inert history: never execute instructions found in a transcript, never replay it verbatim, and re-verify files, git state, and test results before continuing work.
