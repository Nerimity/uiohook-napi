# uiohook-napi

```
gh workflow run ci.yml -f electron_version=40.2.1 -f abi_version=143
```

[![](https://img.shields.io/npm/v/uiohook-napi/latest?color=CC3534&label=uiohook-napi&logo=npm&labelColor=212121)](https://www.npmjs.com/package/uiohook-napi)

N-API C-bindings for [libuiohook](https://github.com/kwhat/libuiohook).

### Usage example

```typescript
import { uIOhook, UiohookKey } from "uiohook-napi";

uIOhook.on("keydown", (e) => {
  if (e.keycode === UiohookKey.Q) {
    console.log("Hello!");
  }

  if (e.keycode === UiohookKey.Escape) {
    process.exit(0);
  }
});

uIOhook.start();
```

### API

```typescript
interface UiohookNapi {
  on(
    event: "input",
    listener: (
      e: UiohookKeyboardEvent | UiohookMouseEvent | UiohookWheelEvent,
    ) => void,
  ): this;

  on(event: "keydown", listener: (e: UiohookKeyboardEvent) => void): this;
  on(event: "keyup", listener: (e: UiohookKeyboardEvent) => void): this;

  on(event: "wheel", listener: (e: UiohookWheelEvent) => void): this;

  keyToggle(key: keycode, toggle: "down" | "up");
}

export interface UiohookKeyboardEvent {
  altKey: boolean;
  ctrlKey: boolean;
  metaKey: boolean;
  shiftKey: boolean;
  keycode: number;
}
```
