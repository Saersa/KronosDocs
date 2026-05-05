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
| `Title` | string | | Bold header text. |
| `Description` | string | | Main body text. |
| `Icon` | string | `nil` | Lucide icon name. |
| `Buttons` | table | `{}` | Dictionary of `[ButtonText] = Callback`. |

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
