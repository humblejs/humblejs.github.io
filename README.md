Humble.js is a web framework built on modern technology stack with speed, security and scalability in mind.

The project was started in 2018 by [Amrayn Web Services](https://amrayn.com). It is currently active and maintained by the same company. The project was bootstrapped with CRA, thanks to the CRA team.

## features

Humble.js comes with a lot of features out of the box, some of them are listed below:

(The keyword before semicolon represent the type of microservice (e.g, `ui:` is User Interface service))

* Containerized framework
* Multiple services and cron jobs architecture for scalability
* Built-in orchestration configuration (swarm or k8s) with pre-configured yaml files to get started
* Generic codebase designed to fit any project whether small or huge.
* Adaptive built-in microservice framework that you can use to create your own custom microservices and interact with it with ease.
* ui: Server side rendering
* ui: Semi-automatic code splitting
* ui: PWA-ready with service worker and customisable URLs
* RESTful API framework included
* Database framework: schema management, modelling and querying, all built-in!
* cronmaster: Task automation framework
* ui: SEO and social media optimised pages
* ui: Built-in structured data meta information
* Use your own components with zero-config
* ui: Uses webpack dev server hot deployment to speed-up the development of UI
* ui: Humble.js's react components for consistent UI and UX (see list of [packages](/#packages) below) - there are no restrictions
* Easy upgrade to your implementation to latest version of _Humble.js server_
* ui: CSS preprocessor using Sass (does support _emotion_ as well out of the box)
* Security features against fast malicious systems and software
* Vulnerabilities patches as soon as they are discovered in web standards
* Components development framework to develop the components without needing the server
* A lot of built-in automated tasks (based on task automation framework), e.g, email composition, database backup. You can enable or disable them with simple steps.
* auth:
* A lot of built-in microservices (on top of existing ones like database backup), some of them are listed below:
  - static: Storage service that is used to upload, maintain and access static files. You can upload files from other services or from frontend
  - cron-sitemap-generator: Sitemap generator with user's specifications
  - cron-database-backup: Backups and restore database (or selected tables) and secure the backups with strong encryption
  - auth: Manage user's identity with built-in service

We at Amrayn Web Services use humble.js in all our Node.js projects. We want speed, security and scalability out of the box as much as you do.

## server

current version 2.0.4-beta

Humble.js v1.70.2 is current stable non-beta release. It used monolithic architecture and it will be replaced with v2.0.0 once it is stable.

Humble.js server is the core of Humble.js that incorporates all the components and serve them accordingly.

[Click here](/server) for more details

## cli

Humble.js CLI for your `package.json`. It comes in two flavours:

* `@humblejs/scripts` (v 1.9.11)
* `@humblejs/server` (v 1.10.33)

[Click here](/cli) for more details

## packages
Humble.js comes with various category of packages

### essentials
These packages go hand-in-hand with humble.js server and client pages. These are useful to speed-up the development and data accessibility.

 * [context](/pkg/context) (v 1.8.25)
 * [core](/pkg/core) (v 1.3.178)
 * [data-provider](/pkg/data-provider) (v 1.1.17)
 * [demo](/pkg/demo) (v 2.1.25)
 * [link](/pkg/link) (v 1.8.25)
 * [page](/pkg/page) (v 1.8.25)
 * [theme](/pkg/theme) (v 1.0.17)

### utils
Various utility packages to aid the development.

 * [infinite](/pkg/infinite) (v 1.1.25)
 * [lib](/pkg/lib) (v 1.9.11)
 * [paypal-button](/pkg/paypal-button) (v 1.8.28)
 * [shopping-cart](/pkg/shopping-cart) (v 1.8.25)

### ui
Custom UI packages. You can completely ignore them if you want to use something else.

 * [breadcrumbs](/pkg/breadcrumbs) (v 1.9.25)
 * [form](/pkg/form) (v 1.8.25)
 * [icon](/pkg/icon) (v 1.9.18)
 * [img](/pkg/img) (v 1.8.26)
 * [menu](/pkg/menu) (v 1.1.28)
 * [modal](/pkg/modal) (v 1.2.26)
 * [pending](/pkg/pending) (v 1.1.25)
 * [share](/pkg/share) (v 1.8.25)
 * [skeleton](/pkg/skeleton) (v 1.8.25)
 * [spinner](/pkg/spinner) (v 1.8.25)

### pages
Pre-build page components that are shared across and can be used in your project. Some of these pages come with humble.js server.

 * [pa-config](/pkg/pa-config) (v 1.1.185)
 * [pa-error](/pkg/pa-error) (v 1.1.25)
 * [pa-reset-pwd](/pkg/pa-reset-pwd) (v 1.1.25)
 * [pa-signin](/pkg/pa-signin) (v 1.1.29)
 * [pa-static](/pkg/pa-static) (v 1.1.25)
 * [pa-view-email](/pkg/pa-view-email) (v 1.1.25)
