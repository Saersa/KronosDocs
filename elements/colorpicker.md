# Color Picker

The Color Picker allows users to select a custom RGB color.

## Usage

```lua
Section:CreateColorPicker({
    Name = "ESP Color",
    Default = Color3.fromRGB(255, 0, 0),
    Callback = function(color)
        print("Selected Color:", color)
    end
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Default` | Color3 | `Color3.new(1,1,1)` | Initial color. |
| `Callback` | function | | Fired when the color changes. |

---

Next: [Keybind](keybind.md)
