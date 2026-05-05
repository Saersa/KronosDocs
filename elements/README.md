# Elements Overview

Kronos provides a rich set of interactive UI elements. All elements share a **unified API surface** for consistency.

## Universal Methods (v1.1)

Every element created via `Section:Element(...)` returns an object with the following standard methods:

| Method | Description |
| :--- | :--- |
| `:Update(config)` | Dynamically updates the element's properties (Name, Description, etc.). |
| `:Lock()` | Locks the element, preventing user interaction. Displays a lock icon. |
| `:Unlock()` | Unlocks the element, restoring full interactivity. |
| `:SetLockState(boolean)` | Sets the locked state programmatically. `true` = locked. |
| `:SetVisible(boolean)` | Shows or hides the element. |
| `:SetValue(value)` | Manually sets the element's current value (type varies by element). |

## Premium Gating

Any element can be gated behind a premium flag:

```lua
Section:Button({
    Name = "VIP Feature",
    Premium = true,
    LockedTitle = "PURCHASE ACCESS",
    Callback = function() end
})
```

Premium elements are automatically locked with a custom title until manually unlocked via `:Unlock()`.

## Available Elements

| Element | Page |
| :--- | :--- |
| Button | [button.md](button.md) |
| Hold Button | [holdbutton.md](holdbutton.md) |
| Toggle | [toggle.md](toggle.md) |
| Slider | [slider.md](slider.md) |
| Dropdown | [dropdown.md](dropdown.md) |
| Multi Dropdown | [multidropdown.md](multidropdown.md) |
| Input | [input.md](input.md) |
| Color Picker | [colorpicker.md](colorpicker.md) |
| Keybind | [keybind.md](keybind.md) |
| Paragraph | [paragraph.md](paragraph.md) |

---

Next: [Button](button.md)
