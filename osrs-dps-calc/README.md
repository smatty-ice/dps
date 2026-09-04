# OSRS DPS Calculator (extended loadouts)

Self-hosted copy of the [OSRS Wiki DPS calculator](https://tools.runescape.wiki/osrs-dps) with the loadout cap raised from 6 to 12.

## Provenance and license

Vendored from [weirdgloop/osrs-dps-calc](https://github.com/weirdgloop/osrs-dps-calc) at commit `89c3e25b344aea90d0189746e4b5f73dde0f0383` (2026-09-02). Licensed under GPL-3.0, see [LICENSE](LICENSE). This copy is not affiliated with the OSRS Wiki or Weird Gloop.

## Changes from upstream

- `NUMBER_OF_LOADOUTS` raised from 6 to 12 (`src/lib/constants.ts`).
- TTK worker pool is sized from `NUMBER_OF_LOADOUTS` instead of a hardcoded 10 (`src/worker/worker.ts`).
- Loadout comparison and TTK comparison charts carry 12 distinct line colours instead of 6 (`src/app/components/results/LoadoutComparison.tsx`, `TtkComparison.tsx`).
- The loadout tab row wraps onto extra lines so 12 tabs fit the player column (`src/app/components/player/PlayerContainer.tsx`).
- The `cdn/equipment` and `cdn/monsters` image directories (roughly 200 MB) are not vendored. The app loads those images from `https://tools.runescape.wiki/osrs-dps/cdn/` at runtime, exactly as the production site does, so an internet connection is needed for item and monster images. `cdn/json` (the equipment, monster, and spell data the build imports) is vendored.

## Running

Requires Node 18 or newer. Yarn 4 is vendored in `.yarn/releases`, so a plain `yarn` (via corepack) picks the right version.

```sh
yarn install
yarn dev        # then open http://localhost:3000/osrs-dps
```

Other useful commands:

```sh
yarn build      # static export into out/, served under the /osrs-dps base path
yarn test       # jest suite
yarn lint       # eslint
```

A GitHub Actions workflow at the repo root ([`.github/workflows/deploy-pages.yml`](../.github/workflows/deploy-pages.yml)) builds this project with the base path overridden for GitHub Pages and deploys it to `https://<owner>.github.io/<repo>/osrs-dps/`.

## Updating game data

Equipment, monster, and spell data live in `cdn/json` as a snapshot from the vendored commit. To refresh, either copy `cdn/json` from a newer upstream checkout or run upstream's scraper scripts in `scripts/` (see their [CONTRIBUTING.md](CONTRIBUTING.md)).

## Acknowledgements

- The [weirdgloop/osrs-dps-calc](https://github.com/weirdgloop/osrs-dps-calc) authors and [contributors](https://github.com/weirdgloop/osrs-dps-calc/graphs/contributors), who built the entire calculator.
- Bitterkoekje's [spreadsheet](https://docs.google.com/spreadsheets/d/1wzy1VxNWEAAc0FQyDAdpiFggAfn5U6RGPp2CisAHZW8/edit?pli=1#gid=158500257) for much of the original math.
- The [OSRS Wiki](https://oldschool.runescape.wiki) contributors for item, monster, and spell data.
