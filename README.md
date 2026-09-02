# renovate-config

Org-wide Renovate configuration for SEA-AI.

Renovate opens PRs to update dependencies. We use the Mend-hosted app, so we don't
run it ourselves.

## Why this repo

Instead of a `renovate.json` in every repo, the hosted app reads one shared config
— `org-inherited-config.json` here — and applies it to every repo the Renovate app
runs on that has no config of its own. This is the only way to configure Renovate
org-wide without self-hosting. The repo and file names are fixed by Mend; don't
rename them.

"Runs on" = repos in the app's access list: Org → Settings → GitHub Apps →
Renovate → Repository access.

A change here hits every repo, so `main` is protected — edits go through a reviewed
PR, validated by CI.

## Files

- `org-inherited-config.json` — the inherited config.
- `.github/workflows/validate.yml` — runs Renovate's config validator on each PR.

## GitHub-side settings (not in this repo)

- **Allow auto-merge**, per repo: Settings → General → Pull Requests. `platformAutomerge`
  does nothing without it, and there's no org-wide default.
- **Org ruleset**: require PR + 1 approval, with the Renovate app in the bypass list
  so its PRs merge unattended. Renovate still waits for CI to pass on its own.

## Enable on a new repo

1. Add it to the Renovate app's access list (skip if that's set to "All repositories").
2. `gh repo edit SEA-AI/<repo> --enable-auto-merge`
3. Done — it inherits this config. Don't add a `renovate.json` unless the repo needs
   different behaviour. Check the first run at developer.mend.io/github/SEA-AI.
