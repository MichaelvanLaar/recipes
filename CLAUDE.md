# Tandoor Recipes

Django 5 + DRF recipe manager with Vue 3 + TypeScript + Vuetify frontend, deployed via Docker.

## Key Config Files

| File | Purpose |
|------|---------|
| `.claudeignore` | Paths excluded from Claude Code indexing |
| `.claude/settings.json` | Permissions, hooks, environment variables |
| `.githooks/pre-commit` | Keeps Key Config Files table in sync |
| `.github/workflows/build-docker.yml` | Docker image build and push |
| `.github/workflows/ci.yml` | CI pipeline |
| `.github/workflows/codeql-analysis.yml` | TODO: add description |
| `.github/workflows/docs.yml` | TODO: add description |
| `.gitignore` | Git ignore patterns |
| `mkdocs.yml` | TODO: add description |
| `openapitools.json` | TODO: add description |
| `.prettierignore` | TODO: add description |
| `.prettierrc` | Prettier config (printWidth 179, no semis) |
| `pyproject.toml` | yapf + isort formatter config |
| `pytest.ini` | Pytest config, tests in cookbook/tests/ |
| `scripts/sync-config-table.sh` | Auto-sync script for Key Config Files table |

## Commands

**Backend (project root):**

- `pytest cookbook/tests/` — run Django test suite
- `yapf -i <file>` — format a Python file
- `isort <file>` — sort imports in a Python file
- `python manage.py makemigrations` — create migrations
- `python manage.py migrate` — apply migrations

**Frontend (`vue3/` directory):**

- `yarn dev` — start Vite dev server
- `yarn build` — production build

## Structure

- `cookbook/` — Django app: models, views, serializers, API endpoints, tests
- `recipes/` — Django project: settings, URLs, WSGI
- `vue3/` — Vue 3 + TypeScript + Vuetify frontend
- `docs/` — MkDocs documentation

## Conventions

- Python: yapf line limit 179, PEP8-based; isort `multi_line_output=5`, `line_length=179`
- Frontend: Prettier (`printWidth` 179, no semicolons, 2-space indent, trailing commas ES5)
- Main development branch is `develop`, not `main`
- Use `django-scopes` for multi-tenancy — always scope querysets appropriately

## Don't

- Don't commit secrets or credentials to git
- Don't use `--force` flags — fix the underlying issue instead
- Don't modify `.env.template` with real values
- Don't bypass `django-scopes` — never use unscoped querysets in user-facing code

## Learnings

When the user corrects a mistake or points out a recurring issue, append a one-line summary to `.claude/learnings.md`. Don't modify CLAUDE.md directly.

## Compact Instructions

When compacting, preserve: list of modified files, current test status, open TODOs, and key decisions made.
