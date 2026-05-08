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
| `Options` | table | `{}` | List of options (strings or `{Name, Value}` tables). |
| `Default` | table/any | `{}` | Initial selected values. |
| `Searchbar` | boolean | `true` | Enables built-in option search. |
| `ConfigId` | string | `nil` | Registers the element in config save/load. |
| `Callback` | function | | Fired when the selection changes. |

## Methods

### `:Update(config)`
Updates options or labels.

### `:SetValue(valueOrTable)`
Manually sets selection.

### `:GetValue()`
Returns a table of currently selected strings.

Selections and options should be updated through `:Update(config)`.

### `:Lock()` / `:Unlock()`
Standard interaction locking.

---

Next: [Paragraph](paragraph.md)
