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
    SubTitle    = "v1.1 - Production Ready",
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
    Name = "Auto Farm",
    Description = "Demonstrates the persistent config system.",
    ConfigId = "DemoAutoFarm", -- Unique ID for auto-saving
    Default = false,
    Callback = function(v) print("Auto Farm:", v) end
})

local PrecisionSlider = Basic:Slider({
    Name = "Walk Speed",
    Description = "Adjust numeric values with smooth dragging.",
    ConfigId = "DemoWalkSpeed",
    Min = 16, Max = 500, Default = 16,
    Suffix = " studs/s",
    Callback = function(v) print("WalkSpeed:", v) end
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
    Name = "Webhook URL",
    Description = "Persists across sessions via ConfigId.",
    ConfigId = "WebhookInput",
    Placeholder = "https://discord.com/api/webhooks/...",
    Callback = function(v) print("Webhook:", v) end
})

TextInputs:Input({
    Name = "Multi-Line Script",
    Description = "Perfect for code snippets.",
    Type = "Textarea",
    Placeholder = "print('Hello Kronos')",
    Callback = function(v) print("Script Content Updated") end
})

local Selection = InputTab:Section("Selection Menus", { Boxed = true })

local MainDropdown = Selection:Dropdown({
    Name = "Active Weapon",
    Description = "Search UI enabled by default.",
    ConfigId = "WeaponSelect",
    Options = {"Sword", "Bow", "Magic Staff"},
    Default = "Sword",
    Callback = function(v) print("Equipped:", v) end
})

Selection:Button({
    Name = "Refresh Shop List",
    Callback = function()
        MainDropdown:Refresh({"Greatsword", "Longbow", "Chaos Wand"}, true)
        Window:Notify({ Title = "Inventory", Content = "Shop list updated!" })
    end
})

Selection:MultiDropdown({
    Name = "Auto-Loot Filters",
    Description = "Select items to collect automatically (search disabled).",
    ConfigId = "LootFilters",
    Searchbar = false,
    Options = {"Gold", "Iron", "Wood", "Stone", "Potions"},
    Default = {"Gold", "Potions"},
    Callback = function(v) print("Looting:", table.concat(v, ", ")) end
})

-- ═══════════════════════════════════════════════════════════════
-- 6. ADVANCED & INTERACTIVE
-- ═══════════════════════════════════════════════════════════════
local Advanced = AdvancedTab:Section("Special Interaction")

Advanced:HoldButton({
    Name = "Self Destruct",
    Description = "Requires a 3-second hold to trigger.",
    Duration = 3,
    Callback = function()
        Window:Notify({ Title = "Boom", Content = "Self destruct activated!" })
    end
})

Advanced:Keybind({
    Name = "Menu Bind",
    ConfigId = "MenuToggleBind",
    Button = Enum.KeyCode.RightShift,
    Callback = function() print("Toggle Key Pressed!") end
})

Advanced:KeybindToggle({
    Name = "Fly (F)",
    ConfigId = "FlyToggleBind",
    Button = Enum.KeyCode.F,
    Callback = function(v) print("Flying:", v) end
})

Advanced:ColorPicker({
    Name = "Chams Color",
    Description = "Customizable ESP highlighting.",
    ConfigId = "ChamsColor",
    Default = Color3.fromRGB(0, 255, 255),
    Callback = function(v) print("ESP Color Updated") end
})

-- ═══════════════════════════════════════════════════════════════
-- 7. PREMIUM & LOCKING API
-- ═══════════════════════════════════════════════════════════════
local VIP = PremiumTab:Section("VIP Features", { Boxed = true })

VIP:Button({
    Name = "Instant Win",
    Premium = true,
    LockedTitle = "PURCHASE VIP AT .GG/KRONOS",
    Callback = function() print("Premium Action!") end
})

VIP:Toggle({
    Name = "Infinite Health",
    Premium = true,
    LockedTitle = "VIP ONLY",
    Callback = function(v) print("God Mode:", v) end
})

local ManualLock = PremiumTab:Section("Manual Control")

local TargetToggle = ManualLock:Toggle({
    Name = "Module Locked",
    Description = "This can be unlocked via the button below."
})
TargetToggle:Lock()

ManualLock:Button({
    Name = "Unlock Module",
    Callback = function()
        TargetToggle:Unlock()
        Window:Notify({ Title = "Security", Content = "Module unlocked." })
    end
})

-- ═══════════════════════════════════════════════════════════════
-- 8. DYNAMIC UPDATES & FEEDBACK
-- ═══════════════════════════════════════════════════════════════
local Feedback = CoreTab:Section("Live API Demo", { Boxed = true, Rounded = false })

local InfoCard = Feedback:Paragraph({
    Title = "Status Report",
    Description = "Waiting for data synchronization...",
    Icon = "refresh-cw",
    Buttons = {
        ["Sync Now"] = function()
            PrecisionSlider:Update({
                Title = "Speed Overridden",
                Description = "Value updated via external API call.",
                Icon = "zap"
            })
        end
    }
})

task.delay(10, function()
    InfoCard:Update({
        Title = "System Online",
        Description = "All modules synced with cloud database.",
        Icon = "check-circle"
    })
    
    FeatureToggle:Update({
        Name = "Auto Farm (Enabled)",
        Description = "The script is now actively gathering resources."
    })
end)

-- ═══════════════════════════════════════════════════════════════
-- 9. VISIBILITY & RUNTIME API
-- ═══════════════════════════════════════════════════════════════
local RuntimeDemo = AdvancedTab:Section("Runtime API")

local HiddenSlider = RuntimeDemo:Slider({
    Name = "Debug Value",
    Min = 0, Max = 100, Default = 0,
    Callback = function(v) end
})
HiddenSlider:SetVisible(false)

RuntimeDemo:Button({
    Name = "Show Debug Controls",
    Callback = function()
        HiddenSlider:SetVisible(true)
        Window:Notify({ Title = "Debug", Content = "Controls revealed." })
    end
})

RuntimeDemo:Button({
    Name = "Manual Dialog",
    Callback = function()
        Window:Dialog({
            Title = "Save Config?",
            Content = "Would you like to overwrite your existing settings?",
            Buttons = {
                ["Overwrite"] = function()
                    Window:SaveSettings()
                end,
                ["Cancel"] = function() end
            }
        })
    end
})

-- ═══════════════════════════════════════════════════════════════
-- 10. SETTINGS & THEMES
-- ═══════════════════════════════════════════════════════════════
local Styles = AppearanceTab:Section("Aesthetics")

Styles:Dropdown({
    Name = "UI Theme",
    Options = {"Batman", "Ocean", "Space", "Disco", "KronosRed", "KronosBlue", "KronosPurple", "KronosGreen"},
    Default = "Space",
    Callback = function(v) Kronos:SetTheme(v) end
})

Styles:Button({
    Name = "Set Background Image",
    Callback = function()
        Window:SetBackgroundImage("rbxassetid://11419713314", 0.85)
        Window:Notify({ Title = "Theme", Content = "Background updated!" })
    end
})

-- ═══════════════════════════════════════════════════════════════
-- 11. UNIVERSAL INDEX REFERENCE
-- ═══════════════════════════════════════════════════════════════
local IndexTab = Window:Tab({ Name = "Quick Index", Icon = "book-open" })
IndexTab:Index({
    Title = "Quick Index",
    Description = "Universal lookup for mobs, items, drops, XP, and notes.",
    Searchbar = true,
    Collapsible = true,
    DefaultCollapsed = true,
    Data = {
        {
            Name = "Goblin",
            Data = {
                Drops = "Gold, Leather",
                XP = "45",
                Notes = "Common early-game enemy"
            }
        },
        {
            Name = "Health Potion",
            Data = {
                Effect = "Restore 100 HP",
                Rarity = "Common",
                Location = "Shop"
            }
        },
        {
            Name = "Crystal Dragon",
            Data = {
                Drops = "Dragon Scale, Crystal Claw",
                XP = "1200",
                Rarity = "Boss"
            }
        }
    }
})

-- ═══════════════════════════════════════════════════════════════
-- 12. INITIAL NOTIFICATION
-- ═══════════════════════════════════════════════════════════════
Window:Notify({
    Title = "Kronos v1.1 Loaded",
    Content = "Premium UI initialized. Press RightControl to toggle.",
    Duration = 5
})
```
