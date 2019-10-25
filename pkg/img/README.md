# Img
Image with low resolution support. Low res image is loaded and once high res is
ready, low res is replaced with high res.

[Demo](https://humble.js.org/pkg/img/demo)

## Install

```
yarn add @humblejs/img
```

## Props

| **Name** | **Type / Description** | **Is Required?** | **Default** |
|-----------|----------|-------------|-------------|
| `className`    | string<br><br>Extra class on top of default `co-img` | No | Empty |
| `src`    | string<br><br>High resolution image source | Yes |  |
| `srcLowResolution`    | string<br><br>Low resolution image source | No | `src` value |
| `alt`    | string<br><br>Image `alt` tag | Yes | |
| `fallback`    | component<br><br>Fallback component when image could not be loaded. This acts as a placeholder for error. | No | |
| `onLoad`    | func<br><br>Callback when high-res image was successfully loaded | No | |
| `onError`    | func<br><br>Callback if there was problem in loading image | No | |
| `type`    | string (`img`, `div`) <br><br>Load `<img>` tag or `<div>` with background image tag | No | `img` |
