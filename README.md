# tui-utils

Shared Claude Code skills for jeffdt's TUI apps (rolomux, boomerang,
teleport, backlog, ...): `mockup`, `vhs-recording`, `cutting-a-release`,
`live-preview`, plus the `/ship-it` command. This repo is a Claude Code
plugin and its own marketplace -- install it once and its skills are
available in every Claude Code session on this machine, regardless of which
repo you're in.

## Installing

```
/plugin marketplace add jeffdt/tui-utils
/plugin install tui-utils@tui-utils
```

That's a one-time, per-machine setup (not per-repo). No files get vendored
into rolomux/boomerang/teleport/backlog -- the skills load straight from the
plugin install.

## Updating

```
/plugin marketplace update tui-utils
/plugin update tui-utils
```

Or just edit this repo and push; the commands above pull the latest.

## Per-app overrides

`cutting-a-release`'s `release.sh` derives the release asset name, Homebrew
formula name, and binary name from the consumer app's `Cargo.toml` package
name. Apps where that doesn't hold (e.g. a package named `tp-core` shipping
as formula `tp`) add a `[package.metadata.tui-utils]` table to override
`asset_name` / `formula_name`. See `skills/cutting-a-release/release.sh`'s
header comment for details.

The `mockup` skill needs to know whether the app launches into a
fixed-width tmux popup or fills the terminal; it determines this by
inspecting the target repo at use-time rather than needing config.

## Layout

```
.claude-plugin/
  plugin.json       # plugin manifest
  marketplace.json  # self-hosted marketplace, source: ./
skills/
  mockup/
  vhs-recording/
  cutting-a-release/
  live-preview/
commands/
  ship-it.md        # /ship-it
```
