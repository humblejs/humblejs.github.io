<p align="center">
  <a href="/docs/getting-started">← Getting Started</a>
</p>

## Basics

Humble.js uses express and react-router library underneath for routing and server. For you, all the details are abstract and you are only required to provide simple JSON
to serve the pages and process API requests.

Humble.js has 2 main components

 * Front-end components (pages) - preferably using `@humblejs/page` but can work with existing pages
 * Controllers - these are middleware that are used with each route.
 
## Routing

Humble.js routing are split in to three parts:
 * API Routes
 * Session Routes
 * Page Routes


### API Routes
API routes are defined in `routes/api` directory. An example of such route is

```javascript
import SigninController from '~/controllers/api/signin';
import * as hjs from '~/core/__middleware'; // Humble.js defined helper middleware
export default [
  {
    path: '/api/v1/signin',
    method: 'POST',
    controllers: [
      hjs.json, // set response type to JSON
      hjs.noCache, // never cache this
      SigninController,
    ],
  },
];
```

Notice `controllers` array, these are middleware in order. The last one should send the response. `hjs` in above example are just helpers middleware, you can use your own if you want.

### Session Routes
Humble.js comes with default session management, which is based on express-session. You can override this by specifying custom routes in `routes/sess` directory. For most cases, the default session controllers are good enough.


### Page Routes
Page routes are defined in `client/routes` directory which are then compiled. These definitions are simple JSON based and no controller information is available here.


An example of most simple route is:
```javascript
import AboutPage from '~/client/pages/About';

export default [
  {
    path: '/about',
    component: AboutPage,
    controllerId: 'about',
  },
];
```

## Controllers
The idea behind above JSON (page route) is, when user hits `/about`, the server triggers middleware from `about` which is essentially a javascript file `controllers/pages/about.js`.

```javascript
import done from './__final';

export default async (req, res, next) => {
  done({
    req,
    next,
    props: {
      message: 'Hello from server',
    },
  });
}
```

Controllers are considered last middleware before `done` is called. Server then puts everything together and passes in to `AboutPage` which is react page and hydrates the react DOM. In turn, user sees `Hello from server` message on their browser.

`done()` function takes other inputs as well:

|*Field*|*Description*|
|---|---|
| `req` | Request object straight from current middleware |
| `next` | `next()` function straight from current middleware |
| `page` | Page controller (`page.js`) is customisable middleware that you can use as basis for every page. `done()` puts everything from `page` object to props |
| `props` | The props for the page component |
| `meta` | Meta object supported by [`@humblejs/page`](/pkg/page/) |
| `token` | Any custom JWT token. Typically you will do this in `page.js` but if you want a custom token for this particular page, you can define it here |
| `header` | Props specifically for header component of the page |
| `footer` | Props specifically for footer component of the page |
| `breadcrumbs` | Breadcrumbs for the page, typically passed in to [`@humblejs/breadcrumbs`](/pkg/breadcrumbs/) component |
| `structuredData` | Any custom structured data for the page. This is appended to the default one |
| `cid` | Controller ID for the page, this is auto-generated but if you want to override this for any reason, you can do it by specifying here. Controller ID is file path from `controllers/pages/...` onwards. For example, if you have a file `controllers/pages/admin/find-users.js`, the controller ID is `admin/find-users` by default. |

## React Pages

A typical `AboutPage` file will look like this:

```javascript
import { PageDefinition } from '@humblejs/core';

export default PageDefinition({
  name: 'About',
  importer: () => import(/* webpackChunkName: "About" */ '@train/pa-about'),
  pkg: '@train/pa-about',
});
```

`PageDefinition` lazy loads the page and helps in code-splitting. `webpackChunkName` is a magic comment by webpack. Read more about [magic comments here](https://medium.com/faceyspacey/how-to-use-webpacks-new-magic-comment-feature-with-react-universal-component-ssr-a38fd3e296a)

## Code Splitting
Code splitting is done automatically for each pages, typically coming from `importer()` in `PageDefinition`. This is because Humble.js uses [`webpack`](https://webpack.js.org/) for bundling.

## Templates
Templates define the bare bones of any page or email. They're found in `templates` directory. Humble.js uses EJS templates.

### Page Templates
`__page.ejs` is default template and you can use custom page template by specifying config data `PAGE_TEMPLATE` which will be picked up from `templates` directory.

### Email Templates
`templates/__emails/` is default source for the templates, but you can specify custom source directory in config data `EMAIL_TEMPLATE_DIR`.

### Error Templates
`templates/__errors` is default source for the templates. You can override this in config data `ERROR_TEMPLATE_DIR`.

`templates/__errors/__generic.ejs` is catch-all for all the errors. You can override catch-all with config data `EMAIL_TEMPLATE` which will be picked up from `templates/__errors` (or `ERROR_TEMPLATE_DIR` if available)

You can add HTTP status codes templates for each type of error templates. For example, if you want custom error page for error 503, you will need to create `templates/__errors/503.ejs`.