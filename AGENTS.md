# agent-dotfiles

Portable configuration for coding agents, organized as GNU Stow packages:

- `shared/` installs `~/.agents/skills/`, read natively by Pi and others.
- `pi/` installs `~/.pi/agent/` (settings, instructions, prompts, themes,
  extensions, subagent definitions).
- `claude/` installs `~/.claude/skills/` as per-skill symlinks into `shared/`.

To add a harness, create another top-level package mirroring its home layout.
To add a shared skill, add `shared/.agents/skills/<name>/SKILL.md` and a
matching link `claude/.claude/skills/<name> -> ../../../shared/.agents/skills/<name>`.

## Rules

- Never commit credentials, sessions, caches, package installs, or other
  runtime state. `.gitignore` lists the known Pi paths; keep it current.
- Keep paths relative and free of usernames. The prompt aliases in
  `pi/.pi/agent/prompts/0*.md` are relative links that assume this repository
  sits two directory levels below `$HOME` (for example `~/dotfiles/agents` or
  `~/.config/agent-dotfiles`). Preserve that depth when adding similar links.
- Files here are stowed into `$HOME` as symlinks, so edits take effect
  immediately. After adding or removing files, restow the affected packages.

## Committing

This repository is usually checked out as the `agents/` submodule of
`ChienNQuang/dotfiles`. Commit and push here first, then update the submodule
pointer in the parent:

```sh
git add -A && git commit -m "<summary>" && git push origin main
cd .. && git add agents && git commit -m "agents: <summary>" && git push origin main
```

If this checkout is standalone (not inside `dotfiles/`), only the first line
applies.

## Verifying

- Pi: `printf '{"type":"get_commands"}\n' | pi --mode rpc --no-session` lists
  discovered skills and prompts.
- Claude Code: `~/.claude/skills/<name>/SKILL.md` must resolve to a regular
  file through the link chain.
- Fresh-install check: stow the packages into a temporary `--target` directory
  and confirm no broken links.
