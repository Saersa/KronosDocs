# Slider

Sliders allow users to select a value within a specific range.

## Usage

```lua
Section:CreateSlider({
    Name = "WalkSpeed",
    Min = 16,
    Max = 100,
    Default = 16,
    ConfigId = "PlayerSpeed",
    Callback = function(val)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = val
    end
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Min` | number | `0` | Minimum possible value. |
| `Max` | number | `100` | Maximum possible value. |
| `Default` | number | `Min` | Initial value. |
| `ConfigId` | string | | ID for the config system. |
| `Callback` | function | | Fired when the value changes. |

---

Next: [Dropdown](dropdown.md)
