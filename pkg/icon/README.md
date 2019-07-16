# Icon
SVG based Icons packages. Thanks to Font Awesome

[Demo](https://humblejs.zuhd.org/pkg/icon/demo)

## Install

```
yarn add @humblejs/icon
```

## Style

Import all styling
```
@import '@humblejs/icon/dist/css/styles.scss';
```

## Props

| **Name** | **Type / Description** | **Is Required?** | **Default** |
|-----------|----------|-------------|-------------|
| `size`    | string (`large`, `small`, `custom`)      | NO | Custom with 18px x 18px |
| `flipped`    | bool<br><br>Flip icon horizontally | NO | FALSE |
| `className`    | string<br><br>Custom class name | NO | EMPTY |

## Usage

You can import all the packages

```
import Icons from '@humblejs/icon';

...

<Icons.Yelp />
```

or you can import separately
```
import { Facebook } from '@humblejs/icon'

...

<Facebook />
```

or you can import from file
```
import FacebookIcon from '@humblejs/icon/dist/js/facebook'

...

<FacebookIcon />
```

