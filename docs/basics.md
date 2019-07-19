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

Humble.js routing are split in to two parts:
 * Page routes
 * API routes
 
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

The idea behind this JSON is, when user hits `/about`, the server triggers middleware from `about` which is essentially a javascript file `controllers/pages/about.js`.

`about.js`
```javascript
export default async (req, res, next) => {
  res.send('Hello from server')
}
```

After the last middleware, server puts everything together and passes in to `AboutPage` which is react page and hydrates the react DOM. In turn, user sees `Hello from server` message on their browser.

A typical `AboutPage` file will look like this:

```javascript
import { PageDefinition } from '@humblejs/core';

const Page = PageDefinition({
  component: () => import(/* webpackChunkName: "AboutPage" */ '@train/pa-about'),
  modules: ['About'],
});

Page.pkg = '@train/pa-about';

export default Page;
```

`PageDefinition` lazy loads the page and helps in code-splitting. `webpackChunkName` is a magic comment by webpack. Read more about [magic comments here](https://medium.com/faceyspacey/how-to-use-webpacks-new-magic-comment-feature-with-react-universal-component-ssr-a38fd3e296a)

### API Routes
API routes are defined in `routes/api` directory which are slightly different to page routes. An example of such route is

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

Notice `controllers` array, these are middleware in order. The last one should send the response. `hjs` in above example are just helper middleware, you can use your own if you want.

### Session Routes
Humble.js comes with default session management, which is based on express-session. You can override this by specifying custom routes in `routes/sess` directory. For most cases, the default session controllers are good enough.
