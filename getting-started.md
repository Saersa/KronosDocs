# Loadstring

To begin using Kronos v1.2, simply execute the following loadstring at the top of your script. This version introduces **Popout panels**, **privacy-focused key masking**, and **hardened key validation**.

## Standard Execution

```lua
local Kronos = loadstring(game:HttpGet("https://kronosscripts.vercel.app/raw/UILibrary.lua"))()
```

## Developer Notes

- **Non-Blocking Hydration**: `CreateWindow` no longer blocks your script. You can build your entire UI while the Key System or Loading Screen is visible.
- **API Parity**: Use the new `Tab:Section` and `Tab:Toggle` aliases for cleaner code.
- **Security**: Premium gating is now handled via a secure memory-based locking system, making it significantly harder to bypass than attribute-based systems.
- **Assets**: All icons are bundled into the library—no more external HTTP requests for basic UI assets.
- **Popout Panels** _(v1.2)_: Side-extending panels with console support, toggleable from any button callback.
- **Key Privacy** _(v1.2)_: Auto-verification masks keys for screenshare safety (first 10 chars visible, rest starred).

## Minimum Requirements

| Feature                | Requirement                                           |
| :--------------------- | :---------------------------------------------------- |
| **Executor**           | Level 7+ (Supporting `game:HttpGet` and `loadstring`) |
| **Roblox Environment** | Client-side only                                      |
| **Internet Access**    | Required for initial library and asset loading        |

---

Next: [Window Configuration](core/window.md)
