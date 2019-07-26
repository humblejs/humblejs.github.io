<p align="center">
  <a href="/docs/getting-started">← Getting Started</a>
</p>

## Basics Concepts

Humble.js uses express and react-router library underneath for routing and server. For you, all the details are abstract and you are only required to provide simple JSON
to serve the pages and process API requests.

Humble.js has 2 main components

 * Front-end components (pages) - humble.js works with your existing pages
 * Controllers - these are middleware that are used with each route.

## Global Variables
A part from Node's default, humble.js has some helpful global read-only variables that can be accessed from anywhere in the application.

| *Variable Name* | *Description* |
|---|---|
| `logger` | Logger based on [winston logging](https://github.com/winstonjs/winston) |
| `cfg`    | Configuration data for the application (managed in database table called `ConfigData`) - The configurations are updated every 15 minutes - This value can be changed in `core/__constants.js`. Anything specific in `KEY_NAME` column of the table is accessed as is. For example, if you have `VERSION`, you can access it at anytime by `cfg.VERSION` |
| `deploymentCfg` | Deployment configuration if you need it, it contains deployment information, e.g, `deploymentCfg.SCOPE` |

Global variables can be dangerous (thread-safety issues) and also can cause memory problems (memory leaks if not used properly). It is not recommended to define new global variables unless you absolutely need them.

## Modelling
All the database tables are modelled automatically to javascript objects using `models/__model.js` and `models/__base.js`. For example, if you have a table called `Client`, a typical model class will look like:

```javascript
import { Model, STATUS } from '~/models';

const TABLE_NAME = 'Client';

const QUERIES = {
  QUERY_BY_EMAIL: 'SELECT * FROM Client WHERE email = ? AND status = ?',
};

const hasFlag = (record, flag) => record && (record.flag & flag) === flag;

const FUNCTIONS = [
  hasFlag,
];

const model = Model({
  TABLE_NAME,
  QUERIES,
  FUNCTIONS,
});

const queryByEmail = ({ email }) => (model.querySingleObject(QUERIES.QUERY_BY_EMAIL, [ // or use model.query if you expect query to return multiple objects
  email, STATUS.ACTIVE,
]));

export default {
  ...model,
  queryByEmail,
  hasFlag,
};
```

Now when you query the database, you simply do:

```javascript
import Client from '~/models/client';

...
Client.queryByEmail({ email: 'blah@example.com' }).then((client) => {
  const correct = client.hasFlag(Flags.IS_CORRECTED); // notice single parameter only
});

// -- or you can use Client.hasFlag(myClient, Flags.IS_CORRECTED)
```

#### Default Functions

`model()` pre-defines some basic queries and corresponding functions

|*Function*|*Description*|
|---|---|
| `queryAllActive()` | Queries all the active records |
| `queryById({ id })` | Queries record by ID |
| `queryByIds({ ids })` | Query records by IDs, expects `ids` to be array of numbers |
| `queryByPublicId({ publicId })` | Queries single record by public ID. Public ID is a random string associated with the record. Similar to ID |

If you have an empty object and you want to convert it in to a model

```javascript
const newClient = Client.createNew({ name: 'blah', email: 'blah@example.com', flag: 4 }); // or Client.convertObject which is an alias to createNew

// -- now you can simply insert the record to the database
// -- or update existing records

newClient.insert().then(() => {
  console.log('Record successfully inserted');
});

```

#### Database Functions

Default database functions are very handy

|*Function*|*Description*|
|---|---|
| `insert()` | Inserts current object in to the database |
| `update()` | Update the current object |
| `del()` | Deletes the record from the database |


```javascript
import Client from '~/models/client';

const deleteClient = async (email) => {
  const client = await Client.queryByEmail({ email: 'blah@example.com' });
  if (client) {
    await client.del();
  }
}
```

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

#### Page Templates
`__page.ejs` is default template and you can use custom page template by specifying config data `PAGE_TEMPLATE` which will be picked up from `templates` directory.

#### Email Templates
`templates/__emails/` is default source for the templates, but you can specify custom source directory in config data `EMAIL_TEMPLATE_DIR`.

#### Error Templates
`templates/__errors` is default source for the templates. You can override this in config data `ERROR_TEMPLATE_DIR`.

`templates/__errors/__generic.ejs` is catch-all for all the errors. You can override catch-all with config data `EMAIL_TEMPLATE` which will be picked up from `templates/__errors` (or `ERROR_TEMPLATE_DIR` if available)

You can add HTTP status codes templates for each type of error templates. For example, if you want custom error page for error 503, you will need to create `templates/__errors/503.ejs`

## Automated Tasks
Humble.js comes with task automation framework which helps you run frequent tasks by simply scheduling them. All the tasks are defined in `crons` directory.

A task is a simple class that has a run function that returns promise.

```javascript
export default class MyNewTask {
  constructor() {
    this.name = this.constructor.name;
  }

  async run() {
    const result = { };

    return result;
  }
}

```

To run this task manually for development, simply do `yarn runjob my-new-task --mock`

`--mock` will ignore checking of the database entry in `Cron` table and will always run.

Once the task is ready for production, simply add an entry in `Cron` with preferred `schedule` and `run_type`. `run_type` tells Humble.js whether to run the task from within running application or register it as linux cron.

If you want to manually run the task, simply do `yarn runjob <task name>`.
