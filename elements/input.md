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
| `Description` | string | `nil` | Optional text shown below the title. |
| `Type` | string | `"Input"` | `"Input"` for single line, `"Textarea"` for multi-line. |
| `Placeholder` | string | `"Enter text..."`| Ghost text shown when empty. |
| `Numeric` | boolean | `false` | (Coming Soon) Restricts input to numbers. |
| `Finished` | boolean | `false` | If true, callback only fires on focus lost (Enter/Click away). |
| `Callback` | function | | Fired on text change (or focus lost if `Finished` is true). |

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
