# Benchmarks of JavaScript Package Managers

**Last benchmarked at**: _Sep 3, 2024, 3:15 AM_ (_daily_ updated).

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
| install |       |          |             | 1m 31.4s | 41.3s | 38.4s | 17.3s |
| install | ✔     | ✔        | ✔           | 3.8s | 2.6s | 3.3s | n/a |
| install | ✔     | ✔        |             | 39.5s | 18.4s | 23.9s | 2.7s |
| install | ✔     |          |             | 55.8s | 29.1s | 27.7s | 5.7s |
| install |       | ✔        |             | 45.5s | 31.9s | 33.6s | 13.1s |
| install | ✔     |          | ✔           | 4.3s | 7.6s | 6.5s | n/a |
| install |       | ✔        | ✔           | 4.6s | 2.6s | 13.2s | n/a |
| install |       |          | ✔           | 4.3s | 26.5s | 16s | n/a |

<img alt="Graph of the large-workspace results" src="/img/benchmarks/large-workspace.svg" />