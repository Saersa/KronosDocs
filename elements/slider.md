# Slider

A draggable slider for selecting a numeric value within a range.

## Usage

```lua
Section:Slider({
    Name = "WalkSpeed",
    Description = "Adjust your character's speed.",
    Min = 16,
    Max = 100,
    Default = 16,
    Suffix = " studs", -- Optional text added to the value
    Callback = function(v)
        print("Value:", v)
    end
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Description` | string | `nil` | Optional text shown below the title. |
| `Min` | number | | Minimum allowed value. |
| `Max` | number | | Maximum allowed value. |
| `Default` | number | `Min` | Initial value. |
| `ConfigId` | string | `nil` | Registers the element in config save/load. |
| `Callback` | function | | Fired when the value changes. |

## Methods

### `:Update(config)`
Updates labels or range.

### `:SetValue(number)`
Manually sets the slider value (automatically clamped).

### `:GetValue()`
Returns the current number.

### `:Lock()` / `:Unlock()`
Standard interaction locking.

---

Next: [Toggle](toggle.md)
