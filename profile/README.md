# ricochet

**The universal data science deployment platform.**

Deploy R, Julia, and Python apps, APIs, documents, and scripts on your own infrastructure, secured by your identity provider and scaled on demand.
Self-host it free with the [Community Edition](https://docs.ricochet.rs/latest/admin/pricing/5-community-edition/), or use Ricochet Cloud.

[Website](https://ricochet.rs) · [Docs](https://docs.ricochet.rs) · [Pricing](https://ricochet.rs/pricing) · [Discord](https://discord.gg/hgdXEm8xuT) · [Bluesky](https://bsky.app/profile/ricochet.rs)

## Quick start

Deploy a sample app to the public trial instance, which we reset every week:

```sh
curl -fsSL https://raw.githubusercontent.com/ricochet-rs/cli/main/install.sh | sh
ricochet login -S https://try.ricochet.rs
git clone https://github.com/ricochet-rs/test-apps.git /tmp/test-apps
cd /tmp/test-apps/r/waiting
ricochet deploy -S https://try.ricochet.rs
```

To run your own server, see the [installation guide](https://docs.ricochet.rs/latest/admin/installation/1-host/).

## Apps and tasks

Everything you deploy is an app or a task.
Apps stay running at a persistent URL, and ricochet load balances them across instances and scales them with demand.
Tasks run to completion on a schedule, from the REST API, or from the CLI.
You can publish any task that renders HTML as a static site.

- R: Shiny, Plumber, plumber2, Ambiorix, `_server.yml` standard, R Markdown, Quarto, and R scripts
- Julia: Dash.jl, Quarto, and Julia scripts
- Python: FastAPI, Flask, Streamlit, Dash, Shiny for Python, Jupyter, Quarto, and Python scripts

## How it works

- ricochet restores each deployment's environment from `renv.lock`, `Manifest.toml`, or `uv.lock`.
- Users sign in through any OIDC provider, and you make each item private, internal, or external.
- ricochet is one binary that runs your content on a Linux host, in Docker or Podman, or on Kubernetes.
- Deploy from the CLI, or connect a Git repository and branch and ricochet pulls and redeploys your content.
- ricochet keeps each app's and task's persistent storage across redeploys.
- ricochet includes audit logs, OpenTelemetry metrics and traces, scoped API keys, and encrypted environment variables.

## Repositories

| Repo                                                  | What it is                              |
| ----------------------------------------------------- | --------------------------------------- |
| [cli](https://github.com/ricochet-rs/cli)             | The `ricochet` command-line client      |
| [docs](https://github.com/ricochet-rs/docs)           | Documentation source                    |
| [helm](https://github.com/ricochet-rs/helm)           | Helm chart for Kubernetes               |
| [ansible](https://github.com/ricochet-rs/ansible)     | Ansible collection for server installs  |
| [exec-envs](https://github.com/ricochet-rs/exec-envs) | Execution environments                  |
| [skills](https://github.com/ricochet-rs/skills)       | Agent skills for Claude Code and Codex  |
| [test-apps](https://github.com/ricochet-rs/test-apps) | Example apps and tasks                  |
