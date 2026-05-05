# Theming

Kronos features a robust theming engine with multiple premium palettes.

## Built-in Themes

| Theme | Aesthetic |
| :--- | :--- |
| `Batman` | Dark blue and matte black with neon teal accents. |
| `Ocean` | Deep sea blue with soft cyan highlights. |
| `Space` | Midnight purple with vibrant violet accents. |
| `Disco` | High-contrast dark mode with neon pink highlights. |
| `KronosRed` | Official branding (Red/Black). |
| `KronosBlue` | Official branding (Blue/Black). |
| `KronosPurple` | Official branding (Purple/Black). |
| `KronosGreen` | Official branding (Green/Black). |

## Usage

### At Initialization
```lua
local Window = Kronos:CreateWindow({
    Theme = "Space"
})
```

### At Runtime
```lua
Kronos:SetTheme("Batman")
```

## Creating Custom Themes

You can register your own color palettes using `Kronos:AddTheme`:

```lua
Kronos:AddTheme({
    Name = "MyTheme",
    Main = Color3.fromRGB(20, 20, 20),
    Accent = Color3.fromRGB(255, 100, 0),
    -- See Theme module for full color table keys
})
```

---

Next: [Notifications](notifications.md)
