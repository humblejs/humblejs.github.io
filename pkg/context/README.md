# Context
Lightweight wrapper React 16 context API

[Demo](https://humble.js.org/pkg/context/demo)

## Install

```
yarn add @humblejs/context
```

## Usage
```
import { Provider, withContext } from '@humblejs/context';
```

### Provider
Provides the context using React 16 context API

```
import { Provider } from '@humblejs/context';

const App = () => (
  <Provider value={
    {
      name: 'Amrayn Web Services',
      productName: 'humblejs',
    }
  }>
    <MyComponent />
  </Provider>
);
```

### withContext
Function to consume all the props provided by `Provider`

You can use this function in 3 different style, each one has its own benefit over other.

#### Simple
Simple mapping is where you map all the consumables in one-to-one fashion.

```
withContext(
  'name',
  'productName',
)
```

The props are available with same names, i.e, `props.name` and `props.productName`

For example

```
<div>Company name is {props.name}. Product: {props.productName}</div>
```

#### Mapped
You can map all the consumables with a custom name.

```
withContext(
  {
    'companyName': 'name',
  },
  'productName',
)
```
The `name` prop is available as `companyName` and `productName` is available as it is.

For example

```
<div>Company name is {props.companyName}. Product: {props.productName}</div>
```

#### Wrapped Object
You can map all the consumables in a separate wrapped object. **Notice the object**

```
withContext(
  {
    company: [
      'name',
      'productName',
    ],
  }
)
```

All the information is under object called `company`.

For example

```
<div>Company name is {props.company.name}. Product: {props.company.productName}</div>
```

## Provider Nesting
There will be time when you require multiple contexts created in same file. You will have to create
your own context.

```
import Context from '@humblejs/context';

const { Provider: Context1Provider, withContext: withContext1 } = Context.createContext();
const { Provider: Context2Provider, withContext: withContext2 } = Context.createContext();

<Context1Provider value={
  {
    name: 'context1-name',
    age: 22,
  }
}>
  <Context2Provider value={
    {
      amount: 24.33,
    }
  }>
    <MyComponent />
  </Context2Provider>
</Context1Provider>
```

```
const MyComponent = props => (
  <div>
    <div>Name: {props.name}</div>
    <div>Age: {props.age}</div>
    <div>Amount: {props.amount}</div>
  </div>
);

export default flow( // flow from lodash
  withContext1(
    'name',
    'age',
  ),
  withContext2(
    'amount',
  ),
)(MyComponent);
```
