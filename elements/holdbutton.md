# Hold Button

A button that requires the user to hold it down for a specified duration before the callback is triggered. Perfect for dangerous actions.

## Usage

```lua
Section:HoldButton({
    Name = "Delete Data",
    Description = "Hold for 3 seconds to wipe everything.",
    Duration = 3,
    Callback = function()
        print("Action confirmed!")
    end
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Description` | string | `nil` | Optional text shown below the title. |
| `Duration` | number | `2` | Time in seconds required to hold. |
| `HoldDuration` | number | `2` | Alias of `Duration`. |
| `Callback` | function | | Fired after the duration is met. |

## Methods

### `:Update(config)`
Dynamically updates properties.

```lua
MyHold:Update({
    Name = "Wipe Server",
    Duration = 5
})
```

### `:Lock()` / `:Unlock()`
Standard interaction locking.

---

Next: [Input](input.md)
