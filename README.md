# CodeRX

> Performance and UX driven fork of `ultraworkers/claw-code`, maintained by [RamsesCB](https://github.com/RamsesCB).

CodeRX is a practical fork focused on three goals:

1. Optimize runtime performance and reliability in real workflows.
2. Improve theming and UI extensibility (plugins, formatters, visual polish).
3. Make MCP and tool integrations easier to connect, validate, and operate.

## What this fork is

- A continuously synced fork of `ultraworkers/claw-code`.
- A safe place to iterate on optimization, theme system, and extension architecture.
- A production minded branch where changes are measured, tested, and realistic.

## What this fork is not

- Not a replacement for upstream governance.
- Not a promise to land risky rewrites in one step.
- Not a divergence for the sake of divergence.

## Upstream and sync model

Upstream source of truth:

- `https://github.com/ultraworkers/claw-code`

This repository:

- `https://github.com/RamsesCB/CodeRX`

Local setup:

```bash
git clone https://github.com/RamsesCB/CodeRX.git
cd CodeRX
git remote add upstream https://github.com/ultraworkers/claw-code.git
```

Sync flow:

```bash
git fetch upstream
git checkout main
git merge upstream/main
```

## Why CodeRX exists

Upstream is moving fast, specially in `rust/`. That speed is excellent, but it can make personal customization hard to maintain.

CodeRX keeps a disciplined strategy:

- Prefer additive modules over invasive edits in hot files.
- Isolate customization in plugin/tool/theme layers when possible.
- Keep compatibility with parity harness and existing workflows.

## Focus areas (realistic roadmap)

### 1) Performance optimization

- Startup profiling and reduction of cold start overhead.
- Lower tool call latency through better batching and caching.
- Context/token efficiency improvements in agent loops.
- Safer defaults for long running sessions (timeouts, backpressure, retries).

### 2) Theme and UX system

- Structured theme presets for TUI readability and contrast.
- Cleaner visual formatting for logs, diffs, and status blocks.
- Theme hooks for community packs without touching core execution code.
- Better defaults for accessibility and terminal compatibility.

### 3) Plugins and extension points

- Clear plugin boundaries for lifecycle hooks.
- Better docs and templates for extension authors.
- Small compatibility layer to reduce breakage after upstream updates.

### 4) MCP and integration formats

- Opinionated MCP connector presets for fast local setup.
- Health checks and diagnostics for MCP tool availability.
- Consistent format for declaring MCP endpoints and capabilities.
- Better examples for connecting local agents and automation servers.

### 5) Test and parity discipline

- Keep parity harness green when introducing optimizations.
- Add targeted tests for performance sensitive paths.
- Validate that theme/plugin additions do not break core behavior.

## Current repository map

- `rust/` -> canonical runtime and CLI implementation.
- `USAGE.md` -> build, auth, session, and operation workflows.
- `ROADMAP.md` -> upstream roadmap and work alignment.
- `PARITY.md` -> parity status and migration checkpoints.
- `src/` + `tests/` -> companion surfaces and validations.

## Quick start

```bash
cd rust
cargo build --workspace
./target/debug/claw --help
```

Run quality checks:

```bash
cd rust
cargo fmt
cargo clippy --workspace --all-targets -- -D warnings
cargo test --workspace
```

## Contribution policy for this fork

- Keep PRs small and reviewable.
- Avoid large edits in monolithic files unless absolutely necessary.
- Prefer new modules (`app.rs`, `format.rs`, plugin/tool files) over one-file growth.
- Document every optimization with expected impact and rollback path.

## Near-term milestones

- [ ] Baseline benchmarks for startup and tool call latency.
- [ ] First stable theme preset pack with accessibility checks.
- [ ] MCP connector profile spec (YAML/JSON) and validator command.
- [ ] Plugin scaffold template for quick extension bootstrapping.
- [ ] Refactor opportunities proposal for large `main.rs` hotspots.

## Disclaimer

- This repository is a fork and remains aligned with upstream direction whenever possible.
- This project is not affiliated with or endorsed by Anthropic.
