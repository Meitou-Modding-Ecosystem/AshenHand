# The Ashen Hand

A shadow order for [MeitouClient](https://github.com/Meitou-Modding-Ecosystem/MeitouClient), built on
[Rivalry Core](https://github.com/Meitou-Modding-Ecosystem/MeitouMods): thieves fund it, hunters answer its grudges. Mod id `ashen.hand`;
what it does, its data file and settings: [docs/ashen-hand.md](docs/ashen-hand.md). GPL-3.0-or-later.

Rivalry Core is not in this repo: `meitou.lock.json` pins its release (`rivalry-core-v0.6.0`), which the build downloads into `deps/`
([framework lock](https://github.com/TheIvoryDisaster/GutenStructure/blob/beta/docs/framework-lock.md)). To build against a local Rivalry Core
clone instead, see [docs/local-development.md](docs/local-development.md).

- Build and run locally with Visual Studio, VS Code or the terminal (this repo's engine or the installed launcher, deployed to the game): [docs/play.md](docs/play.md).
- Setting up the repos on your machine: [docs/local-development.md](docs/local-development.md).
- Instructing agents on a change that spans repos: [docs/agents-across-repos.md](docs/agents-across-repos.md).

## Layout

- `engine/`: MeitouClient as a git submodule, pinned to the engine commit the mod builds against. After a pull that moves it:
  `git submodule update --init`.
- `AshenHand/`: the mod's project and `meitou.json`. `AshenHand.Tests/`: its tests (synthetic worlds, no game install needed).
  `AshenHand.Data/`: the generator that writes `AshenHand.mod` from the installed game (Play runs it).
- `Play/`: one-click build, deploy and run.
- `Directory.Build.props` imports the engine's, so mods build with the game's settings (warnings are errors).

## Branches

PRs into `beta`; CI (build and tests) must pass. `beta` is promoted to `main` once tested in play, and production goes through a PR to
`release`.
