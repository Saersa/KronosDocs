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
| `Options` | table | `{}` | List of options (strings or `{Name, Value}` tables). |
| `Default` | any | `nil` | Initial selected value. |
| `Searchbar` | boolean | `true` | Enables built-in option search. |
| `ConfigId` | string | `nil` | Registers the element in config save/load. |
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

### `:SetValue(value)`
Manually sets the selected option value.

### `:GetValue()`
Returns the currently selected value.

### `:Lock()` / `:Unlock()`
Standard interaction locking.

---

Next: [Multi Dropdown](multidropdown.md)
