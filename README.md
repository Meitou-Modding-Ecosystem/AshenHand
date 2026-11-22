# The Ashen Hand

A shadow order for [MeitouClient](https://github.com/Meitou-Modding-Ecosystem/MeitouClient), built on
[Rivalry Core](https://github.com/Meitou-Modding-Ecosystem/RivalryCore): thieves fund it, hunters answer its grudges. Mod id `ashen.hand`;
what it does, its data file and settings: [docs/ashen-hand.md](docs/ashen-hand.md). GPL-3.0-or-later.

Rivalry Core is not in this repo: `meitou.lock.json` pins its release (`rivalry-core-0.6.5-beta.39661ed`), which the build downloads into `deps/`
([framework lock](https://github.com/TheIvoryDisaster/GutenStructure/blob/beta/docs/framework-lock.md)). To build against a local Rivalry Core
clone instead, see [docs/local-development.md](docs/local-development.md). New Rivalry Core releases arrive as PRs from the Framework update
workflow, merged when CI passes ([framework update](https://github.com/TheIvoryDisaster/GutenStructure/blob/beta/docs/framework-update.md)).

- Build and run locally with Visual Studio, VS Code or the terminal (this repo's engine or the installed launcher, deployed to the game): [docs/play.md](docs/play.md).
- Setting up the repos on your machine: [docs/local-development.md](docs/local-development.md).
- Instructing agents on a change that spans repos: [docs/agents-across-repos.md](docs/agents-across-repos.md).
- Agent rules for the engine pin, versions, CI and releases: [CLAUDE.md](CLAUDE.md) (same as `AGENTS.md`); step-by-step procedures:
  `.claude/skills/meitou-engine-release`.

## Layout

- `engine/`: MeitouClient as a git submodule, pinned to the engine commit the mod builds against. `git pull` does not move it: after
  every pull run `powershell -ExecutionPolicy Bypass -File tools\Update-Local.ps1 -Clean -Build`
  ([keep clones current](docs/local-development.md#keep-clones-current)).
- `AshenHand/`: the mod's project and `meitou.json`. `AshenHand.Tests/`: its tests (synthetic worlds, no game install needed).
  `AshenHand.Data/`: the generator that writes `AshenHand.mod` from the installed game (Play runs it).
- `Play/`: one-click build, deploy and run.
- `Directory.Build.props` imports the engine's, so mods build with the game's settings (warnings are errors).

## Branches

PRs into `beta`; CI (build and tests) must pass. `beta` is promoted to `main` once tested in play, and production goes through a PR to
`release`.
