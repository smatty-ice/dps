# dps

Umbrella repo for DPS calculator projects.

## Projects

- [`osrs-dps-calc/`](osrs-dps-calc/): the OSRS Wiki DPS calculator (GPL-3.0 fork of [weirdgloop/osrs-dps-calc](https://github.com/weirdgloop/osrs-dps-calc)) with the loadout cap raised from 6 to 12. See its [README](osrs-dps-calc/README.md) for details and run instructions.

## GitHub Pages

[`deploy-pages.yml`](.github/workflows/deploy-pages.yml) deploys the repo to GitHub Pages on every push to the default branch: the landing page in [`site/`](site/) at the site root, and the calculator under `/osrs-dps/`. For `smatty-ice/dps` that is:

- https://smatty-ice.github.io/dps/ (landing page)
- https://smatty-ice.github.io/dps/osrs-dps/ (calculator)

GitHub Pages only publishes from public repositories on free plans, so the repo must be public (or on a paid plan) for the deploy to succeed. The workflow tries to enable Pages automatically on first deploy; if that step fails, enable it once under Settings, Pages, Source: GitHub Actions.
