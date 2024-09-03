# Benchmarks of JavaScript Package Managers

**Last benchmarked at**: _Sep 3, 2024, 3:10 AM_ (_daily_ updated).

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
| install |       |          |             | 1m 25.9s | 30.3s | 22.9s | 10.3s |
| install | ✔     | ✔        | ✔           | 1.6s | 1s | 1.6s | n/a |
| install | ✔     | ✔        |             | 14.5s | 9.9s | 12.7s | 1.3s |
| install | ✔     |          |             | 24.1s | 19.4s | 15.3s | 3.1s |
| install |       | ✔        |             | 18.2s | 23.2s | 18.7s | 7.3s |
| install | ✔     |          | ✔           | 2s | 5.6s | 3.5s | n/a |
| install |       | ✔        | ✔           | 1.8s | 1s | 8s | n/a |
| install |       |          | ✔           | 1.7s | 19s | 11s | n/a |

<img alt="Graph of the large-workspace results" src="/img/benchmarks/large-workspace.svg" />