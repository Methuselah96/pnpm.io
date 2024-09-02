# Benchmarks of JavaScript Package Managers

**Last benchmarked at**: _Sep 2, 2024, 10:46 PM_ (_daily_ updated).

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
| install |       |          |             | 1m 17.9s | 30.3s | 15.8s | 4.4s |
| install | ✔     | ✔        | ✔           | 1.5s | 1s | 1.6s | n/a |
| install | ✔     | ✔        |             | 13.2s | 10.2s | 11.6s | 1.3s |
| install | ✔     |          |             | 22.4s | 18.1s | 14.3s | 3.1s |
| install |       | ✔        |             | 17.9s | 22.7s | 12.1s | 1.3s |
| install | ✔     |          | ✔           | 1.8s | 6.3s | 3.7s | n/a |
| install |       | ✔        | ✔           | 1.9s | 998ms | 1.4s | n/a |
| install |       |          | ✔           | 1.7s | 18.4s | 3.3s | n/a |
| update  | n/a | n/a | n/a | 19.8s | 8.3s | 2m 25.6s | 3.6s |

<img alt="Graph of the large-workspace results" src="/img/benchmarks/large-workspace.svg" />