# Benchmarks of JavaScript Package Managers

**Last benchmarked at**: _Sep 2, 2024, 3:51 AM_ (_daily_ updated).

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
| install |       |          |             | 1m 47.8s | 37.6s | 22.7s | 8.3s |
| install | ✔     | ✔        | ✔           | 4.1s | 3.1s | 3.9s | n/a |
| install | ✔     | ✔        |             | 33.2s | 15.9s | 16.8s | 3.1s |
| install | ✔     |          |             | 51.2s | 28s | 21.7s | 6.4s |
| install |       | ✔        |             | 40.5s | 24.9s | 17s | 3.1s |
| install | ✔     |          | ✔           | 5s | 7.6s | 7.2s | n/a |
| install |       | ✔        | ✔           | 4.2s | 3.1s | 3.8s | n/a |
| install |       |          | ✔           | 5s | 19.9s | 7.1s | n/a |
| update  | n/a | n/a | n/a | 24.1s | 12.1s | 11.8s | 7.6s |

<img alt="Graph of the redux-devtools results" src="/img/benchmarks/redux-devtools.svg" />