# Server
This page introduces you to the **humble.js server** which is the core of humble framework.

## Introduction

1. Humble.js is a **complete** back-to-front web server powered by most popular libraries. These libraries are used internally and developers are not bound to any libraries (see scalibility below). They only needs to map the components/pages to routes (via simple JSON format). Humble.js comes with built-in frameworks for RESTful api, database and task automation. You can use your pre-existing react components or create your own one with humble.js's frontend framework (using [`humblejs-repo`](/cli#humblejs-repo) CLI) to speed up the development.
2. Your humble.js app will be a fork of latest humble.js source (managed with git) and is easily upgradable with minimal or no conflict. As long as you don't change files starting with `__` you should be able to smoothly update to latest version of humble.js simply by doing `yarn humblejs:update` from the root.
3. humble.js comes with built-in database support (`mysql` by default) and provides you features to query the records without having to write your schema etc. This also means SQL injection prevention without having to worry about it.
4. Most importantly, humble.js is not just react framework, it is end-to-end web framework for your website that uses react for the frontend.

Humble.js is focused on isomorphic javascript development, helping you make it all with javascript, from database layer to api to frontend rendering and styling.

Hopefully, soon there will be a fully working demo up and running where you will be able to experience a lot of humble.js's built-in features.

## Development
Smooth development is one of the main reasons why you would want to use it instead of writing your own. Humble.js follows a specific pattern that makes your application highly efficient for development across many teams.

* Frontend components are separately built and tested - they do not have to have server running, humble.js comes with framework to run your components against fixtures. This framework also allows you to make fake `fetch` calls with mocked responses.
* Components that are ready can be integrated to the server and you will have routes mapping for the component and handlers behind it (we call them `controllers`) which will generate props for the component.
* Humble.js's special handler then takes the props and automatically serve them with server rendered
* Developers can fully control the controllers and there is no magic happening. Controllers are simple express.js middleware `req, res, next`
* Developers do not have to worry about changing that one little colour in the colour pallette of theme, all they need to change is one of the frontend components (usually named `@yourapp/theme`) and the changes will be immediately visible in the component demo and can easily be updated on server by simply re-generating `yarn.lock`.
* With humble.js, navigating through pages are very light on network, it only updates props for the component (and updates styling etc.). This is all done automatically, as long as you use `@humble.js/link` for all your links in frontend components (similar to `<a>`). You do not need to do anything special for this, no need to use special library or inject a script.

With release of version 2, the development is even easier. Each service is in it's own directory/package and does not depend on one another. The only time it depends is when they actually need to talk to each other, but that's mostly the last step because you would use RESTful client to test your package (unless you take TDD approach which we highly recommend).

## Debugging
Humble.js comes with debugging support

* Frontend packages can be debugged using dev tools like `firebug` or `Chrome Dev Tools`
* Backend (server) debugging is also supported with `--inspect` flag
* Debugging frontend packages (javascript or sass files) that are integrated with server, is in experimental stage and not very reliable as of current version.

## Config

`humble.config.js` is the base file for your project's humble.js implementation. This is javascript file instead of plain json file. This gives you flexibility of using external `dev` packages.

| *Config Name* | *Description* |
|---------------|---------------|
| `scope`       | Packages scope for your project. This is used when creating new packages, upgrading the packages and while building |
| `version`     | Version of your app. You wouldn't change `package.json`'s version, as that is specific for the humble.js's (the server framework) version |
| `remote`      | Object that specifies the remote config. `name`, `user`, `host`, `port`, `dest`, `privateKey` and `keep` are the possible properties of this object. This is used with [`@humblejs/server` deployment process](/cli/#humblejs-server) |
| `serviceWorker` | Configuration related to service worker and progress web app. `enabled`, `cacheControllers` and `cacheUrls` |
| `pageMapping` | Page to package mapping for custom pages. For example, if some of the pages do not use packages from `scope`, you can specify here. |
| `disabledApi` | You can disable any humble.js built-in API by adding the identifier here. For example `['USERS.SIGNUP']` will disable signup API, `['USERS']` will disable all the user related API (`signin`, `signup` etc) |

#### Sample file

```javascript
module.exports = {
  scope: 'sample', //  allows packages like @sample/pa-homepage
  version: '1.0.0', // your app version

  deployments: {
    default: {
      port: 3080,
      cronmasterPort: 9000,
      pmaPort: 3084,
      stack: [
        '__docker-stack.yml',
        '__docker-stack-crons.yml',
        '__docker-stack.prod.yml',
      ],
    },
  },

  // any custom mapping for your components that do not use humble.js's
  // defined format (i.e, @SCOPE/pa-<PAGE_NAME>)
  pageMapping: {
    Homepage: 'fe-pa-homepage',
  },

  // Any API you want to disable (that come default with humble.js)
  disabledApi: [

  ],

  serviceWorker: {
    enabled: false,
    cacheControllers: [
      // list of controllers to cache by service worker
      { url: '/', controllerId: 'homepage' },
      { url: '/about', controllerId: 'about' },
    ],
    cacheUrls: [
      // list of urls to cache by service worker
    ],
  },
};

```
