# Configuration System

Kronos features an automated configuration system that allows you to save and load user settings with ease.

## Registering Elements

To make an element "savable", simply provide a unique `ConfigId` string.

```lua
Section:CreateToggle({
    Name = "Aimbot",
    ConfigId = "Combat_Aimbot", -- Must be unique
    Callback = function(v) end
})
```

## Saving and Loading

The library provides global methods to manage the configuration files.

### `Kronos:SaveConfig(filename)`
Saves all registered elements to a JSON file in the executor's workspace folder.

```lua
Kronos:SaveConfig("my_settings") -- Saves to "my_settings.json"
```

### `Kronos:LoadConfig(filename)`
Loads settings from a file and automatically updates all registered UI elements.

```lua
Kronos:LoadConfig("my_settings")
```

## Best Practices
- Use prefixes for `ConfigId` to avoid collisions (e.g., `Combat_`, `Visuals_`).
- Call `LoadConfig` after all elements have been created to ensure they are updated correctly.

---

Next: [Theming](themes.md)
