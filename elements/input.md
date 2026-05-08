# Input

A text input field for capturing user strings. Supports both single-line and multi-line (textarea) modes.

## Usage

```lua
-- Single Line
Section:Input({
    Name = "Webhook URL",
    Description = "Enter your Discord webhook.",
    Placeholder = "https://...",
    Callback = function(v)
        print("Input:", v)
    end
})

-- Multi Line (Textarea)
Section:Input({
    Name = "Script Box",
    Type = "Textarea",
    Placeholder = "Enter script code...",
    Callback = function(v)
        print("Code:", v)
    end
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Title` | string | `Name` | Alias for display title. |
| `Description` / `Desc` | string | `nil` | Optional text shown below the title. |
| `Type` | string | `"Input"` | `"Input"` for single line, `"Textarea"` for multi-line. |
| `Icon` | string | `nil` | Optional title icon. |
| `Placeholder` | string | `"Type here..."`| Ghost text shown when empty. |
| `Value` / `Default` | string | `""` | Initial text value. |
| `MinimumLength` | number | `0` | Minimum allowed length (validated on focus lost). |
| `MaximumLength` | number | `9999` | Maximum allowed length (validated on focus lost). |
| `ConfigId` | string | `nil` | Registers the element in config save/load. |
| `Callback` | function | | Fired when input focus is lost. |

## Methods

### `:Update(config)`
Dynamically updates properties.

### `:SetValue(string)`
Manually sets the input text.

### `:GetValue()`
Returns the current text string.

### `:Lock()` / `:Unlock()`
Standard interaction locking.

---

Next: [Keybind](keybind.md)
