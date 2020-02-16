# Core
Core packages shared between humblejs server and client

A lot of these packages are used in the server and can be shared in micro services.

## Install

```
yarn add @humblejs/core
```

## Modules

* `AppProvider` (`app-provider.js`) - HOC for application (root of application that contains all the information including auth)
  * `appContext` - Consumer for AppProvider
* `AuthProvider` (`auth-provider.js`) - HOC for auth related stuff
  * `withAuth` - Consumer for AuthProvider
* `CronBase` (`cron.js`)
* `Logger` (`logger.js`)
* `EnvUtils` (`load-env.js`) - Load and override any environment variables from various places with priority.
* `PageDefinitions` (`pagedef.js`)
* `snooze()` (`snooze.js`)
* `PasswordUtils` (`password.js`)
* `Microservice` (`microservice.js`) - Microservice class that is used to register all the service mini-functions
  * `MicroserviceMessageBus` - Microservice channel bus responsible to talk to microservice (using HTTP protocol)
  * `createChannels` - utility to create microservice channel bus.
* `Model` (`model.js`) - Core of any database model that automatically provide ability to CRUD the record.
* `DatabaseManager` (`db.js`) - The core of database manager providing utility functions to query and update/insert/delete. You should not need this if you use `Model` as it is wrapped in it.
