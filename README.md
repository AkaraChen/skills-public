# skills-public

## Skills

- [init-deep](init-deep/SKILL.md): Generate hierarchical codebase instructions.
- [write-goal](write-goal/SKILL.md): Turn a rough intention into a verifiable goal. Copied from the [Kimi Code open-source repository](https://github.com/MoonshotAI/kimi-code) by Moonshot AI; see [source and license details](write-goal/README.md).
- [resume-claude](resume-claude/SKILL.md): Resume or continue work from a recent Claude Code session. Copied from the **Grok Build (grok CLI) bundled skills** by SpaceXAI (xAI); see [source and license details](resume-claude/README.md).
- [resume-codex](resume-codex/SKILL.md): Resume or continue work from a recent Codex CLI / Codex VS Code session. Copied from the **Grok Build (grok CLI) bundled skills** by SpaceXAI (xAI); see [source and license details](resume-codex/README.md).
- [resume-cursor](resume-cursor/SKILL.md): Resume or continue work from a recent Cursor CLI / Cursor Desktop session. Copied from the **Grok Build (grok CLI) bundled skills** by SpaceXAI (xAI); see [source and license details](resume-cursor/README.md).

The three `resume-*` skills share the runtime in [`shared/resume-session`](shared/resume-session/) (`CORE.md` + `session_reader.py` + the upstream Apache-2.0 `LICENSE`). Copy the whole `shared/` directory together with the skill folders — the wrappers resolve their instructions via `${SKILL_DIR}/../shared/resume-session`.
