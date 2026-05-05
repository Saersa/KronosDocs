# Paragraph

Paragraphs are versatile display elements used for instructions, descriptions, or information blocks. They support thumbnails and multiple action buttons.

## Usage

```lua
Section:CreateParagraph({
    Title = "Important Note",
    Content = "This is a paragraph with content, a thumbnail, and buttons.",
    Thumbnail = "rbxassetid://6031289329",
    Buttons = {
        ["Dismiss"] = function() print("Dismissed") end,
        ["Learn More"] = function() print("Opening link...") end
    }
})
```

## Options

| Property | Type | Description |
| :--- | :--- | :--- |
| `Title` | string | The bold title at the top. |
| `Content` | string | The main text body. |
| `Thumbnail` | string | (Optional) Asset ID for an image on the left. |
| `Buttons` | table | (Optional) Dictionary of `[Label] = Callback` for action buttons. |

---

Next: [Premium & Locking](../advanced/premium.md)
