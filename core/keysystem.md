# Key System

Kronos includes a built-in, animated Key System that supports custom validation logic or integration with 3rd-party services like **Junkie**.

## Basic Configuration

```lua
local Window = Kronos:CreateWindow({
    Keysystem = {
        Enabled = true,
        SaveKey = true, -- Auto-save key to file
        Title   = "Kronos Verification",
        Subtitle = "Join Discord for Key",
        Note    = "Key link: discord.gg/kronos",
        FileName = "KronosKey", -- The name of the file saved on your PC
        Key      = "abc-123" -- Single key OR table: {"key1", "key2"}
    }
})
```

## Junkie Integration (Recommended)

If you use [Junkie](https://jnkie.com), Kronos can handle the entire verification flow, including SCRIPT_KEY detection from external loaders and initializing the secure `getgenv().Client` profile.

```lua
Keysystem = {
    Enabled = true,
    SaveKey = true,
    Provider = {
        Name = "Junkie",
        ServiceID = "1234", -- Your Service ID
        ServiceName = "Kronos" -- Your Service Name
    }
}
```

### Loading Sequence

1. **Manual Entry**: If no saved key exists, the Key System window opens.
2. **Auto-Skip**: If a valid key exists in `getgenv().SCRIPT_KEY` (External Loader) or your local `FileName.txt`, the UI shows for **2 seconds** before automatically verifying and continuing.
3. **Setting Up**: After verification, a 5-second "Setting up window..." loader appears while your script builds the UI in the background.

## Advanced Validation

You can use a custom function to validate keys (e.g., calling your own API).

```lua
Keysystem = {
    Enabled = true,
    KeyValidator = function(input)
        local success, response = pcall(function()
            return game:HttpGet("https://your-api.com/check?key=" .. input)
        end)
        return (success and response == "valid")
    end
}
```

---

Next: [Navigation](navigation.md)
