# Notifications

Display high-fidelity toast notifications to provide feedback to the user.

## Usage

```lua
Window:Notify({
    Title = "Success",
    Content = "The configuration has been saved.",
    Duration = 5,
    Icon = "check-circle" -- Optional Lucide icon
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Title` | string | | Bold header text. |
| `Content` | string | | Main body text. |
| `Duration` | number | `5` | Time in seconds before the notification fades. |
| `Buttons` | table | `nil` | Optional dictionary of `[ButtonText] = Callback`; when provided, notification becomes action-based. |

---

Next: [Theming](themes.md)
