# Popout Panels

Popout panels are side-extending windows that slide out from the main UI. They are ideal for consoles, logs, data viewers, or any secondary interface that shouldn't take up a full tab.

## Creating a Popout

Popouts are created via `Window:Popout()`. They start **hidden** and are controlled via `:Open()`, `:Close()`, or `:Toggle()`.

```lua
local Pop = Window:Popout({
    Title    = "Side Console",
    Position = "right",       -- "left", "right", "top", "bottom"
    Size     = Vector2.new(250, 300)
})
```

### Options

| Property       | Type    | Default   | Description                                                        |
| :------------- | :------ | :-------- | :----------------------------------------------------------------- |
| `Title`        | string  | `"Popout"` | Header title of the popout panel.                                  |
| `Position`     | string  | `"right"` | Which side of the window to extend from.                           |
| `Size`         | Vector2 | auto      | Dimensions of the popout panel.                                    |
| `Transparency` | number  | `0`       | Background transparency of the panel.                              |
| `Data`         | table   | `nil`     | Optional data table to render as an Index inside the popout.       |

## Toggling from a Button

The recommended pattern is to create the popout once at setup, then toggle it from any button callback:

```lua
-- Create popout once
local Pop = Window:Popout({
    Title    = "Side Console",
    Position = "right",
    Size     = Vector2.new(250, 300)
})

local Console = Pop:CreateConsole({ AutoScroll = true })
Console:AddLine({ "Console ready.", Type = "Info" })

-- Toggle from any section button
local Advanced = AdvancedTab:Section("Tools")

Advanced:Button({
    Name = "Toggle Console",
    Description = "Opens the side console panel.",
    Callback = function()
        Pop:Toggle()
    end
})
```

## Methods

| Method                      | Description                                                        |
| :-------------------------- | :----------------------------------------------------------------- |
| `Pop:Open()`                | Animates the popout open from the main window.                     |
| `Pop:Close()`               | Animates the popout closed back into the main window.              |
| `Pop:Toggle()`              | Opens if closed, closes if open.                                   |
| `Pop:CreateConsole(options)` | Adds a [Console](../elements/console.md) inside the popout.       |
| `Pop:RemoveConsole()`       | Removes the console and clears the content area.                   |
| `Pop:Update(options)`       | Updates title, size, position, or data at runtime.                 |

### Update Options

```lua
Pop:Update({
    Title    = "New Title",
    Size     = Vector2.new(300, 400),
    Position = "left",
    Data     = { ... } -- Replaces content with an Index view
})
```

## Behavior

### Window Sync
- The popout **follows** the main window when it is dragged.
- The popout **hides** automatically when the main window is minimized or toggled off.
- The popout **closes** when the main window is toggled via keybind.

### Animation
- **Open**: Slides out from the edge of the main window with a fade-in.
- **Close**: Slides back into the main window with a fade-out.
- Uses `CanvasGroup` for a seamless visual extension effect.

### Close Button
Each popout includes a built-in **X** button in the header that calls `:Close()`.

## Console in Popout

```lua
local Pop = Window:Popout({
    Title    = "Event Log",
    Position = "right",
    Size     = Vector2.new(250, 300)
})

local Log = Pop:CreateConsole({ AutoScroll = true })

Log:AddLine({ "System initialized.", Type = "Info" })
Log:AddLine({ "Monitoring events...", Type = "Message" })

-- Feed real-time data
task.spawn(function()
    while task.wait(5) do
        if Pop.Visible then
            Log:AddLine({ "Heartbeat: " .. os.clock(), Type = "Info" })
        end
    end
end)
```

## Data View in Popout

Instead of a console, you can display structured data using the Index renderer:

```lua
local Pop = Window:Popout({
    Title = "Player Stats",
    Position = "left",
    Size = Vector2.new(220, 250),
    Data = {
        { Name = "Health", Data = { Current = "100", Max = "100" } },
        { Name = "Mana",   Data = { Current = "50",  Max = "75"  } }
    }
})
```

---

Next: [Configuration](config.md)
