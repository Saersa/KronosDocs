# Keybind

Assign a physical key to an action.

## Usage

```lua
Section:Keybind({
    Name = "Trigger Action",
    Description = "Press a key to execute.",
    Button = Enum.KeyCode.X, -- v1.1 Standard
    Callback = function()
        print("X was pressed!")
    end
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Description` | string | `nil` | Optional text shown below the title. |
| `Button` | Enum.KeyCode | `nil` | The initial key assigned. |
| `Default` | Enum.KeyCode | `nil` | Legacy alias for `Button`. |
| `Callback` | function | | Fired when the assigned key is pressed. |

## Keybind Toggle (Special Element)

Kronos v1.1 includes a specialized `KeybindToggle` that combines a boolean state with a keybind.

```lua
Section:KeybindToggle({
    Name = "Fly Mode",
    Button = Enum.KeyCode.F,
    Default = false,
    Callback = function(toggled)
        print("Fly is now:", toggled)
    end
})
```

## Methods

### `:Update(config)`
Updates binding or labels.

### `:SetValue(Enum.KeyCode)`
Manually re-binds the key.

### `:Lock()` / `:Unlock()`
Standard interaction locking.

---

Next: [Multi Dropdown](multidropdown.md)
