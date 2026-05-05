# Dropdown

A selection menu that allows users to pick a single item from a list.

## Usage

```lua
Section:Dropdown({
    Name = "Active Weapon",
    Description = "Select your primary tool.",
    Options = {"Sword", "Hammer", "Bow"},
    Default = "Sword",
    Callback = function(v)
        print("Selected:", v)
    end
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Description` | string | `nil` | Optional text shown below the title. |
| `Options` | table | `{}` | List of strings to choose from. |
| `Default` | string | `nil` | Initial selected value. |
| `Callback` | function | | Fired when a new option is selected. |

## Methods

### `:Update(config)`
Dynamically updates the dropdown's properties or options.

```lua
MyDropdown:Update({
    Options = {"New Option 1", "New Option 2"},
    Default = "New Option 1"
})
```

### `:SetValue(string)`
Manually sets the selected option. Must exist in the `Options` list.

### `:GetValue()`
Returns the currently selected string.

### `:Refresh(newOptions, keepCurrent)`
Updates the options list. If `keepCurrent` is true, it attempts to keep the current selection if it exists in the new list.

### `:Lock()` / `:Unlock()`
Standard interaction locking.

---

Next: [Multi Dropdown](multidropdown.md)
