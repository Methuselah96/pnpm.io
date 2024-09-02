# Benchmarks of JavaScript Package Managers

**Last benchmarked at**: _Sep 2, 2024, 3:41 AM_ (_daily_ updated).

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

## Redux Devtools

The app's `package.json` [here](https://github.com/pnpm/pnpm.io/blob/main/benchmarks/fixtures/redux-devtools/package.json)

| action  | cache | lockfile | node_modules| npm | pnpm | Yarn | Yarn PnP |
| ---     | ---   | ---      | ---         | --- | ---  | ---  | ---      |
| install |       |          |             | 1m 37.6s | 25.7s | 12.5s | 4.7s |
| install | ✔     | ✔        | ✔           | 1.7s | 1.2s | 1.8s | n/a |
| install | ✔     | ✔        |             | 12.6s | 6.7s | 8.6s | 1.4s |
| install | ✔     |          |             | 23.9s | 14.1s | 11s | 3.5s |
| install |       | ✔        |             | 17.2s | 17.2s | 8.2s | 1.3s |
| install | ✔     |          | ✔           | 2s | 3.4s | 3.7s | n/a |
| install |       | ✔        | ✔           | 1.6s | 1.1s | 1.6s | n/a |
| install |       |          | ✔           | 1.9s | 15.7s | 3.7s | n/a |
| update  | n/a | n/a | n/a | 15.9s | 6s | 6.5s | 4.1s |

<img alt="Graph of the redux-devtools results" src="/img/benchmarks/redux-devtools.svg" />