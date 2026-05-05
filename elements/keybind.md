# Keybind

A Keybind element allows users to assign a specific key to an action.

## Usage

```lua
Section:CreateKeybind({
    Name = "Kill All",
    Default = Enum.KeyCode.X,
    Callback = function()
        print("X was pressed!")
    end
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Default` | Enum.KeyCode | `nil` | Initial keybind. |
| `Callback` | function | | Fired when the key is pressed. |

---

Next: [Paragraph](paragraph.md)
