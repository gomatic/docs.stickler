---
title: stickler
---

**stickler** is the gomatic **lint runner** — a stickler for the rules. It executes a set of analyzer tools to completion, normalizes their findings into one diagnostic schema, writes the report to stdout in the chosen format, prints a pass/fail status to stderr, and **reports pass/fail via the process exit code**. Any finding or any tool error is a stickler failure; every tool still runs to completion first.

> **Note:** stickler was originally conceived as a single-binary analyzer suite. That role now belongs to the [yze](https://github.com/gomatic/docs.yze) family; stickler is the **runner** that orchestrates yze and other tools.

## Usage

```
stickler [--format human|json|github] [root]
```

- **Runner model** — each tool is an executable plus an output adapter (`Runner`). The [`yze`](https://github.com/gomatic/yze) suite is read via its native stickler-json (no adapter); `golangci-lint`'s JSON is adapted (its v2 stdout summary footer is skipped by decoding only the first JSON value).
- **`--format`** — `human` (default, one line per finding), `json` (the normalized result), `github` (Actions annotations). SARIF output is planned.
- **Exit code** — `0` only when every tool ran cleanly with zero findings; non-zero on any finding or tool error.

## Output streams

The normalized report is written to **stdout** (so machine formats pipe cleanly); the pass/fail status line is written to **stderr**.

## Related

- [yze](https://github.com/gomatic/docs.yze) — the analyzer family stickler runs (framework, analyzers, aggregator).
- [go-yze](https://github.com/gomatic/go-yze) — the diagnostic schema stickler normalizes into.

Planned: SARIF output, `--fix` (delegating to each tool's fixer), and a `stickler.yaml` tool configuration. v1 runs `yze` + `golangci-lint` zero-config.
