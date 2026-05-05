# Window Configuration

The `CreateWindow` function is the entry point for your UI. It accepts a variety of options to customize the appearance and behavior of the window.

## Usage

```lua
local Window = Kronos:CreateWindow(options)
```

## Options Reference

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Title` | string | `"Kronos"` | The main title of the window. |
| `SubTitle` | string | `""` | A small subtitle shown next to the title. |
| `Icon` | string | `nil` | The asset ID for the window icon (or "Dynamic"). |
| `IconSize` | number | `48` | The size of the window icon. |
| `Size` | Vector2 | `Vector2.new(650, 450)` | The dimensions of the window. |
| `Theme` | string | `"KronosRed"` | The initial theme name. |
| `ToggleUI` | Enum.KeyCode | `Enum.KeyCode.RightShift` | The key used to hide/show the UI. |
| `Acrylic` | boolean | `true` | Enables/disables the blur effect. |
| `SearchBar` | boolean | `true` | Shows a search bar in the sidebar for tabs. |
| `KeyExpiry` | boolean | `false` | Shows a key expiration timer in the footer. |
| `Keysystem` | table | `nil` | Configuration for the built-in key system. |
| `OnReady` | function | `nil` | Callback that fires when the UI is verified. |

### Key System

The built-in Key System supports multiple providers (like Junkie) and handles local key caching automatically.

```lua
local Window = Kronos:CreateWindow({
    Keysystem = {
        Enabled = true,
        SaveKey = true,
        Title   = "Kronos Access",
        Subtitle = "Verification System",
        Provider = { 
            Name = "Junkie", 
            ServiceID = "1078290", 
            ServiceName = "Kronos" 
        }
    }
})
```
See [Key System](keysystem.md) for full details.

### Loading Screen

You can configure the splash screen (Loader 1) that plays before the Key System.

```lua
local Window = Kronos:CreateWindow({
    LoadingScreen = {
        Enabled     = true,
        Duration    = 3, -- Seconds
        Title       = "Project Name",
        Description = "Loading modules...",
        Icon        = "Dynamic"
    }
})
```

### User Info Footer

Shows user details (Discord username/avatar) at the bottom of the sidebar. This integrates automatically with the Junkie `Client` profile.

```lua
local Window = Kronos:CreateWindow({
    UserInfo = {
        Enabled = true,
        Anonymous = false, -- Set true to hide Discord tag
        Clicked = function()
            print("User profile opened")
        end
    }
})
```

## Methods

### `Window:Notify(options)`
Shows a toast notification. See [Notifications](../advanced/notifications.md) for details.

### `Window:SetToggleKeybind(key)`
Dynamically changes the key used to toggle the UI.

### `Window:SetGlow(state)`
Enables or disables the accent glow effects globally.

---

Next: [Key System](keysystem.md)
