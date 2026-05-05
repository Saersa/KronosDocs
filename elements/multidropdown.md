# Multi Dropdown

A selection menu that allows users to pick one or more items from a list.

## Usage

```lua
Section:MultiDropdown({
    Name = "Active Cheats",
    Description = "Select modules to enable.",
    Options = {"Aimbot", "ESP", "Fly", "Infinite Jump"},
    Default = {"ESP"},
    Callback = function(list)
        print("Enabled:", table.concat(list, ", "))
    end
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Description` | string | `nil` | Optional text shown below the title. |
| `Options` | table | `{}` | List of strings to choose from. |
| `Default` | table | `{}` | List of initially selected strings. |
| `Callback` | function | | Fired when the selection changes. |

## Methods

### `:Update(config)`
Updates options or labels.

### `:SetValue(table)`
Manually sets the selection list.

### `:GetValue()`
Returns a table of currently selected strings.

### `:Refresh(newOptions, keepCurrent)`
Standard options refresh.

### `:Lock()` / `:Unlock()`
Standard interaction locking.

---

Next: [Paragraph](paragraph.md)
