# Changelog

Notable changes to dexrust, in [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)
format. Versions follow [semantic versioning](https://semver.org/spec/v2.0.0.html):
a feature is a minor bump, a fix-only release is a patch.

`dist` reads the section matching the version in `Cargo.toml` and uses it as the
body of the GitHub Release, so this file is also what a release *says*. Add
entries under `## [Unreleased]` as changes land (`### Added`, `### Changed`,
`### Fixed`, `### Removed`) and leave that section empty when there is nothing:
dist takes whatever sits under the heading as the release body, so a
placeholder line would ship as the notes.

The link definitions sit here, above the sections, because dist treats
everything after the last heading as part of the last release's notes.

[Unreleased]: https://github.com/DanielCarmingham/dexrust/compare/v0.2.0...HEAD
[0.2.0]: https://github.com/DanielCarmingham/dexrust/compare/v0.1.2...v0.2.0
[0.1.2]: https://github.com/DanielCarmingham/dexrust/compare/v0.1.1...v0.1.2
[0.1.1]: https://github.com/DanielCarmingham/dexrust/compare/v0.1.0...v0.1.1
[0.1.0]: https://github.com/DanielCarmingham/dexrust/releases/tag/v0.1.0

## [Unreleased]

### Fixed

- `complete --result ""` is rejected as a missing result, as in the original
  dex, instead of completing the task with empty notes.

## [0.2.0] - 2026-10-03

### Changed

- Renamed the project, repository, crate, and canonical binary from
  `dexrs`/`dex-cli` to `dexrust`. The `dex` compatibility binary remains.
- Added cargo-binstall metadata for the prebuilt GitHub Release archives.
- README credits the original dex project and states the version tracked.
- Repository root discovery walks up the directory tree for a `.git` entry,
  as the original does, instead of spawning `git rev-parse` twice per
  command. `dexrust list` goes from about 39 ms to 12 ms.

## [0.1.2] - 2026-09-22

### Fixed

- Release builds: the `dist` profile was missing from `Cargo.toml`, so the
  v0.1.1 GitHub Release and Homebrew formula never built. crates.io 0.1.1 is
  unaffected.

## [0.1.1] - 2026-09-22

First release on crates.io (as `dex-cli`), GitHub Releases, and the
`DanielCarmingham/homebrew-tap` tap.

### Fixed

- `dex version` now reports `dexrs v<version>` rather than echoing the name
  the binary was invoked as, so a compatibility install identifies itself.

## [0.1.0] - 2026-09-22

Feature parity with dex v0.16: the same `.dex/tasks.jsonl` store, archive,
config files, GitHub Issues and Shortcut Stories sync formats, MCP server, and
command surface, with every write wrapped in a locked atomic transaction.
Two behaviours improve on the original: repeated syncs are idempotent, and the
pushed-commit check works in repositories cloned while empty.
