# Premium & Locking

Kronos provides a native API for feature gating, allowing you to easily lock individual elements or entire sections based on user access levels.

## Automatic Premium Gating

Every element supports a `Premium` flag. When true, the element is locked by default and displays a custom message.

```lua
Section:Toggle({
    Name = "Kill Aura",
    Premium = true,
    LockedTitle = "PURCHASE VIP",
    Callback = function(v) end
})
```

## Manual Locking API

You can programmatically lock or unlock any element at runtime. This is useful for feature dependencies (e.g., locking "Speed Amount" until "Auto Speed" is enabled).

```lua
local MySlider = Section:Slider({...})

-- Lock the element
MySlider:Lock()

-- Unlock the element
MySlider:Unlock()

-- Set state via boolean
MySlider:SetLockState(true)
```

## Section Locking

You can also lock an entire `TabSection` if needed:

```lua
local SecretSection = Window:Section({ Title = "Classified" })
-- Logic here
```

---

Next: [Configuration](config.md)
