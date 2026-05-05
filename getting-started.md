# Getting Started

This guide will help you create your first window and add basic elements to your UI.

## Basic Example

Kronos is designed to handle all your loading and security logic automatically. Here is a professional setup using the latest linear loading flow.

```lua
local Kronos = loadstring(game:HttpGet("https://kronosscripts.vercel.app/raw/UILibrary.lua"))()

-- 1. Create the Window
-- This function will handle the Splash Screen and Key System automatically.
-- It will pause your script (yield) until the user is verified!
local Window = Kronos:CreateWindow({
    Title       = "Kronos Library",
    SubTitle    = "v1.0.0",
    Icon        = "Dynamic", -- Uses theme icon
    Theme       = "KronosRed",
    Size        = Vector2.new(650, 450),
    
    -- Key System configuration
    Keysystem = {
        Enabled = true,
        SaveKey = true,
        Title   = "Kronos Access",
        Provider = { Name = "Junkie", ServiceID = "1078290" } -- Automatic Junkie integration
    },
    
    -- Optional loading screen before key system
    LoadingScreen = { Enabled = true, Title = "Kronos", Duration = 3 }
})

-- 2. Create a Sidebar Category
local MainSection = Window:Section({ Title = "Combat", Icon = "swords" })

-- 3. Create a Tab (Page)
local KillAuraTab = MainSection:Tab({ Name = "Kill Aura", Icon = "zap" })

-- 4. Create a Visual Section on the Page
local SettingsGroup = KillAuraTab:CreateSection("Aura Settings")

-- 5. Add Elements
SettingsGroup:CreateToggle({
    Name = "Enabled",
    Callback = function(state)
        print("Kill Aura:", state)
    end
})
```

## How it Works

### 1. Automatic Sequencing
When you call `CreateWindow`, the library starts a sequence:
1. **Loader 1**: Your splash screen.
2. **Key System**: Authenticates the user (auto-skips if they have a saved key).
3. **Loader 2**: Shows a "Setting up window..." screen.

**Crucially**, `CreateWindow` returns the `Window` object as soon as Loader 2 starts. This means your script continues to build all your tabs and sections *while* the "Setting up" screen covers the empty window. By the time the loader finishes, your UI is fully built!

### 2. Linear Flow
You no longer need to wrap your entire script in an `OnReady` function. Simply write your code after `CreateWindow`. The library ensures that your script only progresses once the user is verified.

---

Next: [Window Configuration](core/window.md)
