# Using This Template

This guide turns a fresh clone of the template into a clean, project-specific repository. Work through it top to bottom. When you finish, **no references to the template's placeholder names should remain** (`Document Repository Template`, `your-project`, `Your License Here`, etc.).

Throughout this guide, replace:

- `my-project` with your repository or project name
- `content,meta,repo` with your commit scopes when they no longer fit

## Prerequisites

- [Git](https://git-scm.com/)
- [prek](https://github.com/j178/prek)

## 1. Create the repository

Use the GitHub **"Use this template"** button, or clone and reset history:

```bash
git clone <template-url> my-project && cd my-project
rm -rf .git && git init
```

## 2. Install hooks

```bash
prek install --hook-type commit-msg
prek install
prek run --all-files
```

`prek run --all-files` must pass before you consider setup done.

## 3. Shape the document layout

The default folder is `content/`. Rename or replace it to match your use case:

| Use case              | Suggested layout                          |
| --------------------- | ----------------------------------------- |
| Single knowledge base | `content/` with topic subfolders          |
| Research notes        | `notes/` or `research/`                   |
| Personal wiki         | `wiki/`                                   |
| Multi-volume docs     | `docs/volume-1/`, `docs/volume-2/`, etc.  |

Update `AGENTS.md` and `README.md` if you change the default path.

## 4. Customize commit scopes

Scopes should reflect how you think about changes in *your* repo. Edit `.pre-commit-config.yaml` under `conventional-pre-commit`:

```yaml
args:
  - --strict
  - --force-scope
  - --scopes
  - handbook,notes,meta,repo   # your scopes
```

Guidelines:

- Keep scopes few and obvious (three to six is enough).
- Reserve `repo` for hooks, EditorConfig, and other tooling.
- Use `meta` for agent guides and internal documentation unless you have a better name.
- Name content scopes after collections (`handbook`, `notes`, `specs`) not individual files.

Update the scope tables in `DEVELOPING.md` and `AGENTS.md` to match.

## 5. Customize commit types (optional)

The default types suit most document repos: `feat`, `fix`, `docs`, `chore`, `refactor`, `style`.

To restrict or extend them, edit the type list at the bottom of the `conventional-pre-commit` args in `.pre-commit-config.yaml`, then mirror the change in `DEVELOPING.md`.

## 6. Tailor agent conventions

Edit `AGENTS.md` for your audience and workflow:

- Document format (Markdown only, or also Org, AsciiDoc, etc.)
- Filename rules
- Folder layout
- Tone, citation, or review expectations

Keep it short. Agents read this on every task.

## 7. Clean up the documentation

### `README.md`

- Replace the title and template description with your project's name and purpose.
- Remove the **"Use this template"** callout once setup is done.
- Update the project structure tree to your real layout.
- Remove the link to this guide from the Documentation section.
- Replace `[Your License Here]` with your actual license (and add a `LICENSE` file).

### `AGENTS.md`

- Remove the link to this guide.
- Update folder names and scope examples to match your repo.

## 8. Final sweep

Confirm nothing template-specific remains:

```bash
grep -rIn -e "Document Repository Template" -e "your-project" -e "Your License" \
  --exclude-dir=.git .
```

The command should return nothing.

## 9. Delete this guide

Once the sweep is clean:

```bash
rm docs/use-this-template.md
```

If `docs/` is empty afterward, remove the directory or add your own meta-docs there.

Setup complete. Commit with a conventional message, e.g. `chore(repo): initialize project from template`.
