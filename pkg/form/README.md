# Form
Form elements package contains various UI components for forms.

[Demo](https://humblejs.zuhd.org/pkg/form/demo)

## Install

```
yarn add @humblejs/form
```

## Style

Import all the styling

```
@import '@humblejs/form/dist/css/styles.scss';
```

or import separately

```
@import '@humblejs/form/dist/css/form/input.scss';
@import '@humblejs/form/dist/css/form/checkbox.scss';
```

## Usage

You can import all the packages

```
import Form from '@humblejs/form'

...

<Form.Input />
```

or you can import separately
```
import { Input } from '@humblejs/form'

...

<Input />
```

### Input

| **Description** | **Value** |
|-----------|----------|
| Base component   | `<div>` |
| Base class   | `hjs-form__input` |

| **Props** | **Type / Description** | **Is Required?** | **Default** |
|-----------|----------|-------------|-------------|
| `name`    | string<br><br>Name of the text input element      | YES | |
| `icon`    | Icon from `@humblejs/icon` | NO | |
| `hasError` | bool<br><br>If true it adds `has-error` class | NO | FALSE |

### Checkbox

| **Description** | **Value** |
|-----------|----------|
| Base component   | `<li>` |
| Base class   | `hjs-form__checkbox` |
| Notes   | Must be inside `<ul>` |

| **Props** | **Type** | **Is Required?** | **Default** |
|-----------|----------|-------------|-------------|
| `name`    | string<br><br>Name of the text input element      | NO | null |
| `value`    | string<br><br>Value for checkbox      | NO | empty |
| `id`      | string<br><br>ID of input element | YES | |
| `onChange`      | func(e)<br><br>e is bool whether checked or not | NO | |
| `checked`      | bool<br><br>Checked or not | NO | `false` |
| `type`      | string (`checkbox`, `radio`)<br><br>Type of input | NO | `checkbox` |
| `icon`    | Icon from `@humblejs/icon` | NO | `check` |
| `shape`    | string (`round`, `square`)<br><br>Shape of checkbox | NO | `round` |
| `animation`    | string (`smooth`, `jelly`, `rotate`, `pulse`)<br><br>Animation when user interacts with checkbox  | NO | `smooth`  |
| `classList`    | Array of string<br><br>For further customising pretty checkbox | NO | []  |
