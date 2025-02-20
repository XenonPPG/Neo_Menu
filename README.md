# Python Terminal Menu System

A Python library for creating interactive terminal menus with options, submenus (folders), and visual separators. This project supports two navigation modes:

- **Expanded Mode:** Displays the full menu tree with composite numbering (e.g., `1`, `1.1`, `1.1.1`).
- **Collapsed Mode:** Step-by-step navigation where folders open on demand and you can select "Back" to return to the previous level.

## Features

- **Dynamic Options:** Easily add actionable options with corresponding functions.
- **Submenus (Folders):** Organize your menu items in folders (submenus) with nested levels.
- **Visual Separators:** Improve readability with non-selectable separator lines.
- **Multiple Modes:** Choose between expanded (full tree) and collapsed (step-by-step) navigation.


## Example
```python
if __name__ == '__main__':
    menu = Menu("Test Menu", Color.LIGHTBLUE_EX, Color.CYAN, Color.LIGHTBLACK_EX, True)
    menu.add_option("Option 1", lambda: print("Action 1"))
    menu.add_option("Option 2", lambda: print("Action 2"))

    # Add a separator at the root
    menu.add_separator()

    # Create a folder with nested elements
    folder1 = menu.set_folder("Folder 1")
    menu.add_option("Option in Folder 1", lambda: print("Action in Folder 1"), folder1)
    menu.add_separator(folder1)
    subfolder = menu.set_folder("Subfolder", folder1)
    menu.add_option("Option in Subfolder", lambda: print("Action in Subfolder"), subfolder)

    # Create an empty folder (will display as <empty>)
    menu.set_folder("Empty Folder")

    # Run the menu in collapsed mode
    menu.show(collapsed=True, clear_console=True)
    # To test expanded mode, use:
    # menu.show(collapsed=False)
```