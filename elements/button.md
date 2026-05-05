# Button

A standard interactive button that triggers a callback when clicked.

## Usage

```lua
Section:Button({
    Name = "Kill All",
    Description = "Eliminates all players in the server.",
    Callback = function()
        print("Button clicked!")
    end
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Name` | string | | The display name. |
| `Description` | string | `nil` | Optional text shown below the title. |
| `Premium` | boolean | `false` | If true, locks the button for non-premium users. |
| `LockedTitle`| string | `nil` | Custom text shown when locked. |
| `Callback` | function | | Fired when the button is clicked. |

## Methods

### `:Update(config)`
Dynamically updates the button's properties.

```lua
MyButton:Update({
    Name = "New Label",
    Description = "New description"
})
```

### `:Lock()` / `:Unlock()`
Standard interaction locking.

### `:SetVisible(boolean)`
Shows or hides the element.

---

Next: [Hold Button](holdbutton.md)
