# Core
Core packages shared between humblejs server and client

A lot of these packages are used in the server and can be shared in micro services.

## Install

```
yarn add @humblejs/core
```

## Modules

* `AppProvider` (`app-provider.js`)
  * `appContext`
* `AuthProvider` (`auth-provider.js`)
  * `withAuth`
* `CronBase` (`cron.js`)
* `Logger` (`logger.js`)
* `PageDefinitions` (`pagedef.js`)
* `snooze()` (`snooze.js`)
* `PasswordUtils` (`password.js`)
* `Microservice` (`microservice.js`)
  * `MicroserviceMessageBus`
* `Model` (`model.js`)
* `DatabaseManager` (`db.js`)
