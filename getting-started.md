# Loadstring

To begin using Kronos v1.1, simply execute the following loadstring at the top of your script. This version introduces **secure locking**, **centered layouts**, and **background hydration**.

## Standard Execution

```lua
local Kronos = loadstring(game:HttpGet("https://kronosscripts.vercel.app/raw/UILibrary.lua"))()
```

## Developer Notes

*   **Non-Blocking Hydration**: `CreateWindow` no longer blocks your script. You can build your entire UI while the Key System or Loading Screen is visible.
*   **API Parity**: Use the new `Tab:Section` and `Tab:Toggle` aliases for cleaner code.
*   **Security**: Premium gating is now handled via a secure memory-based locking system, making it significantly harder to bypass than attribute-based systems.
*   **Assets**: All icons are bundled into the library—no more external HTTP requests for basic UI assets.

## Minimum Requirements

| Feature | Requirement |
| :--- | :--- |
| **Executor** | Level 7+ (Supporting `game:HttpGet` and `loadstring`) |
| **Roblox Environment** | Client-side only |
| **Internet Access** | Required for initial library and asset loading |

---

Next: [Window Configuration](core/window.md)
