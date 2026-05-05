# Navigation (Sections & Tabs)

Kronos uses a hierarchical navigation system to handle complex UIs with many features.

## 1. Sidebar Sections

Sidebar sections are used to group tabs into categories like "Combat", "Visuals", etc.

```lua
local CombatSection = Window:Section({ 
    Title = "Combat", 
    Icon = "swords" -- Supports Lucide icon names
})
```

### Options
- `Title`: The display name of the section.
- `Icon`: (Optional) The Lucide icon name to display next to the section title.

## 2. Tabs

Tabs are individual pages where elements are placed. They belong to a Sidebar Section.

```lua
local CombatTab = CombatSection:Tab({ 
    Name = "Aimbot", 
    Icon = "target" 
})
```

### Options
- `Name`: The display name of the tab.
- `Icon`: (Optional) The Lucide icon name for the tab.

## 3. Page Sections

Page sections are used to visually group elements within a tab. They create a titled box on the page.

```lua
local AimbotSettings = CombatTab:CreateSection("Aimbot Settings")
```

### Methods
Once a Page Section is created, you use it to add interactive elements:
- `AimbotSettings:CreateButton(...)`
- `AimbotSettings:CreateToggle(...)`
- ...and so on.

---

Next: [Elements Overview](../elements/README.md)
