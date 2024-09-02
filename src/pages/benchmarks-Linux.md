# Benchmarks of JavaScript Package Managers

**Last benchmarked at**: _Sep 2, 2024, 3:40 AM_ (_daily_ updated).

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
| install |       |          |             | 1m 23.4s | 20.7s | 14.7s | 6.8s |
| install | ✔     | ✔        | ✔           | 3.7s | 2.2s | 3s | n/a |
| install | ✔     | ✔        |             | 17.5s | 4.6s | 10.2s | 2.6s |
| install | ✔     |          |             | 30.8s | 14.5s | 13.7s | 5.4s |
| install |       | ✔        |             | 24.9s | 10.1s | 10.4s | 2.6s |
| install | ✔     |          | ✔           | 3.6s | 5.4s | 6.1s | n/a |
| install |       | ✔        | ✔           | 2.9s | 2.1s | 3s | n/a |
| install |       |          | ✔           | 3.6s | 11.6s | 6.1s | n/a |
| update  | n/a | n/a | n/a | 19.4s | 8.2s | 7.4s | 6.4s |

<img alt="Graph of the redux-devtools results" src="/img/benchmarks/redux-devtools.svg" />