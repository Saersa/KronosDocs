# Color Picker

The Color Picker element allows users to select an RGB color with support for HSV, RGB sliders, Alpha (transparency), and HEX input.

## Usage

```lua
Section:ColorPicker({
    Name = "Accent Color",
    Description = "Choose the UI accent color.",
    Default = Color3.fromRGB(255, 77, 77),
    Callback = function(color, alpha)
        print("Color Selected:", color, "Alpha:", alpha)
    end
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Description` | string | `nil` | Optional text shown below the title. |
| `Default` | Color3 | `white` | Initial color value. |
| `Callback` | function | | Fired when the color or alpha changes. |

## Features

### 1. Unified HSV & RGB
Users can select colors via the traditional Saturation/Value square, Hue slider, or individual Red, Green, and Blue sliders for precision.

### 2. Alpha Support
Includes an Alpha (transparency) slider. The callback returns both the `Color3` and a `number` (0-1) for alpha.

### 3. HEX Input & Copy (v1.1)
Users can enter hex codes manually. A **Copy Button** has been added next to the HEX field to quickly copy the current color code to the system clipboard (requires `setclipboard` support).

## Methods

### `:Update(config)`
Dynamically updates the color picker's properties.

```lua
MyPicker:Update({
    Name = "New Label",
    Default = Color3.new(0, 1, 0)
})
```

### `:SetValue(Color3)`
Manually sets the color.

### `:GetValue()`
Returns the current `Color3` value.

### `:Lock()` / `:Unlock()`
Standard interaction locking.

---

Next: [Keybind](keybind.md)
