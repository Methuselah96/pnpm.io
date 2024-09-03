# Benchmarks of JavaScript Package Managers

**Last benchmarked at**: _Sep 2, 2024, 8:37 PM_ (_daily_ updated).

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

| action  | cache | lockfile | node_modules| pnpm | Yarn | Yarn PnP |
| ---     | ---   | ---      | ---         | ---  | ---  | ---      |
| install |       |          |             | 21.3s | 16.2s | 5.3s |
| install | ✔     | ✔        | ✔           | 1.4s | 1.8s | n/a |
| install | ✔     | ✔        |             | 2.7s | 12s | 1.6s |
| install | ✔     |          |             | 12.5s | 14.6s | 4.2s |
| install |       | ✔        |             | 10.1s | 12.1s | 1.7s |
| install | ✔     |          | ✔           | 6.3s | 4.5s | n/a |
| install |       | ✔        | ✔           | 1.3s | 1.9s | n/a |
| install |       |          | ✔           | 14.2s | 4.4s | n/a |

<img alt="Graph of the large-workspace results" src="/img/benchmarks/large-workspace.svg" />