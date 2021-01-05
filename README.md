Humble.js is a web framework built on modern technology stack with speed, security and scalability in mind.

It initially began with monolithic architecture and it has moved to microservice architecture that enables developers to adapt any microservice pattern that works best for them. By default it uses "decomposition by business capability" architecture.

The project was started in 2018 by [Amrayn Web Services](https://amrayn.com).

## Features

Humble.js comes with a lot of features out of the box, some of them are listed below:

### Core

* Containerized framework
* Multiple services and cron jobs architecture for scalability
* Built-in orchestration configuration (swarm or k8s) with pre-configured yaml files to get started
* Generic codebase designed to fit any project whether small or huge.
* Adaptive built-in microservice framework that you can use to create your own custom microservices and interact with it with ease.
* RESTful API framework included
* Database framework with schema management, modelling and querying, all built-in!
* Task automation framework
* Use your own components with zero-config
* Easy upgrade to your implementation to latest version of _Humble.js server_
* Security features against fast malicious systems and software
* Vulnerabilities patches as soon as they are discovered in web standards
* Components development framework to develop the components without needing the server
* A lot of built-in automated tasks (based on task automation framework), e.g, email composition, database backup. You can enable or disable them with simple steps.

### UI Microservice
  * Server side rendering
  * Semi-automatic code splitting
  * PWA-ready with service worker and customisable URLs
  * SEO and social media optimised pages
  * Built-in structured data meta information
  * Uses webpack dev server hot deployment to speed-up the development of UI
  * Humble.js's react components for consistent UI and UX (see list of [packages](/#packages) below) - there are no restrictions
  * CSS preprocessor using Sass (does support _emotion_ as well out of the box)

### Default Services

A lot of built-in microservices (on top of existing ones like database backup), some of them are listed below:

  * static: Storage service that is used to upload, maintain and access static files. You can upload files from other services or from frontend
  * cron-sitemap-generator: Sitemap generator with user's specifications
  * cron-database-backup: Backups and restore database (or selected tables) and secure the backups with strong encryption
  * auth: Manage user's identity with built-in service
  * cfg: Manage application wide configuration accessible via all the services

We at Amrayn Web Services use this framework in all our Node.js projects. We want speed, security and scalability out of the box as much as you do.

## Server

Current version 2.0.5

`@humblejs/server` and `@humblejs/server2` is the core of Humble.js that incorporates all the components/services and utilise them accordingly.

[Click here](/server) for more details

## CLI

Humble.js CLI for your `package.json`. It comes in two flavours:

* `@humblejs/scripts` (v1.10.7)
* `@humblejs/server2` (v2.1.36)

[Click here](/cli) for more details

## Packages
Humble.js comes with various category of packages

### Essentials
These packages go hand-in-hand with humble.js server and client pages. These are useful to speed-up the development and data accessibility.

 * [context](/pkg/context) (v 1.9.6)
 * [core](/pkg/core) (v 1.4.23)
 * [data-provider](/pkg/data-provider) (v 1.2.6)
 * [demo](/pkg/demo) (v 2.2.6)
 * [link](/pkg/link) (v 1.9.6)
 * [page](/pkg/page) (v 1.9.6)
 * [theme](/pkg/theme) (v 1.1.6)

### Utils
Various utility packages to aid the development.

 * [infinite](/pkg/infinite) (v 1.2.6)
 * [lib](/pkg/lib) (v 1.10.6)
 * [paypal-button](/pkg/paypal-button) (v 1.9.6)
 * [shopping-cart](/pkg/shopping-cart) (v 1.9.6)

### UI
Custom UI packages. You can completely ignore them if you want to use something else.

 * [breadcrumbs](/pkg/breadcrumbs) (v 1.10.6)
 * [form](/pkg/form) (v 1.9.9)
 * [icon](/pkg/icon) (v 1.10.7)
 * [img](/pkg/img) (v 1.9.7)
 * [menu](/pkg/menu) (v 1.2.6)
 * [modal](/pkg/modal) (v 1.3.6)
 * [pending](/pkg/pending) (v 1.2.6)
 * [share](/pkg/share) (v 1.9.6)
 * [skeleton](/pkg/skeleton) (v 1.9.6)
 * [spinner](/pkg/spinner) (v 1.9.6)

### Pages
Pre-build page components that are shared across and can be used in your project. Some of these pages come with humble.js server.

 * [pa-config](/pkg/pa-config) (v 1.2.20)
 * [pa-error](/pkg/pa-error) (v 1.2.6)
 * [pa-reset-pwd](/pkg/pa-reset-pwd) (v 1.2.8)
 * [pa-signin](/pkg/pa-signin) (v 1.2.8)
 * [pa-static](/pkg/pa-static) (v 1.2.6)
 * [pa-view-email](/pkg/pa-view-email) (v 1.2.6)
