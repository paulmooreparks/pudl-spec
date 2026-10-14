# Toolbars

A toolbar is a row of the commands a reader uses while working in something, such as the formatting commands of a page editor: the paragraph style, bold and italic, lists, what can be inserted, the link, and a table menu. It stands above or beside the work, and every control in it is raised, since every one is pressed.

## Anatomy

A toolbar holds **groups**, each a named set of controls that belong together: glyph buttons, menu buttons, and small buttons with words. Controls in a group are `space-1` apart, and groups are set apart by a 1px rule in `border` with `space-2` either side of it. A glyph button in a toolbar is the standalone 28px button with its glyph at 14px. A menu button there is the same button widened to hold the `caret` after its glyph. When the toolbar's row is too narrow, the groups wrap onto further lines, each group whole, so a group is never cut across a line.

A control whose state the cursor is in, such as Bold while the cursor is in bold text, is **latched**: it is drawn pressed in, as a toggle button latched on is, and exposed as pressed. A menu button whose every command is disabled is disabled with them, so the toolbar never shows a button that can do nothing, and is enabled again as soon as a command is.

## States

The controls have the states of their own sections. A latched control is pressed in until its state ends.

## Interaction

The toolbar is one stop in the keyboard's tab order, on the control last used or else the first. Left and Right move focus along the toolbar's enabled controls, across every group, from the last back to the first; Home and End move to the first and last; Tab leaves the toolbar; and each control responds to its own keys. A disabled control is skipped. In a right-to-left page the arrows follow the reading direction.

## Accessibility

The toolbar is exposed as a toolbar named for what it holds, each group as a group named for what it does, each control with its own name and state, and a latched control as pressed. In the platform's high-contrast mode the controls keep their borders and a latched control takes the system's highlight colours, as a latched toggle button does.

## Questions this section must settle

- Whether a toolbar may hold a field, such as a search field, and how the arrow keys treat it.
- Whether a toolbar too narrow for its groups should collapse into a menu, as the menu bar does, rather than wrap.

## Conformance checklist

1. A toolbar's controls are raised, grouped `space-1` apart in groups set apart by a hairline, and wrap with groups whole.
2. A latched control is pressed in and exposed as pressed; a menu button with only disabled commands is disabled.
3. The toolbar is one tab stop, Left and Right move along its enabled controls from end to end, Home and End move to the ends, and a disabled control is skipped.
4. The toolbar, its groups and its controls are exposed with their roles and names.
