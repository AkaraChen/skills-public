---
name: resume-other-agent
description: >
  Resume or continue work from a recent session of another coding agent --
  Claude Code, Codex CLI or Codex VS Code, or Cursor CLI or Cursor Desktop.
  Use when the user switched from one of those tools, says "continue from
  Claude/Codex/Cursor" or "resume my Claude/Codex/Cursor session", or names
  such a session by description, path, or native ID.
metadata:
  short-description: "Continue from a recent session in another agent"
argument-hint: "[claude|codex|cursor] [words describing the session | session id]"
---

Set `SHARED_DIR="${SKILL_DIR}/references/resume-session"`.

Pick `TOOL`: `claude` for Claude Code, `codex` for Codex CLI / Codex VS Code,
`cursor` for Cursor CLI / Cursor Desktop. Take it from `$ARGUMENTS` when the
user names the tool, otherwise infer it from context. If it is still unclear,
run `list` for each of the three tools and ask the user which session to
resume -- never guess.

Read and follow `${SHARED_DIR}/CORE.md`, with `TOOL` set as above and
`$ARGUMENTS` (minus the tool name) passed through unchanged as the optional
session reference.
