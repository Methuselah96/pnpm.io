# Benchmarks of JavaScript Package Managers

**Last benchmarked at**: _Sep 3, 2024, 3:03 AM_ (_daily_ updated).

This benchmark compares the performance of npm, pnpm, Yarn Classic, and Yarn PnP (check [Yarn's benchmarks](https://yarnpkg.com/benchmarks) for any other Yarn modes that are not included here).

Here's a quick explanation of how these tests could apply to the real world:

- `clean install`: How long it takes to run a totally fresh install: no lockfile present, no packages in the cache, no `node_modules` folder.
- `with cache`, `with lockfile`, `with node_modules`: After the first install is done, the install command is run again.
- `with cache`, `with lockfile`: When a repo is fetched by a developer and installation is first run.
- `with cache`: Same as the one above, but the package manager doesn't have a lockfile to work from.
- `with lockfile`: When an installation runs on a CI server.
- `with cache`, `with node_modules`: The lockfile is deleted and the install command is run again.
- `with node_modules`, `with lockfile`: The package cache is deleted and the install command is run again.
- `with node_modules`: The package cache and the lockfile is deleted and the install command is run again.

## Large workspace

The app's `package.json` [here](https://github.com/pnpm/pnpm.io/blob/main/benchmarks/fixtures/large-workspace/package.json)

| action  | cache | lockfile | node_modules| npm | pnpm | Yarn | Yarn PnP |
| ---     | ---   | ---      | ---         | --- | ---  | ---  | ---      |
| install |       |          |             | 1m 9.6s | 20.2s | 26.6s | 14.3s |
| install | ✔     | ✔        | ✔           | 3.3s | 1.8s | 2.6s | n/a |
| install | ✔     | ✔        |             | 18.7s | 5.2s | 14.5s | 2.2s |
| install | ✔     |          |             | 30.2s | 14.3s | 18.1s | 5.1s |
| install |       | ✔        |             | 24.3s | 11.1s | 22.6s | 10.1s |
| install | ✔     |          | ✔           | 3s | 6.9s | 5.3s | n/a |
| install |       | ✔        | ✔           | 3.1s | 1.9s | 10.8s | n/a |
| install |       |          | ✔           | 3s | 13.3s | 14s | n/a |

<img alt="Graph of the large-workspace results" src="/img/benchmarks/large-workspace.svg" />