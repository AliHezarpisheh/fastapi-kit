# How to Start a FastAPI Project (My Method)

## git

First thing, you should make your repo, a git repository:

```bash
git flow init
```

Don't forget the `v` prefix for version names.

## pyproject.toml

Copy and paste everything beneath the `[dependency-groups]` section(don't copy the
actual packages). These are the tools configuration.

## uv

Now, let's setup our Python environment:

```bash
uv init \
--name "oauth2-fastapi" \
--description "An implementation of Oauth2 flows, using FastAPI." --app \
--python 3.14.3

uv sync

uv add ruff isort mypy pre-commit --group

uv add pytest pytest-asyncio pytest-cov pytest-env pytest-order pytest-randomly \
--group testing

uv add "fastapi[standard]" pydantic-settings "sqlalchemy[asyncio]" asyncpg
```

Remove the `main.py`.

## Copying Other Files

Now it's time to copy and paste the files that you need in your new project.

### Files You Probably Need in Every Project

First of all, you should copy and paste `.gitignore`, `Dockerfile`, `settings.toml`,
`.pre-commit-config.yaml`, `.dockerignore`, `scripts/`, and `app/`. These are kinda the
most general and primitive things you should have in your project.

#### pre-commit

Use the `update-pre-commit.sh` script to update the pre-commit file. Then install it
using `pre-commit install`.

### Additional Files

You may need `docker-compose.yml`, `.env files`, `LICENSE`, `toolkit/`, `config/`, and
`tests/`. You may need them partially, or you should do some modifications on them so
they match the project.

---

That's it! Start working on the project business logic. Don't forget to update this repo
whenever you have modified the general files.
