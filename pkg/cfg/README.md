# Cfg
Remote config wrapper and provider

[Demo](https://humble.js.org/pkg/cfg/demo)

## Install

```
yarn add @humblejs/cfg
```

## Usage

```
import { ConfigWrapper } from '@humblejs/cfg';


const App = () => (
  <ConfigWrapper url="/api/cfg">
    <MyComponent />
  </ConfigWrapper>
);
```

```
import withConfig from '@humblejs/cfg';

const MyComponent = ({ cfg }) => (
  <div>My address is {cfg.ADDRESS}</div>
);

export default withConfig(MyComponent, [
  'ADDRESS',
]);
```

### Advanced

For JSON Array response

```
withConfig(MyComponent, '*')

...

Array.isArray(props.cfg) // == true
```

For custom key name

```
withConfig(MyComponent, '*', 'staff')

...

Array.isArray(props.staff) // == true
```
