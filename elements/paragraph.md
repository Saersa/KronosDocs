# Paragraph

A rich information card used to display instructions, credits, or status updates. Supports icons and interactive buttons.

## Usage

```lua
local Info = Section:Paragraph({
    Title = "Support",
    Description = "Join our Discord for updates and help.",
    Icon = "info",
    Buttons = {
        ["Copy Link"] = function()
            setclipboard("discord.gg/kronos")
        end
    }
})
```

## Options

| Property | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `Title` / `Name` | string | `"Paragraph"` | Header text. |
| `Description` / `Content` / `Desc` | string | `""` | Main body text. |
| `Icon` | string | `nil` | Lucide icon name. |
| `IconSide` | string | `"Left"` | Icon placement (`"Left"` or `"Right"`). |
| `Thumbnail` | string | `nil` | Optional top banner image (`"Dynamic"` supported). |
| `ThumbnailHeight` | number | `100` | Banner height in pixels. |
| `ThumbnailSize` | UDim2 | `nil` | Optional banner size override. |
| `Image` | string | `nil` | Optional large content image. |
| `Buttons` | table | `{}` | Dictionary of `[ButtonText] = Callback` or `{ Callback, Color }`. |

## Methods

### `:Update(config)`
Dynamically updates the content. Perfect for live logs or status indicators.

```lua
Info:Update({
    Title = "Status: Online",
    Description = "Modules have been successfully hydrated.",
    Icon = "check-circle"
})
```

### `:SetVisible(boolean)`
Standard visibility control.

---

Next: [Slider](slider.md)
