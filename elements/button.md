# Buttons

Buttons allow users to trigger actions with a single click or by holding.

## Standard Button

A simple clickable element.

### Usage

```lua
Section:CreateButton({
    Name = "Click Me",
    Callback = function()
        print("Button clicked!")
    end
})
```

### Options

| Property | Type | Description |
| :--- | :--- | :--- |
| `Name` | string | The text displayed on the button. |
| `Callback` | function | Fired when the button is clicked. |
| `Premium` | boolean | (Optional) Lock for premium users. |
| `Locked` | boolean | (Optional) Manually lock the button. |
| `LockedTitle` | string | (Optional) Title shown when locked. |

---

## Hold Button

A button that requires the user to hold it for a specific duration before the callback fires.

### Usage

```lua
Section:CreateHoldButton({
    Name = "Hold to Reset",
    Duration = 2, -- Seconds
    Callback = function()
        print("Hold completed!")
    end
})
```

### Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The text displayed on the button. |
| `Duration` | number | `1` | Time in seconds to hold. |
| `Callback` | function | | Fired when hold is complete. |

---

Next: [Toggle](toggle.md)
