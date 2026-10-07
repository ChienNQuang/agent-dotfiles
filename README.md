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

## Install standalone

Requires [GNU Stow](https://www.gnu.org/software/stow/).

```sh
mkdir -p ~/.local/share
git clone https://github.com/ChienNQuang/agent-dotfiles.git ~/.local/share/agent-dotfiles
stow --dir="$HOME/.local/share" --target="$HOME" --no-folding agent-dotfiles
pi update --extensions
```

Use `--no-folding` so credentials, sessions, caches, and other runtime state
remain in `$HOME` rather than being written into the repository.

Update an existing installation:

```sh
git -C ~/.local/share/agent-dotfiles pull --ff-only
stow --dir="$HOME/.local/share" --target="$HOME" --restow --no-folding agent-dotfiles
pi update --extensions
```

Remove the managed links without deleting machine-local runtime state:

```sh
stow --dir="$HOME/.local/share" --target="$HOME" --delete agent-dotfiles
```

## Install through the dotfiles repository

This repository is included as the `agents` submodule of
[`ChienNQuang/dotfiles`](https://github.com/ChienNQuang/dotfiles).

```sh
git clone --recurse-submodules https://github.com/ChienNQuang/dotfiles.git ~/dotfiles
cd ~/dotfiles
stow --no-folding agents
pi update --extensions
```

Existing checkout:

```sh
cd ~/dotfiles
git pull
git submodule update --init --recursive
stow --restow --no-folding agents
```

Credentials are deliberately not synchronized. Authenticate each agent on each
machine after installation.
