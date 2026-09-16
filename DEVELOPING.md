# Development Guide

## Hooks

[prek](https://github.com/j178/prek) runs git hooks. Hook list and args live in `.pre-commit-config.yaml`.

```bash
prek install --hook-type commit-msg
prek install
prek run --all-files
```

`prek run --all-files` is the canonical check before you commit.

## Commits

[Conventional Commits](https://www.conventionalcommits.org/) with required scopes. Allowed types and scopes: `.pre-commit-config.yaml` (`conventional-pre-commit` hook).

- One line only: `{type}({scope}): {description}`. No body, no blank line after the subject.
- Description: imperative mood, lowercase start, no trailing period, max 72 characters.

### Default scopes

| Scope     | Use for                                     |
| --------- | ------------------------------------------- |
| `content` | Documents readers care about                |
| `meta`    | Agent guides, templates, repo documentation |
| `repo`    | Hooks, EditorConfig, Git attributes         |

### Default types

`feat`, `fix`, `docs`, `chore`, `refactor`, `style`

Do not use a HEREDOC or `-m` twice to add a body. Do not paste bullet lists into the commit message.

## Configuration files

| File                      | Purpose                       |
| ------------------------- | ----------------------------- |
| `.pre-commit-config.yaml` | Hook definitions              |
| `.editorconfig`           | Editor formatting consistency |
| `.gitattributes`          | Line endings                  |
