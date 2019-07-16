# Share
Buttons to share link on social media and other channels

[Demo](https://humblejs.zuhd.org/pkg/share/demo)

## Install

```
yarn add @humblejs/share
```

## Style

Import all styling
```
@import '@humblejs/share/dist/css/styles.scss';
```


## Props

| **Name** | **Type / Description** | **Is Required?** | **Default** |
|-----------|----------|-------------|-------------|
| `url`    | string<br><br>URL to share      | Yes |  |
| `title`    | string<br><br>Title of the URL | No | Empty |
| `excerpt`    | string<br><br>Excerpt from URL (or brief description) | No | Empty |

## Analytics
You can map GA analytics for share buttons using `dist/js/ga.js`

```
import { registerGaEvents, gaEventMap } from `@humblejs/share`;

registerGaEvents();
```

```
import { registerGaEvents, gaEventMap as shareButtonsGaEventMap } from `@humblejs/share`;

registerGaEvents({
  eventMap: shareButtonsGaEventMap, // this is default mapping
});
```
