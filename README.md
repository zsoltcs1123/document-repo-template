# Document Repository Template

A lightweight GitHub template for document-first repositories: markdown conventions, agent guidance, and enforced conventional commits.

## Features

- **AGENTS.md** — conventions for humans and AI agents working on documents
- **conventional-pre-commit** — commit message validation with required scopes
- **prek** — installs and runs git hooks without a language toolchain
- **EditorConfig** — consistent markdown and YAML formatting

## Quick Start

### Prerequisites

- [prek](https://github.com/j178/prek) — pre-commit compatible hook runner
- [uv](https://docs.astral.sh/uv/) — Python package manager (for the local doc browser)

### Setup

> **Starting a new project from this template?**
>
> Follow the [step-by-step guide](docs/use-this-template.md).
>
> It covers customizing scopes, conventions, and removing template placeholders.

For an existing clone:

```bash
prek install --hook-type commit-msg
prek install
uv sync
```

Preview documents locally:

```bash
uv run zensical serve
```

## Development

See **[DEVELOPING.md](DEVELOPING.md)** for commit conventions and hook details.

```bash
prek run --all-files       # Run all hooks manually
prek run conventional-pre-commit --hook-stage commit-msg --commit-msg-filename /tmp/msg.txt
```

## Project Structure

```
your-project/
├── content/               # Documents (served by Zensical)
├── docs/                  # Repo guides and meta-documentation
├── zensical.toml          # Local doc browser configuration
├── pyproject.toml         # uv project file (Zensical dev dependency)
├── AGENTS.md              # Agent and document conventions
└── DEVELOPING.md          # Commits and hooks
```

## Documentation

- **[Use this template](docs/use-this-template.md)** — Turn this template into your project
- **[DEVELOPING.md](DEVELOPING.md)** — Commit conventions and hooks
- **[AGENTS.md](AGENTS.md)** — Document and agent conventions

## License

[Your License Here]
