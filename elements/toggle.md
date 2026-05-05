# Toggle

A boolean switch that can be turned on or off.

## Usage

```lua
Section:Toggle({
    Name = "Aimbot",
    Description = "Automatically target players.",
    Default = false,
    Callback = function(v)
        print("Aimbot is now:", v)
    end
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Description` | string | `nil` | Optional text shown below the title. |
| `Default` | boolean | `false` | Initial state. |
| `Callback` | function | | Fired when the state toggles. |

## Methods

### `:Update(config)`
Dynamically updates properties.

```lua
MyToggle:Update({
    Name = "Silent Aim",
    Description = "Uses memory-based targeting."
})
```

### `:SetValue(boolean)`
Manually sets the toggle state.

### `:GetValue()`
Returns the current boolean value.

### `:Lock()` / `:Unlock()`
Standard interaction locking.

---

Next: [Color Picker](colorpicker.md)
