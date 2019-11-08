# DataProvider
Provides JSON data from remote api

[Demo](https://humble.js.org/pkg/data-provider/demo)

## Install

```
yarn add @humblejs/data-provider
```

## Usage

```
import createDataProvider from '@humblejs/data-provider';

const { DataProvider, withData } = createDataProvider();

const App = () => (
  <DataProvider url="/api/v1/data">
    <MyComponent />
  </DataProvider>
);
```

```
const MyComponent = ({ data }) => (
  <div>My address is {data.ADDRESS}</div>
);

export default withData(MyComponent, [
  'ADDRESS',
]);
```

### Advanced

For JSON Array response

```
withData(MyComponent, '*')

...

Array.isArray(props.data.items) // == true
```

For custom key name

```
withConfig(MyComponent, '*', 'staff')

...

Array.isArray(props.staff.items) // == true
```
