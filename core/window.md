# Window

The `CreateWindow` function is the foundation of your interface. It initializes the library state, handles the dual-loader sequence, and sets up the primary ScreenGui.

## Usage

```lua
local Window = Kronos:CreateWindow(options)
```

## Options Configuration

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Title` | string | `"Kronos"` | The primary title shown in the header. |
| `SubTitle` | string | `""` | Secondary label for versioning or status. |
| `Icon` | string | `nil` | Asset ID for branding. Use `"Dynamic"` for theme default. |
| `IconSize` | number | `48` | Size of the header icon in pixels. |
| `Theme` | string | `"Batman"` | Initial color palette. |
| `Size` | Vector2 | `600, 400` | Default window dimensions. |
| `ToggleUI` | KeyCode | `RightControl` | Hotkey to hide/show the interface. |
| `Acrylic` | boolean | `false` | Enables glassmorphic background blur overlay. |
| `BackgroundImage` | string | `""` | Optional Roblox asset ID for the window background. Hidden when empty. |
| `BackgroundTransparency` | number | `0.8` | The transparency of the background image itself. |
| `UIBackgroundTransparency` | number | `0` | Controls Sidebar and Content panel transparency so backgrounds show through. |
| `SearchBar` | boolean | `false` | Enables global element search in the sidebar. |
| `KeyExpiry` | boolean | `false` | Shows Junkie license expiration in the settings popup. |
| `UserInfo` | table | `nil` | Configures footer user profile display. |
| `LoadingScreen` | table | `nil` | Configures the splash screen sequence. |
| `Keysystem` | table | `nil` | Configures integrated authentication. |

## Advanced Loading Logic

Kronos uses a **Background-Hydration** pattern to ensure zero lag. When you call `CreateWindow`:

1.  **Loader 1**: Displays your custom branding splash.
2.  **Auth Layer**: The Key System validates the user.
3.  **Loader 2**: A "Setting up window..." screen covers the UI.
4.  **Hydration**: Your script continues running and builds your tabs.
5.  **Reveal**: Once Loader 2 finishes, the window fades in **fully populated**.

## Window Methods

| Method | Description |
| :--- | :--- |
| `Window:SetTitle(text)` | Changes the window title dynamically. |
| `Window:SetSubtitle(text)` | Changes the subtitle dynamically. |
| `Window:SetBackgroundImage(id, transparency)` | Sets or clears the background image. Pass `nil` to hide. |
| `Window:SetBlur(val)` | Sets blur overlay. `1` = enabled, `0` = disabled. |
| `Window:SetToggleKeybind(keyCode)` | Changes the UI toggle hotkey at runtime. |
| `Window:Notify(options)` | Displays a notification toast. |
| `Window:Dialog(options)` | Shows a confirmation dialog with buttons. |
| `Window:SaveSettings()` | Manually saves theme, blur, and lock state. |
| `Window:LoadSettings()` | Loads saved settings from disk. |

## Full Example

```lua
local Window = Kronos:CreateWindow({
    Title       = "Kronos - Test",
    SubTitle    = "v1.1",
    Icon        = "Dynamic",
    IconSize    = 48,
    Theme       = "Space",
    ToggleUI    = Enum.KeyCode.RightControl,
    Acrylic     = false,
    SearchBar   = true,
    
    -- Background Image (optional)
    BackgroundImage = "rbxassetid://11419713314",
    BackgroundTransparency = 0.85,
    UIBackgroundTransparency = 0.15,
    
    Keysystem = {
        Enabled = true,
        SaveKey = true,
        Provider = { Name = "Junkie", ServiceID = "1234" }
    },
    
    LoadingScreen = {
        Enabled     = true,
        Duration    = 3,
        Title       = "Project Kronos",
        Description = "Loading core modules..."
    }
})
```

---

Next: [Key System](keysystem.md)
