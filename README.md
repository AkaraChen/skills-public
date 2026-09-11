# skills-public

## Skills

- [init-deep](init-deep/SKILL.md): Generate hierarchical codebase instructions.
- [write-goal](write-goal/SKILL.md): Turn a rough intention into a verifiable goal. Copied from the [Kimi Code open-source repository](https://github.com/MoonshotAI/kimi-code) by Moonshot AI; see [source and license details](write-goal/README.md).
- [resume-claude](resume-claude/SKILL.md): Resume or continue work from a recent Claude Code session. Copied from the **Grok Build (grok CLI) bundled platform skills** by SpaceXAI (xAI); see [source and license details](resume-claude/README.md).
- [resume-codex](resume-codex/SKILL.md): Resume or continue work from a recent Codex CLI / Codex VS Code session. Copied from the **Grok Build (grok CLI) bundled platform skills** by SpaceXAI (xAI); see [source and license details](resume-codex/README.md).
- [resume-cursor](resume-cursor/SKILL.md): Resume or continue work from a recent Cursor CLI / Cursor Desktop session. Copied from the **Grok Build (grok CLI) bundled platform skills** by SpaceXAI (xAI); see [source and license details](resume-cursor/README.md).

The three `resume-*` skills are the same wrapper with a different `TOOL`, and they share one reader runtime. It is stored once, under [`resume-codex/references/resume-session/`](resume-codex/references/resume-session/) (`CORE.md` + `session_reader.py`); `resume-claude` and `resume-cursor` point at it via `../resume-codex/references/resume-session`. Keep the three folders side by side.
