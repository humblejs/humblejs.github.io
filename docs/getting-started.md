[Basics →](/docs/basics)

## Getting Started

**You will need to make sure you have access to humblejs private registry and humblejs git repo**

1. Clone the git repo for the server
```
git clone <path/to/git/repo/humble.js.git>
```
2. Make sure all the required scripts are up to date
```
yarn global add @humblejs/server --latest
yarn global add @humblejs/scripts --latest
```
2. Create new project
```
humblejs new
```

After this you will be asked series of questions. For example you are creating a project for your client named `Train Builders` you can have following answers to make things easier to follow later

|*Question*|*Description*|*Possible Answer*|
|---|---|---|
|Project name|Name of the project folder|`train-builders`|
|Project scope|All the frontend packages will start with this scope|`train` means packages will be `@train/theme` or `@theme/homepage` etc|
|Humble.js repo|Path to git repo for rebasing and updating|`~/humble.js`|
|Git repo for the project|SSH git repo for the project where things will be pushed to. If you do not have one, leave this empty for now||

The process will then generate the whole project and first package called `theme`.
