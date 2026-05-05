# Dropdowns

Dropdowns allow users to select one or more items from a list.

## Standard Dropdown

A single-selection menu.

### Usage

```lua
Section:CreateDropdown({
    Name = "Target Mode",
    Options = {"Nearest", "Lowest HP", "Random"},
    Default = "Nearest",
    ConfigId = "AuraTarget",
    Callback = function(val)
        print("Selected:", val)
    end
})
```

---

## Multi Dropdown

Allows selecting multiple items at once.

### Usage

```lua
Section:CreateMultiDropdown({
    Name = "Filter Players",
    Options = {"Doran", "Jnkie", "Roblox", "Guest"},
    Default = {"Doran"},
    Callback = function(selectedList)
        print("Selected items:", table.concat(selectedList, ", "))
    end
})
```

## Options

| Property | Type | Description |
| :--- | :--- | :--- |
| `Name` | string | The display name. |
| `Options` | table | List of strings to choose from. |
| `Default` | string/table | Initial selection (single string for Dropdown, table for Multi). |
| `Callback` | function | Fired when selection changes. |

---

Next: [Color Picker](colorpicker.md)
