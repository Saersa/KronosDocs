# Key System

The Kronos Key System is an automated security layer that gates your script behind a verification wall. It features a professional, animated interface and seamless integration with the **Junkie SDK**.

## Configuration

```lua
Keysystem = {
    Enabled     = true,
    SaveKey     = true,          -- Caches key locally for auto-skip
    Title       = "Verification",
    Subtitle    = "Kronos Access",
    Note        = "Join: discord.gg/kronos", -- Alias: Description
    Icon        = "Dynamic",     -- Uses current theme icon when "Dynamic"
    Thumbnail   = "Dynamic",     -- Uses current theme banner when "Dynamic"
    FileName    = "KronosKey",   -- Filename for the local cache (default: "KronosKey")

    Provider = {
        Name        = "Junkie",
        ServiceID   = "1234",    -- Your Junkie Service ID
        ServiceName = "Kronos"
    }
}
```

## Smart Features

### 1. Auto-Skip Failsafe (5s Countdown)

If the library detects a cached key (via `getgenv().SCRIPT_KEY` or local `FileName.txt` when `SaveKey = true`), it shows a **5-second countdown** on the "Verify Key" button before auto-validation. During this countdown, the user can **click the Verify button** to cancel auto-verification and retry manually.

> **Why?** Without the failsafe, expired saved keys would trigger immediate validation failure, which some providers respond to by disconnecting the user. The countdown gives the user a chance to cancel and manually enter a new key.

### 2. Privacy-Focused Key Masking _(v1.2)_

During auto-verification, the key is displayed in the text box with **privacy masking**: only the first 10 characters are visible, and the rest are replaced with `*` characters. This protects keys from being stolen during screen sharing or recording.

> [!IMPORTANT]
> The masked key is **only for display**. The actual raw key is always used for server-side validation. The TextBox is cleared automatically if verification fails or is cancelled.

### 3. Failure Feedback

If a key check fails (manual or automatic), the UI will trigger a **shake animation**, display an **"Invalid key"** status in red, and reset the button after 1 second — allowing the user to retry without restarting the script. The "Get Key" button visibility is also correctly restored on failure.

### 4. Real-time Status

The verification button provides live feedback during the process:

- **"Auto-verifying in 5... (Click to cancel)"**: Countdown phase.
- **"Verifying key..."**: While contacting the provider API.
- **"Valid Key"**: On successful authentication (before transitioning).
- **"Invalid key"**: When the provider rejects the token.

## Manual Key Overrides

If you prefer to use a static key or a table of keys:

```lua
Keysystem = {
    Enabled = true,
    Key = "secret-key-123" -- or {"key1", "key2"}
}
```

You can also provide a custom validator:

```lua
Keysystem = {
    Enabled = true,
    KeyValidator = function(input)
        return input == "secret-key-123", "Invalid key"
    end
}
```

---

Next: [Navigation](navigation.md)
