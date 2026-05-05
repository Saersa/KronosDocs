# Full Example

The following is a complete, working example of the Kronos UI Library v1.1. It demonstrates the initialization sequence, the dual-phase loader, the Key System, and almost every UI element available.

```lua
--[[
    ========================================================================
    KRONOS UI LIBRARY - OFFICIAL DEMO & DOCUMENTATION (v1.1)
    ========================================================================
    Premium Syde-inspired UI with WindUI architecture.
    Standardized for high-performance and stealth execution.

    Support: https://discord.gg/kronos
]]

-- ═══════════════════════════════════════════════════════════════
-- 1. INITIALIZATION
-- ═══════════════════════════════════════════════════════════════
local Kronos = loadstring(game:HttpGet("https://kronosscripts.vercel.app/raw/UILibrary.lua"))()

-- ═══════════════════════════════════════════════════════════════
-- 2. WINDOW CREATION
-- ═══════════════════════════════════════════════════════════════
local Window = Kronos:CreateWindow({
    Title       = "Kronos Demo UI",
    SubTitle    = "v1.1 - Full Demo",
    Icon        = "Dynamic",
    IconSize    = 48,
    Size        = Vector2.new(650, 450),
    Theme       = "Space",
    ToggleUI    = Enum.KeyCode.RightControl,
    Acrylic     = false,
    SearchBar   = true,
    KeyExpiry   = true,

    -- Background Image (v1.1)
    BackgroundImage = "",
    BackgroundTransparency = 0.85,
    UIBackgroundTransparency = 0.15,

    -- Footer User Info
    UserInfo = {
        Enabled = true,
        Anonymous = false,
        Clicked = function()
            Window:Notify({ Title = "Profile", Content = "User info clicked!" })
        end
    },

    -- Dual-Phase Loading Sequence
    LoadingScreen = {
        Enabled     = true,
        Duration    = 2.5,
        Title       = "Kronos",
        Description = "Hydrating modules...",
        Icon        = "shield"
    },

    -- Integrated Key System (with Auto-Skip Failsafe)
    Keysystem = {
        Enabled = true,
        SaveKey = true,
        Title = "Access Control",
        Subtitle = "Developer License",
        Note = "Join .gg/kronos for your key.",
        FileName = "Kronos_Key",
        Provider = {
            Name = "Junkie",
            ServiceID = "1078290",
            ServiceName = "Kronos"
        }
    }
})

-- ═══════════════════════════════════════════════════════════════
-- 3. SIDEBAR NAVIGATION
-- ═══════════════════════════════════════════════════════════════
local NavSection = Window:Section({ Title = "Navigation", Icon = "layout" })
local CoreTab = NavSection:Tab({ Name = "Core", Icon = "box" })
local PremiumTab = NavSection:Tab({ Name = "Premium", Icon = "crown" })

local ModulesSection = Window:Section({ Title = "Modules", Icon = "layers" })
local InputTab = ModulesSection:Tab({ Name = "Inputs", Icon = "type" })
local AdvancedTab = ModulesSection:Tab({ Name = "Advanced", Icon = "settings-2" })

local SettingsSection = Window:Section({ Title = "Settings", Icon = "settings" })
local AppearanceTab = SettingsSection:Tab({ Name = "Appearance", Icon = "palette" })

-- ═══════════════════════════════════════════════════════════════
-- 4. CORE ELEMENTS (Standard UI)
-- ═══════════════════════════════════════════════════════════════
local Basic = CoreTab:Section("Basic Elements")

Basic:Button({
    Name = "Simple Button",
    Description = "Triggers a basic notification.",
    Callback = function()
        Window:Notify({ Title = "Action", Content = "Button clicked!", Duration = 3 })
    end
})

local FeatureToggle = Basic:Toggle({
    Name = "Active Toggle",
    Description = "Demonstrates a standard boolean switch.",
    Default = false,
    Callback = function(v) print("Toggle State:", v) end
})

local PrecisionSlider = Basic:Slider({
    Name = "Precision Slider",
    Description = "Adjust numeric values with smooth dragging.",
    Min = 0, Max = 100, Default = 50,
    Callback = function(v) print("Slider Value:", v) end
})

Basic:Paragraph({
    Title = "Welcome to Kronos v1.1",
    Description = "Experience the ultimate Luau UI library with dynamic property updates, premium stealth hardening, and high-fidelity themes.",
    Icon = "info"
})

-- ═══════════════════════════════════════════════════════════════
-- 5. INPUT ELEMENTS (Text & Data)
-- ═══════════════════════════════════════════════════════════════
local TextInputs = InputTab:Section("Text Input Methods")

TextInputs:Input({
    Name = "Single Line Input",
    Description = "Used for short strings like usernames.",
    Placeholder = "Enter text...",
    Callback = function(v) print("Input:", v) end
})

TextInputs:Input({
    Name = "Multi-Line Textarea",
    Description = "Perfect for webhooks or scripts.",
    Type = "Textarea",
    Placeholder = "Enter long content here...",
    Callback = function(v) print("Textarea:", v) end
})

local Selection = InputTab:Section("Selection Menus", { Boxed = true })

Selection:Dropdown({
    Name = "Single Selection",
    Options = {"Option A", "Option B", "Option C"},
    Default = "Option A",
    Callback = function(v) print("Selected:", v) end
})

Selection:MultiDropdown({
    Name = "Multi Selection",
    Description = "Choose one or more options.",
    Options = {"Speed", "Jump", "Fly", "Infinite"},
    Default = {"Speed"},
    Callback = function(v) print("Multi Select:", table.concat(v, ", ")) end
})

-- ═══════════════════════════════════════════════════════════════
-- 6. ADVANCED & INTERACTIVE
-- ═══════════════════════════════════════════════════════════════
local Advanced = AdvancedTab:Section("Special Interaction")

Advanced:HoldButton({
    Name = "Hold to Execute",
    Description = "Prevents accidental triggers.",
    Duration = 2,
    Callback = function()
        Window:Notify({ Title = "Success", Content = "Action executed after hold!" })
    end
})

Advanced:Keybind({
    Name = "Quick Trigger",
    Button = Enum.KeyCode.X,
    Callback = function() print("Keybind Activated!") end
})

Advanced:KeybindToggle({
    Name = "Toggle Bind (F)",
    Button = Enum.KeyCode.F,
    Callback = function(v) print("Bind Toggle:", v) end
})

Advanced:ColorPicker({
    Name = "Accent Color",
    Default = Color3.fromRGB(255, 77, 77),
    Callback = function(v) print("Color Selected:", v) end
})

-- ═══════════════════════════════════════════════════════════════
-- 7. PREMIUM & LOCKING API
-- ═══════════════════════════════════════════════════════════════
local VIP = PremiumTab:Section("VIP Features", { Boxed = true })

VIP:Button({
    Name = "Kill All Server",
    Premium = true,
    LockedTitle = "PURCHASE VIP AT .GG/KRONOS",
    Callback = function() print("Premium Action!") end
})

VIP:Toggle({
    Name = "God Mode",
    Premium = true,
    LockedTitle = "VIP ONLY",
    Callback = function(v) print("God Mode:", v) end
})

local ManualLock = PremiumTab:Section("Manual Control")

local TargetToggle = ManualLock:Toggle({
    Name = "Locked by Default",
    Description = "This can be unlocked via the button below."
})
TargetToggle:Lock()

ManualLock:Button({
    Name = "Unlock Toggle Above",
    Callback = function()
        TargetToggle:Unlock()
        Window:Notify({ Title = "System", Content = "Module unlocked successfully." })
    end
})

ManualLock:Button({
    Name = "Re-Lock Toggle Above",
    Callback = function()
        TargetToggle:Lock()
        Window:Notify({ Title = "System", Content = "Module locked." })
    end
})

-- ═══════════════════════════════════════════════════════════════
-- 8. DYNAMIC UPDATES & FEEDBACK
-- ═══════════════════════════════════════════════════════════════
local Feedback = CoreTab:Section("Live API Demo", { Boxed = true, Rounded = false })

local InfoCard = Feedback:Paragraph({
    Title = "Dynamic Property Update",
    Description = "This card's content will change in 10 seconds.",
    Icon = "info",
    Buttons = {
        ["Manual Update"] = function()
            PrecisionSlider:Update({
                Title = "Manually Updated!",
                Description = "You triggered an :Update() call on a slider element.",
                Icon = "check-circle"
            })
        end
    }
})

task.delay(10, function()
    InfoCard:Update({
        Title = "Auto-Updated!",
        Description = "This content was refreshed via the :Update() method after 10 seconds.",
        Icon = "check-circle"
    })

    FeatureToggle:Update({
        Name = "Renamed Toggle",
        Description = "Even interactive elements can be renamed on the fly."
    })
end)

-- ═══════════════════════════════════════════════════════════════
-- 9. VISIBILITY & RUNTIME API
-- ═══════════════════════════════════════════════════════════════
local RuntimeDemo = AdvancedTab:Section("Runtime API")

local HiddenSlider = RuntimeDemo:Slider({
    Name = "Hidden Slider",
    Description = "This slider is hidden by default.",
    Min = 0, Max = 50, Default = 25,
    Callback = function(v) print("Hidden Slider:", v) end
})
HiddenSlider:SetVisible(false)

RuntimeDemo:Button({
    Name = "Show Hidden Slider",
    Callback = function()
        HiddenSlider:SetVisible(true)
        Window:Notify({ Title = "Visibility", Content = "Slider is now visible!" })
    end
})

RuntimeDemo:Button({
    Name = "Hide Slider Again",
    Callback = function()
        HiddenSlider:SetVisible(false)
    end
})

RuntimeDemo:Button({
    Name = "Show Dialog",
    Callback = function()
        Window:Dialog({
            Title = "Confirm Action",
            Content = "Are you sure you want to proceed?",
            Buttons = {
                ["Yes"] = function()
                    Window:Notify({ Title = "Confirmed", Content = "Action completed." })
                end,
                ["No"] = function() end
            }
        })
    end
})

-- ═══════════════════════════════════════════════════════════════
-- 10. SETTINGS & THEMES
-- ═══════════════════════════════════════════════════════════════
local Styles = AppearanceTab:Section("Aesthetics")

Styles:Dropdown({
    Name = "Active Theme",
    Options = {"Batman", "Ocean", "Space", "Disco", "KronosRed", "KronosBlue", "KronosPurple", "KronosGreen"},
    Default = "Space",
    Callback = function(v) Kronos:SetTheme(v) end
})

Styles:Button({
    Name = "Toggle Background Image",
    Callback = function()
        local current = Window.Root:FindFirstChild("BackgroundImage")
        if current and current.Visible then
            Window:SetBackgroundImage(nil)
            Window:Notify({ Title = "Background", Content = "Background image removed." })
        else
            Window:SetBackgroundImage("rbxassetid://11419713314", 0.85)
            Window:Notify({ Title = "Background", Content = "Background image applied!" })
        end
    end
})

Styles:Button({
    Name = "Save Configuration",
    Callback = function()
        Window:Dialog({
            Title = "Save Configuration?",
            Content = "Do you want to save your current settings?",
            Buttons = {
                ["Yes"] = function()
                    Window:SaveSettings()
                    Window:Notify({ Title = "Saved", Content = "Configuration saved to disk." })
                end,
                ["No"] = function() end
            }
        })
    end
})

-- ═══════════════════════════════════════════════════════════════
-- 11. INITIAL NOTIFICATION
-- ═══════════════════════════════════════════════════════════════
Window:Notify({
    Title = "Kronos Initialized",
    Content = "All modules ready. Press RightControl to toggle UI.",
    Duration = 5
})

```
