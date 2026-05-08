# Configuration System

Kronos includes a built-in JSON-based configuration system that automatically handles saving and loading your script's settings.

## Registering Elements

To make an element saveable, simply provide a `ConfigId` in its options.

```lua
Section:Toggle({
    Name = "Auto Farm",
    ConfigId = "AutoFarmToggle", -- Unique identifier
    Default = false,
    Callback = function(v) end
})
```

## Manual Control

The library handles auto-saving by default if enabled in the Settings popup. You can also trigger it manually:

### `Kronos:SaveConfig(filename)`
Saves all registered elements to `Kronos/<filename>.json`.

```lua
Kronos:SaveConfig("MyCustomSettings")
```

### `Kronos:LoadConfig(filename)`
Loads settings from a specific file and updates all UI elements.

```lua
Kronos:LoadConfig("MyCustomSettings")
```

## Global Settings
The library can also save internal UI state (Theme, Blur, Lock, AutoSave) to `Kronos/settings.json` via:

```lua
Window:SaveSettings()
Window:LoadSettings()
```

---

Next: [Theming](themes.md)
