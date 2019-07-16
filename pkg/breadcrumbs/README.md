# Breadcrumbs
Breadcrumbs navigation for the page

[Demo](https://humblejs.zuhd.org/pkg/breadcrumbs/demo)

## Install

```
yarn add @humblejs/breadcrumbs
```

## Style

Import all styling
```
@import '@humblejs/breadcrumbs/dist/css/styles.scss';
```

## Props

| **Name** | **Type / Description** | **Is Required?** | **Default** |
|-----------|----------|-------------|-------------|
| `items`    | array of object<br> * text (string, required)<br> * link      | YES | Empty |
| `type`    | string<br> * `chevron` <br> * `slash` <br> * `double-angle`      | NO | `chevron` |
| `separator`    | string<br>If specified the `type` is ignored and this separator is used instead | NO | Null |
