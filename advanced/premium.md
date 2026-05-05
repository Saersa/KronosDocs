# Premium & Locking

Kronos includes a built-in system for gating features behind a premium status or manually locking them.

## Manual Locking

You can lock any element by setting the `Locked` property to `true`. Locked elements are greyed out and cannot be interacted with.

```lua
Section:CreateButton({
    Name = "Admin Feature",
    Locked = true,
    LockedTitle = "Admin Required", -- Custom title on the lock overlay
    Callback = function() end
})
```

## Premium Integration

If an element has `Premium = true`, Kronos will automatically check the `getgenv().Client` table for premium status.

### How it works

The library looks for `getgenv().Client.isPremium`. If this is `false`, the element will be locked automatically.

```lua
-- Mock Client Data (usually handled by your loader/auth)
getgenv().Client = {
    isPremium = false
}

Section:CreateToggle({
    Name = "Instant Kill",
    Premium = true, -- Will be locked if isPremium is false
    Callback = function() end
})
```

### Customizing the Lock Message

You can override the default premium lock messages:

```lua
Section:CreateSlider({
    Name = "WalkSpeed",
    Premium = true,
    LockedTitle = "Premium Only",
    LockedContent = "Please upgrade your subscription to access this feature.",
    Callback = function() end
})
```

---

Next: [Configuration System](config.md)
