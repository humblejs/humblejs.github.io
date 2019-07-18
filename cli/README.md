# CLI
Humble.js scripts come with CLI for your package.json.

## humblejs-pkg
CLI specific for a package. It is part of `@humblejs/scripts`

| Command | Description |
|-----------|----------------|
| `humblejs-pkg build` | Build production version of the component |
| `humblejs-pkg build:local` | Build production version of the demo for component |
| `humblejs-pkg start` | Start demo for the component with hot-loading |

Following commands are available but most of the times they are not needed by packages (they're used internally)

| Command | Description |
|-----------|----------------|
| `humblejs-pkg build:css` | Runs CSS pre-processor |
| `humblejs-pkg build:demo-css` | Runs CSS pre-processor for the component demo |
| `humblejs-pkg watch-css` | Watch any changes to the CSS files and immediately compile when a change is detected |

## humblejs-repo
CLI specific for package repository. It is part of `@humblejs/scripts`

| Command | Description |
|-----------|----------------|
| `humblejs-repo new --pkgdir=<packages dir> --scope=<scope> [--name=<name>]` | Create new package in the repository. If name is specified you will not be prompt to change the component name |
| `humblejs-repo build --pkgdir=<packages dir> --scope=<scope>` | Build packages from the directory with specified scope |
| `humblejs-repo install --scope=<scope>` | Install all the package node_modules from the specified directory |
| `humblejs-repo install:clean --pkgdir=<packages dir> --scope=<scope>` | Clean install all the package node_modules from the specified directory. Cleaning means removing `node_modules` and `yarn.lock` for each package before installing |
| `humblejs-repo push` | Pushes all the changed packages to the registry |


## humblejs (server)
CLI specific for humble.js server repository. It is part of `@humblejs/server`

| Command | Description |
|-----------|----------------|
| `humblejs build` | Builds application for production |
| `humblejs new` | Create new server application based on humble.js |
| `humblejs deploy` | Deploys the application to remote server specified in humble.js configuration file|
| `humblejs analyze` | Analyze bundles to see possibilities to reduce the application size|
