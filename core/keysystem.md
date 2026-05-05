# Key System

The Kronos Key System is an automated security layer that gates your script behind a verification wall. It features a professional, animated interface and seamless integration with the **Junkie SDK**.

## Configuration

```lua
Keysystem = {
    Enabled     = true,
    SaveKey     = true,         -- Caches key locally for auto-skip
    Title       = "Verification",
    Subtitle    = "Kronos Access",
    Note        = "Join: discord.gg/kronos",
    FileName    = "MyScriptKey", -- Filename for the local cache
    
    Provider = {
        Name        = "Junkie",
        ServiceID   = "1234",    -- Your Junkie Service ID
        ServiceName = "Kronos"
    }
}
```

## Smart Features

### 1. Auto-Skip Failsafe (3s Countdown)
If the library detects a valid cached key (via `getgenv().SCRIPT_KEY` or the local `FileName.txt`), it will display a **3-second countdown** on the "Verify Key" button. During this countdown, the user can **click anywhere** to cancel the auto-verification. This prevents instant-kicks from providers like Junkie when a saved key has expired.

> **Why?** Without the failsafe, expired saved keys would trigger immediate validation failure, which some providers respond to by disconnecting the user. The countdown gives the user a chance to cancel and manually enter a new key.

### 2. Failure Feedback
If a key check fails (manual or automatic), the UI will trigger a **shake animation**, display an **"Invalid key"** status in red, and reset the button after 1 second — allowing the user to retry without restarting the script.

### 3. Real-time Status
The verification button provides live feedback during the process:
*   **"Auto-verifying in 3... (Click to cancel)"**: Countdown phase.
*   **"Verifying key..."**: While contacting the provider API.
*   **"Valid Key"**: On successful authentication (before transitioning).
*   **"Invalid key"**: When the provider rejects the token.

### 4. Junkie Profile Hydration
When using the Junkie provider, Kronos automatically fetches the user's `Client` profile (Discord ID, Premium status, etc.) and populates the [User Info](../core/navigation.md) section.

## Manual Key Overrides

If you prefer to use a static key or a table of keys:

```lua
Keysystem = {
    Enabled = true,
    Key = "secret-key-123" -- or {"key1", "key2"}
}
```

---

Next: [Navigation](navigation.md)
