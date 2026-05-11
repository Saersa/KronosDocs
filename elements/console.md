# Console

The Console is a specialized component that allows you to output logs, status messages, and debug information directly within the UI. It takes over the entire content area of the Tab it is created in.

## Usage

To create a console, call `CreateConsole` on a Tab instance. 

> [!WARNING]
> Initializing a Console will hide all other elements in that Tab. It is recommended to dedicate a specific Tab solely for the Console.

```lua
local ConsoleTab = Window:Tab({ Name = "Logs", Icon = "terminal" })

local Console = ConsoleTab:CreateConsole({
    AutoScroll = true
})
```

### Options

| Parameter | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `AutoScroll` | boolean | `true` | Automatically scroll to the bottom when new lines are added. |

## Methods

### AddLine

Adds a new line to the console.

```lua
Console:AddLine({
    "My Message",
    Type = "Info", -- Message, Info, Warning, Error
    Color = Color3.fromRGB(255, 255, 255) -- Optional override
})
```

**Log Types:**
*   `Message`: Standard text.
*   `Info`: Uses the theme's Accent color.
*   `Warning`: Yellow/Orange text for alerts.
*   `Error`: Red text for critical failures.

### ClearAll

Clears all lines from the console with a smooth transition.

```lua
Console:ClearAll()
```

### RemoveLine

Removes a specific line based on its order or index.

```lua
Console:RemoveLine({ LineToRemove = 1 })
```

---

Next: [Keybind](keybind.md)
