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
| `humblejs new` (Global) | Create new server application based on humble.js |
| `humblejs build-ui` (UI) | Builds UI service for production |
| `humblejs analyze` (UI) | Analyze bundles to see possibilities to reduce the application size|

## Other commands
Here are other list of commands you would run from root directory

| Command | Description |
|-----------|----------------|
| `yarn deploy` | Deploys the stack as defined in humble.js config file |
| `yarn build-for` | Builds images for specific stack e.g, `yarn build-for default` will build humble.js config file → `deployments` → `default` |
| `yarn push-for` | Push images to container registry for specific stack. See `build-for` above for details |
| `yarn up-for` | Helps you start stack using `docker-compose` |
| `yarn build` | Alias for `yarn build-for default` |
| `yarn push` | Alias for `yarn push-for default` |
| `yarn runjob <name> [<args...>]` | Manually run automated task from `crons` directory. It uses `docker exec` to trigger the job |
| `yarn new:svc <name>` | Create new microservice from template |
| `yarn new:cron <name>` | Create new cron from template |
| `yarn humblejs:update` | Update the framework based off origin |
| `yarn reset` | **Hard Resets** any changes and refresh version of your code to match the remote |
| `yarn pkg:update` | Updates all the packages for your scope (humble.js config file → `scope`) |
