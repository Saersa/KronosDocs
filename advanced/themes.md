# Theming

Kronos supports dynamic themes and accent colors to allow users to personalize their experience.

## Switching Themes

You can change the theme at any time using the `SetTheme` method.

```lua
Kronos:SetTheme("KronosBlue")
```

## Built-in Themes
- `KronosRed` (Default)
- `KronosBlue`
- `KronosPurple`
- `KronosGreen`

## Getting Available Themes

To populate a dropdown with all available themes:

```lua
local Themes = Kronos:GetThemes() -- Returns a list of theme names
```

## Custom Themes

You can add your own themes by providing a color table to `Kronos:AddTheme`.

```lua
Kronos:AddTheme({
    Name = "Ocean",
    Accent = Color3.fromRGB(0, 150, 255),
    Background = Color3.fromRGB(15, 15, 20),
    -- ... more colors
})
```

---

Next: [Notifications](notifications.md)
