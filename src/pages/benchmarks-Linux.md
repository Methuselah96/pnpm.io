# Benchmarks of JavaScript Package Managers

**Last benchmarked at**: _Sep 2, 2024, 10:40 PM_ (_daily_ updated).

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
- `update`: Updating your dependencies by changing the version in the `package.json` and running the install command again.

## Large workspace

The app's `package.json` [here](https://github.com/pnpm/pnpm.io/blob/main/benchmarks/fixtures/large-workspace/package.json)

| action  | cache | lockfile | node_modules| npm | pnpm | Yarn | Yarn PnP |
| ---     | ---   | ---      | ---         | --- | ---  | ---  | ---      |
| install |       |          |             | 1m 15.1s | 21.8s | 18.8s | 6.7s |
| install | ✔     | ✔        | ✔           | 3.4s | 2.2s | 2.6s | n/a |
| install | ✔     | ✔        |             | 19.1s | 5.5s | 14.3s | 2.4s |
| install | ✔     |          |             | 30.9s | 15.8s | 17.6s | 5.2s |
| install |       | ✔        |             | 25s | 11.6s | 14.1s | 2.4s |
| install | ✔     |          | ✔           | 3s | 6.7s | 5.4s | n/a |
| install |       | ✔        | ✔           | 3.2s | 2.1s | 2.6s | n/a |
| install |       |          | ✔           | 3.1s | 14.2s | 5.3s | n/a |
| update  | n/a | n/a | n/a | 20.4s | 10s | 1m 32s | 6.2s |

<img alt="Graph of the large-workspace results" src="/img/benchmarks/large-workspace.svg" />