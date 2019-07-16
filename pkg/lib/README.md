# Lib
Common utils library

## Install

```
yarn add @humblejs/lib
```

## Style

Following styles must be imported for all the components

```
@import '@humblejs/lib/dist/css/global.scss';
@import '@humblejs/lib/dist/css/themes/default.scss';
```

Other available files

 * `@humblejs/lib/dist/css/reset.scss`
 * `@humblejs/lib/dist/css/toc.scss` (table of contents)

## Usage
Import complete library

```
import lib from '@humblejs/lib';
```

Import specific function or module

```
import { logger } from '@humblejs/lib';
```

or you can import from direct location like:

```
import logger from '@humblejs/lib/dist/js/logger';
```

## Modules

| *Name* | *Direct import* |
|--------|-------------------|
| `logger` ~> `{ info, debug, error, warn }` ,`{ isLoggingEnabled }` | `dist/js/logger` |
| `Analytics` ~> `{ sendEvent, reset, pageview }` | `dist/js/ga` |
| `{ generateToc, addPermaLinkToHeaders }` | `dist/js/toc` |
| `{ isBrowser, isIE }` | `dist/js/browser` |
| `registerScrollCallback, { isElementInViewport }` | `dist/js/register-scroll-callback` |
| `addListener(elem, evt, fn), { addEventListener }` | `dist/js/event/add-listener` |
| `removeListener(elem, evt, fn)` | `dist/js/event/remove-listener` |


### `logger`
Enable/disable `console` logging. Configuration is based on `localStorage`

### `ga`
Google analytics wrapper

### `toc`
Table of contents generator

### `browser`
Browser related utility functions

### `register-scroll-callback`
Register callback when user scrolls the page

`registerScrollCallback` takes options with `callback` (fn) and `scrollRefId` 
(element ID) so when `scrollRefId` is in view (or passed the point) `callback` 
is triggered.

e.g,

```
window.onload = function() {
  registerScrollCallback({
    scrollRefId: 'menu-bar',
    callback: () => {
      console.log('Just past the menu bar');
    },
  });
}
```