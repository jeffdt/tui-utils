# tui-utils

Shared Claude Code skills for jeffdt's TUI apps (rolomux, boomerang,
teleport, backlog, ...). Each top-level directory is a skill; vendor this
whole repo into a consumer repo via `git subtree` so `.claude/skills/`
resolves without any plugin install step.

## Adding this to a new repo

```sh
git subtree add --prefix=.claude/skills/tui-utils <path-or-url-to-this-repo> main --squash
```

This lands every skill at `.claude/skills/tui-utils/<skill>/SKILL.md`,
which Claude Code auto-discovers.

## Pulling updates

```sh
git subtree pull --prefix=.claude/skills/tui-utils <path-or-url-to-this-repo> main --squash
```

## Pushing changes made from inside a consumer repo back here

```sh
git subtree push --prefix=.claude/skills/tui-utils <path-or-url-to-this-repo> main
```

Prefer editing skills in this repo directly and pulling into consumers,
rather than editing the vendored copy in place, to avoid subtree merge
conflicts.

## Per-app overrides

`cutting-a-release/release.sh` derives the release asset name, Homebrew
formula name, and binary name from the consumer app's `Cargo.toml` package
name. Apps where that doesn't hold (e.g. a package named `tp-core` shipping
as formula `tp`) add a `[package.metadata.tui-utils]` table to override
`asset_name` / `formula_name`. See `cutting-a-release/release.sh`'s header
comment for details.

The `mockup` skill needs to know whether the app launches into a
fixed-width tmux popup or fills the terminal; it determines this by
inspecting the target repo at use-time rather than needing config.
