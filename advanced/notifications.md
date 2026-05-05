# Notifications

Notifications are temporary "toast" messages that appear at the bottom right of the screen to alert the user.

## Usage

```lua
Window:Notify({
    Title = "Welcome",
    Content = "Kronos UI has finished loading.",
    Duration = 5, -- Seconds
    Icon = "check-circle", -- Lucide icon name
    Buttons = {
        ["Ok"] = function()
            print("User clicked Ok")
        end
    }
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Title` | string | | The main bold text. |
| `Content` | string | | The description text. |
| `Duration` | number | `5` | Time in seconds before disappearing. |
| `Icon` | string | `nil` | Lucide icon name. |
| `Buttons` | table | `{}` | Dictionary of `[Label] = Callback` for action buttons. |

---

Back to: [README](../README.md)
