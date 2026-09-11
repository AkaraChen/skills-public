# skills-public

## Skills

- [init-deep](init-deep/SKILL.md): Generate hierarchical codebase instructions.
- [write-goal](write-goal/SKILL.md): Turn a rough intention into a verifiable goal. Copied from the [Kimi Code open-source repository](https://github.com/MoonshotAI/kimi-code) by Moonshot AI; see [source and license details](write-goal/README.md).
- [resume-other-agent](resume-other-agent/SKILL.md): Resume or continue work from a recent Claude Code / Codex / Cursor session. Copied from the **Grok Build (grok CLI) bundled platform skills** by SpaceXAI (xAI); carries the shared reader runtime. See [source and license details](resume-other-agent/README.md).
- [resume-claude](resume-claude/SKILL.md) · [resume-codex](resume-codex/SKILL.md) · [resume-cursor](resume-cursor/SKILL.md): The upstream per-tool wrappers, kept verbatim as aliases (`TOOL` hardcoded) that resolve the reader runtime from `resume-other-agent`. See [source and license details](resume-codex/README.md).

The four `resume-*` folders belong together: the three aliases point at `../resume-other-agent/references/resume-session/` (`CORE.md` + `session_reader.py`), so the 80KB reader is stored once.
