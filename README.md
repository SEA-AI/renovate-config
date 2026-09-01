# renovate-config

Org-wide [Mend Renovate](https://docs.renovatebot.com/mend-hosted/hosted-apps-config/)
inherited configuration for the `SEA-AI` org.

`org-inherited-config.json` is applied to every repo in the org that has no local
`renovate.json`. It is picked up by the Mend-hosted app via `inheritConfig`
(fixed keys: repo `renovate-config`, file `org-inherited-config.json`).

Edits to `org-inherited-config.json` affect every repo in the org, so `main` is
branch-protected: PR + 1 approval + passing `validate` check, no bypass.
`validate.yml` runs the official Renovate config validator on every push/PR.
