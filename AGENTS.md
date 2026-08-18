# Repository Instructions

## Purpose

This repository provides the Yarn Lock Changes GitHub Action. The action summarizes `yarn.lock` changes in pull request comments and can fail when it detects dependency downgrades.

## Layout

- `src/`: JavaScript action implementation and comment rendering utilities.
- `tests/unit/`: Jest coverage for Classic and Berry lockfile behavior, including downgrade cases.
- `tests/ci/`: lockfiles used to exercise the action against Yarn Classic and Berry v2/v3.
- `tests/performance/`: performance test fixtures.
- `dist/index.js`: checked-in action bundle referenced by `action.yml`.
- `action.yml`: action inputs and Node 20 entrypoint.

## Commands

CI installs dependencies with `yarn`.

- `yarn test`: run the Jest suite.
- `yarn lint`: run ESLint across the repository.
- `yarn build`: bundle `src/action.js` into `dist/` with `ncc`.
- `yarn optimize`: optimize assets with SVGO.

## Contribution Constraints

- Keep behavior compatible with the Yarn Classic, Berry v2, and Berry v3 fixtures exercised in `.github/workflows/tests.yml`.
- Run `yarn build` after source changes because `action.yml` executes the checked-in `dist/index.js` bundle.
- Preserve the action inputs and defaults documented in both `action.yml` and `README.md` when changing the public interface.
