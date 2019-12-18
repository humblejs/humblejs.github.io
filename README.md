Humble.js is a web framework built on modern technology stack with speed, security and scalability in mind.

The project was started in 2018 by [Amrayn Web Services](https://amrayn.com). It is currently active and maintained by the same company. The project was bootstrapped with CRA, thanks to the CRA team.

Help make the project open source by donating:

[![Donate](https://ghdl.amrayn.com/donate.png?v2)](https://amrayn.com/donate)

## features

Humble.js comes with a lot of features out of the box, some of them are listed below:

* Generic codebase to fit in to any project
* Server side rendering
* Semi-automatic code splitting
* Load balancing using system CPU
* PWA-ready with service worker and customisable URLs
* RESTful API framework included
* Database framework: schema management, modelling and querying, all built-in!
* Task automation framework
* SEO and social media optimised pages
* Built-in structured data meta information
* Use your own components with zero-config
* Uses webpack dev server hot deployment to speed-up the development of UI
* Humble.js's react components for consistent UI and UX (see list of [packages](/#packages) below) - there are no restrictions
* Easy upgrade to your implementation to latest version of _Humble.js server_
* CSS preprocessor using Sass (does support _emotion_ as well out of the box)
* Security features against fast malicious systems and software
* Vulnerabilities patches as soon as they are discovered in web standards
* Components development framework to develop the components without needing the server
* A lot of built-in automated tasks (based on task automation framework), e.g, email composition, database backup, sitemap generation. You can enable or disable them with simple steps.
* Built-in session management

## future

We're actively working on this project to make it robust and match today's standard. Current version of humble.js has monolithic architecture. Version 2 (which is being developed as you read this) of the framework has adapted microservices architecture. We're excited about this change and already seeing great improvements. Next major version of the framework is coming with:

* Fully containerized framework
* Split services and cron jobs in to many manageable microservices
* Migrating to kubernetes with pre-configured yaml configurations
* Separate identity server

Even though it is a major version, we're still keeping backward compatibility as much as possible. This is to minimize efforts to migrate existing projects.

We at Amrayn Web Services use humble.js in all our Node.js projects. We want speed, security and scalability out of the box as much as you do. Please consider donating to the project so we can make this project open source.

## server

current version 1.70.2

Humble.js server is the core of Humble.js that incorporates all the components and serve them accordingly.

[Click here](/server) for more details

## cli

Humble.js CLI for your `package.json`. It comes in two flavours:

* `@humblejs/scripts` (v 1.9.9)
* `@humblejs/server` (v 1.10.33)

[Click here](/cli) for more details

## packages
Humble.js comes with various category of packages

### essentials
These packages go hand-in-hand with humble.js server and client pages. These are useful to speed-up the development and data accessibility.

 * [context](/pkg/context) (v 1.8.22)
 * [core](/pkg/core) (v 1.3.36)
 * [data-provider](/pkg/data-provider) (v 1.1.14)
 * [demo](/pkg/demo) (v 2.1.22)
 * [link](/pkg/link) (v 1.8.22)
 * [page](/pkg/page) (v 1.8.22)
 * [theme](/pkg/theme) (v 1.0.14)

### utils
Various utility packages to aid the development.

 * [infinite](/pkg/infinite) (v 1.1.22)
 * [lib](/pkg/lib) (v 1.9.8)
 * [paypal-button](/pkg/paypal-button) (v 1.8.25)
 * [shopping-cart](/pkg/shopping-cart) (v 1.8.22)

### ui
Custom UI packages. You can completely ignore them if you want to use something else.

 * [breadcrumbs](/pkg/breadcrumbs) (v 1.9.22)
 * [form](/pkg/form) (v 1.8.22)
 * [icon](/pkg/icon) (v 1.9.15)
 * [img](/pkg/img) (v 1.8.23)
 * [menu](/pkg/menu) (v 1.1.22)
 * [modal](/pkg/modal) (v 1.2.23)
 * [pending](/pkg/pending) (v 1.1.22)
 * [share](/pkg/share) (v 1.8.22)
 * [skeleton](/pkg/skeleton) (v 1.8.22)
 * [spinner](/pkg/spinner) (v 1.8.22)

### pages
Pre-build page components that are shared across and can be used in your project. Some of these pages come with humble.js server.

 * [pa-config](/pkg/pa-config) (v 1.1.43)
 * [pa-error](/pkg/pa-error) (v 1.1.22)
 * [pa-reset-pwd](/pkg/pa-reset-pwd) (v 1.1.22)
 * [pa-signin](/pkg/pa-signin) (v 1.1.22)
 * [pa-static](/pkg/pa-static) (v 1.1.22)
 * [pa-view-email](/pkg/pa-view-email) (v 1.1.22)
