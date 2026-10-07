# agent-dotfiles

Portable configuration for coding agents. Shared Agent Skills live under
`.agents/`; harness-specific settings, prompts, themes, extensions, and agent
definitions live under their native configuration directories.

The repository intentionally excludes credentials, sessions, caches, package
installations, and other machine-local runtime state.

## Layout

- `.agents/skills/` - skills shared by compatible coding agents
- `.pi/agent/` - Pi settings, instructions, prompts, themes, and extensions

Additional agent-specific directories can be added alongside `.pi/` as needed.

## Install through the dotfiles repository

This repository is included as the `agents` submodule of
[`ChienNQuang/dotfiles`](https://github.com/ChienNQuang/dotfiles).

```sh
git clone --recurse-submodules https://github.com/ChienNQuang/dotfiles.git ~/dotfiles
cd ~/dotfiles
stow --no-folding agents
pi update --extensions
```

Use `--no-folding` so agent runtime files remain in `$HOME` rather than being
written into the repository.

Existing checkout:

```sh
cd ~/dotfiles
git pull
git submodule update --init --recursive
stow --restow --no-folding agents
```

Credentials are deliberately not synchronized. Authenticate each agent on each
machine after installation.
