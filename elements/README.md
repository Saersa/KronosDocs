# Elements Overview

Elements are the interactive components of your UI. All elements are added to a **Page Section**.

## Common Features

Most elements support the following properties:

- `Name`: The label for the element.
- `Description`: (Optional) Subtext explaining the feature.
- `Locked`: (Optional) If true, the element is visually locked and unclickable.
- `Premium`: (Optional) If true, automatically locks if the user does not have a premium subscription.
- `ConfigId`: (Optional) A unique string for the configuration system to save/load the value.

## Available Elements

### Inputs
- [Button](button.md): Standard click action.
- [Hold Button](button.md#hold-button): Requires holding for a duration.
- [Toggle](toggle.md): Boolean switch.
- [Slider](slider.md): Range selector.
- [Dropdown](dropdown.md): Single selection list.
- [Multi Dropdown](dropdown.md#multi-dropdown): Multiple selection list.
- [Color Picker](colorpicker.md): RGB color selector.

### Keybinds
- [Keybind](keybind.md): Standard key trigger.
- [Keybind Toggle](keybind.md#keybind-toggle): A toggle controlled by a key.

### Display
- [Paragraph](paragraph.md): Formatted text with support for icons and buttons.

---

Next: [Buttons](button.md)
