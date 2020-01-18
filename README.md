Humble.js is a web framework built on modern technology stack with speed, security and scalability in mind.

The project was started in 2018 by [Amrayn Web Services](https://amrayn.com). It is currently active and maintained by the same company. The project was bootstrapped with CRA, thanks to the CRA team.

Help make the project open source by donating:

[![Donate](https://ghdl.amrayn.com/donate.png?v2)](https://amrayn.com/donate)

## features

Humble.js comes with a lot of features out of the box, some of them are listed below:

* Generic codebase to fit in to more or less any project
* Server side rendering
* Semi-automatic code splitting
* Load balancing using system CPU <sup>^</sup>
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
* "Components development framework" to develop the components without needing the server
* A lot of built-in automated tasks (based on task automation framework), e.g, email composition, database backup, sitemap generation. You can enable or disable them with simple steps.
* Built-in session management <sup>^</sup>

<sup>^</sup> This feature is deprecated and will be removed in version 2 for a better replacement.

## future

We're actively working on this project to make it robust and match today's standard. Current version of humble.js is monolithic architecture. Version 2 (which is being developed as you read this) has adapted microservices architecture. We're excited about this change and already seeing great improvements for devops. Next major version of the framework is coming with:

* Containerized framework
* Multiple services and cron jobs architecture for scalability
* Built-in orchestration with pre-configured configurations
* Easy to adapt built-in microservice framework that you can use to create your own custom microservices and interact with it with ease.
* A lot of built-in microservices (on top of existing ones like database back), some of them are listed below:
  - Storage service that is used to upload, maintain and access static files. You can upload files from other services or from frontend
  - Sitemap generator with user's specifications
  - Auth service to manage all the authentication stuffs at single place

We're not keeping backward compatibility as a lot of things have been moved, changed and renamed for betterment and maintainability.

We at Amrayn Web Services use humble.js in all our Node.js projects. We want speed, security and scalability out of the box as much as you do. Please consider donating to the project and help it make open source.

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

 * [context](/pkg/context) (v 1.8.23)
 * [core](/pkg/core) (v 1.3.125)
 * [data-provider](/pkg/data-provider) (v 1.1.15)
 * [demo](/pkg/demo) (v 2.1.23)
 * [link](/pkg/link) (v 1.8.23)
 * [page](/pkg/page) (v 1.8.23)
 * [theme](/pkg/theme) (v 1.0.15)

### utils
Various utility packages to aid the development.

 * [infinite](/pkg/infinite) (v 1.1.23)
 * [lib](/pkg/lib) (v 1.9.9)
 * [paypal-button](/pkg/paypal-button) (v 1.8.26)
 * [shopping-cart](/pkg/shopping-cart) (v 1.8.23)

### ui
Custom UI packages. You can completely ignore them if you want to use something else.

 * [breadcrumbs](/pkg/breadcrumbs) (v 1.9.23)
 * [form](/pkg/form) (v 1.8.23)
 * [icon](/pkg/icon) (v 1.9.16)
 * [img](/pkg/img) (v 1.8.24)
 * [menu](/pkg/menu) (v 1.1.23)
 * [modal](/pkg/modal) (v 1.2.24)
 * [pending](/pkg/pending) (v 1.1.23)
 * [share](/pkg/share) (v 1.8.23)
 * [skeleton](/pkg/skeleton) (v 1.8.23)
 * [spinner](/pkg/spinner) (v 1.8.23)

### pages
Pre-build page components that are shared across and can be used in your project. Some of these pages come with humble.js server.

 * [pa-config](/pkg/pa-config) (v 1.1.132)
 * [pa-error](/pkg/pa-error) (v 1.1.23)
 * [pa-reset-pwd](/pkg/pa-reset-pwd) (v 1.1.23)
 * [pa-signin](/pkg/pa-signin) (v 1.1.25)
 * [pa-static](/pkg/pa-static) (v 1.1.23)
 * [pa-view-email](/pkg/pa-view-email) (v 1.1.23)
