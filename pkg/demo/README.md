# Demo
Demo component for wrapping components with fixtures and media.

[Demo](https://humblejs.zuhd.org/pkg/demo/demo)

## Install

```
yarn add --dev @humblejs/demo
```

## Component
By default `humblejs-pkg new` integrates the demo component.

`<Demo>` component takes fixture group and fixtures for each group containing props to mount component against.

## Fake Fetch
Sometimes you will need to override `fetch` function to return a mocked JSON response
for URL. This package provides a function to do that for you.

In `fixtures.js` you can define:

```
import { registerFakeFetch } from '@humblejs/demo';

const delay = 3000;

registerFakeFetch({
  '/api/item': {
    'name': 'sample-object'
  },
}, delay);
```

Once registered, `fetch`ing `/api/item` from the page will return `{name: 'sample-object'}` object after `3000 ms`

By default, `delay` is 0 i.e, it returns immediately without a wait.

## Create Items
You can create items by using `createItems` to create JSON objects.

Following function is just a helper to create a single item that we can use with `createItems`
```
const createSingleItem = idx => ({
  id: idx,
  name: `item-${idx}`,
});
```

```
import { createItems } from '@humblejs/demo';
```

Now you can use createItems

```
createItems(11, 10, createSingleItem)
```

Above function will run `createSingleItem` for index `11` to `21` and return array of items.
