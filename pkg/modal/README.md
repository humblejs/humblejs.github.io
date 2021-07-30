# Modal

[Demo](https://humble.js.org/pkg/modal/demo)

## Install

```
yarn add @humblejs/modal
```

## Props

| **Name** | **Type / Description** | **Is Required?** | **Default** |
|-----------|----------|-------------|-------------|
| `title`    | string      | NO | `null` |
| `onCancel`    | func<br><br>Triggers when dialog is cancelled. This function is triggered when close button is clicked, escape key is pressed or clicked outside the dialog. Usually you will set `isOpen` to `false` in the parent     | YES | |
| `hasCloseButton`    | bool<br><br>Whether there is close button or not. This button calls `onCancel`      | NO | `true` |
| `isOpen`    | bool<br><br>Whether modal is open or not, usually you will set it from parent's state     | NO | `false` |
| `fullScreen`    | bool<br><br>Whether modal is full screen or not     | NO | `false` |
| `transitionType`    | one of<ul><li>`slide`</li><li>`appear`</li></ul>     | NO | `slide` |
