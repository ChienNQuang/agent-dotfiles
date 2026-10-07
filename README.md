# agent-dotfiles

Portable configuration for coding agents, organized as one
[GNU Stow](https://www.gnu.org/software/stow/) package per harness plus a
`shared` package for assets every harness uses.

The repository intentionally excludes credentials, sessions, caches, package
installations, and other machine-local runtime state.

## Packages

| Package  | Installs to          | Contents                                              |
| -------- | -------------------- | ----------------------------------------------------- |
| `shared` | `~/.agents/skills/`  | Agent Skills read natively by Pi, Codex, and others   |
| `pi`     | `~/.pi/agent/`       | Pi settings, instructions, prompts, themes, extensions |
| `claude` | `~/.claude/skills/`  | Per-skill links into `shared` for Claude Code          |

Install only the packages for the harnesses you use. Harness packages do not
depend on `shared` being installed; `claude` links resolve inside the
repository.

Add a new harness by creating another top-level package directory that mirrors
its home-directory layout.

## Installation requirements

GNU Stow is required. This is not a skills-only package: Stow installs the
harness-specific configuration as well as the shared skills.

The optional `npx skills` CLI can distribute only `shared/.agents/skills/` to
selected agent harnesses. It does not install the rest of this repository and
therefore does not replace Stow.

## Install standalone

Clone into a directory two levels below `$HOME`, such as `~/.config`. The Pi
prompt aliases are relative links that assume this depth.

```sh
mkdir -p ~/.config
git clone https://github.com/ChienNQuang/agent-dotfiles.git ~/.config/agent-dotfiles
```

Then stow the packages you want. Examples:

```sh
# Pi only
stow --dir="$HOME/.config/agent-dotfiles" --target="$HOME" --no-folding shared pi
pi update --extensions

# Claude Code only
stow --dir="$HOME/.config/agent-dotfiles" --target="$HOME" --no-folding claude

# Everything
stow --dir="$HOME/.config/agent-dotfiles" --target="$HOME" --no-folding shared pi claude
```

Use `--no-folding` so credentials, sessions, caches, and other runtime state
remain in `$HOME` rather than being written into the repository.

Update an existing installation, naming the same packages you installed:

```sh
git -C ~/.config/agent-dotfiles pull --ff-only
stow --dir="$HOME/.config/agent-dotfiles" --target="$HOME" --restow --no-folding shared pi claude
pi update --extensions
```

Remove the managed links without deleting machine-local runtime state:

```sh
stow --dir="$HOME/.config/agent-dotfiles" --target="$HOME" --delete shared pi claude
```

## Install through the dotfiles repository

This repository is included as the `agents` submodule of
[`ChienNQuang/dotfiles`](https://github.com/ChienNQuang/dotfiles).

```sh
git clone --recurse-submodules https://github.com/ChienNQuang/dotfiles.git ~/dotfiles
stow --dir="$HOME/dotfiles/agents" --target="$HOME" --no-folding shared pi claude
pi update --extensions
```

Existing checkout:

```sh
cd ~/dotfiles
git pull
git submodule update --init --recursive
stow --dir="$HOME/dotfiles/agents" --target="$HOME" --restow --no-folding shared pi claude
```

Credentials are deliberately not synchronized. Authenticate each agent on each
machine after installation.
