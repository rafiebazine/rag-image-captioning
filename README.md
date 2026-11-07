# Repository Guidelines

## Branches

- `main`: shared stable branch.
- `rafie`: repository coordination and the only branch allowed to update `phase_01_data_exploration/splitted_data_set/`.
- `bella`, `hadil`, `raouf`, `zinou`: each contributor works only on their own branch.

## Workflow

1. clone the repo, link your local branch to your remote branch.
2. Push changes only to your own branch.
3. Open a pull request from your branch into `main` as base branch to merge.
4. Keep changes focused and do not push directly to `main`.

## Frozen dataset

The files under `phase_01_data_exploration/splitted_data_set/` are frozen. Only Rafie may change them. Any dataset change changes the results, so all affected scripts must be run again and the new results must be recorded before merging.
