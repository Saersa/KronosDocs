# Index

The `Index` element renders searchable, structured entries for changelogs, command references, or module docs.

## Usage

```lua
Section:Index({
    Title = "Commands",
    Description = "Reference list for all commands.",
    Searchbar = true,
    Collapsible = true,
    DefaultCollapsed = true,
    Data = {
        {
            Name = "teleport",
            Description = "Teleport to a player",
            Data = {
                Usage = ";tp <player>",
                Permission = "admin"
            }
        }
    }
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Title` / `Name` | string | `"Index"` | Header text. |
| `Description` | string | `nil` | Optional index description text. |
| `Data` | table | `{}` | Entry list for rendering index items. |
| `Searchbar` | boolean | `true` | Enables search box. |
| `Collapsible` | boolean | `false` | Makes entry bodies expandable. |
| `DefaultCollapsed` | boolean | `true` | Initial entry collapse state when `Collapsible` is enabled. |
| `ModuleCollapsed` | boolean | `false` | Collapses the full index module by default. |
| `ItemIcon` | string | `nil` | Default icon used for entries without `Icon`. |
| `EmptyText` | string | `"No index entries available."` | Empty-state text. |

## Methods

### `:SetData(table)`
Replaces all rendered index entries.

### `:Update(config)`
Updates title, description, data, and collapse behaviors.

### `:SetVisible(boolean)`
Shows or hides the element.

### `:Lock()` / `:Unlock()`
Standard interaction locking.

---

Next: [Button](button.md)
