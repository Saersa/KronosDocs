# Toggles

Toggles are boolean switches used for enabling/disabling features.

## Standard Toggle

### Usage

```lua
Section:CreateToggle({
    Name = "Aimbot",
    Default = false,
    ConfigId = "AimbotToggle",
    Callback = function(state)
        print("Aimbot is now:", state)
    end
})
```

### Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Default` | boolean | `false` | Initial state. |
| `ConfigId` | string | | ID for the config system. |
| `Callback` | function | | Fired when the state changes. |

---

## Keybind Toggle

A toggle that can also be activated by a specific keybind.

### Usage

```lua
Section:CreateKeybindToggle({
    Name = "Fly (F)",
    Keybind = Enum.KeyCode.F,
    Default = false,
    Callback = function(state)
        print("Fly is now:", state)
    end
})
```

### Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Keybind` | Enum.KeyCode | | The key that toggles the state. |
| `Default` | boolean | `false` | Initial state. |
| `Callback` | function | | Fired when toggled. |

---

Next: [Slider](slider.md)
