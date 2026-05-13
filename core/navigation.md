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

### Direct Tab Elements
Tabs can also create elements directly. Kronos creates an internal default section automatically.

```lua
CombatTab:Toggle({ Name = "Enabled", Default = false })
```

## 3. Page Sections

Page sections are used to visually group elements within a tab. They create a titled box on the page.

```lua
local AimbotSettings = CombatTab:Section("Aimbot Settings")

-- Boxed variant (outlined card style)
local BoxedSection = CombatTab:Section("Advanced", { Boxed = true })
```

### Section Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Boxed` | boolean | `false` | Wraps the section in an outlined card. |
| `Rounded` | boolean | `true` | Enables rounded corners on boxed sections. |

## 4. Element Methods

Once a Page Section is created, you use it to add interactive elements:

| Method | Description |
| :--- | :--- |
| `Section:Button(...)` | A clickable action button. |
| `Section:Toggle(...)` | A boolean on/off switch. |
| `Section:Slider(...)` | A draggable numeric range. |
| `Section:Dropdown(...)` | A single-selection dropdown menu. |
| `Section:MultiDropdown(...)` | A multi-selection dropdown menu. |
| `Section:Input(...)` | A text input field (single or textarea). |
| `Section:ColorPicker(...)` | A color selection widget. |
| `Section:Keybind(...)` | A key binding assignment. |
| `Section:KeybindToggle(...)` | A keybind with an integrated toggle state. |
| `Section:HoldButton(...)` | A button that requires holding to activate. |
| `Section:Paragraph(...)` | A rich text info card with optional buttons. |
| `Section:Index(...)` | A searchable index/list panel element. |

### Tab-Level Methods

| Method | Description |
| :--- | :--- |
| `Tab:CreateConsole(options)` | Creates a [Console](../elements/console.md) that fills the entire tab. |

### Window-Level Methods

| Method | Description |
| :--- | :--- |
| `Window:Popout(options)` | Creates a [Popout panel](../advanced/popout.md) toggled from any callback. |

---

Next: [Elements Overview](../elements/README.md)
