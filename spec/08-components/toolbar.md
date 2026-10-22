# Toolbars

A toolbar is a row of the commands a reader uses while working in something, such as the formatting commands of a page editor: the paragraph style, bold and italic, lists, what can be inserted, the link, and a table menu. It stands above or beside the work, and every control in it is raised, since every one is pressed, except a field, which is sunken because it is typed in.

## Anatomy

A toolbar holds **groups**, each a named set of controls that belong together: glyph buttons, menu buttons, small buttons with words, segmented controls and fields. Controls in a group are `space-1` apart, and groups are set apart by a 1px rule in `border` with `space-2` either side of it. A glyph button in a toolbar is the standalone 28px button with its glyph at 14px. A menu button there is the same button widened to hold the `caret` after its glyph.

A toolbar either wraps or folds. A **wrapping** toolbar puts its groups onto further lines when its row is too narrow, each group whole, so a group is never cut across a line. A **folding** toolbar keeps to one row, and as room runs out each group passes, one step at a time, through five stages:

1. The group's name, then each control with its glyph and its words.
2. The group's name, then each control as its glyph alone.
3. One menu button with the group's glyph and name, whose menu holds everything the group holds.
4. That menu button with its glyph alone.
5. A section, under the group's name, of a More menu at the row's end.

Every group reaches stage 2 before any reaches stage 3. After that, the groups of lower priority, and of equal priority the one furthest along the row, fold first. A group the application keeps at the row's end folds last. As the row widens the same steps run back. A group the application marks to stay whole never folds, and the others fold around it.

### Words and captions

A command shows its glyph and its words until folding takes the words. A command whose glyph nearly every reader already knows, such as bold, italic, underline, the lists, copy, the arrows and reload, MAY be marked to show its glyph alone at every stage; its words are then its accessible name and its tooltip. The application marks such commands, since only it knows which glyphs its readers know. A field shows its value, such as a font's name, and no label of its own.

A group's name is the words of its fold button, its accessible name and its tooltip. Whether the name also stands before the group, flat at `text-xs` and weight 600 in `text-muted`, as a **caption**, is chosen once for the whole toolbar by the application. Captions are shown unless the application says otherwise.

### What a fold menu holds

When a group folds, everything it holds reaches its menu, so nothing is lost by folding.

- A command becomes a row with its glyph and words that does what pressing the command does.
- A command that switches something on and off becomes a row with a tick that keeps the menu open, so several can be set in turn.
- A segmented control becomes rows of which one is ticked, under a heading with the control's name.
- A select becomes a row whose submenu holds its options, the current one ticked, and whose second line is the current choice.
- A set of keys that step a value, such as a stepper's minus and plus, becomes rows that keep the menu open, so the value can be stepped more than once.
- A text field, a search field or a combo box becomes a row that opens the field itself in a popover against the fold button, with focus in it, since a field typed into cannot be a menu row. The field goes back to the toolbar when the popover closes.
- A menu button becomes a row that opens its menu beside it as a submenu, with the menu's own headings and separators. A group that holds nothing but one menu button folds into that menu itself.

On a window 640px wide or less, where a submenu cannot stand beside its row, a row shows its submenu in the menu's place, with a Back row first, as a menu bar does when it folds.

## The command bar

A **command bar** is a folding toolbar whose first group holds a menu bar, drawn as the section on menu bars sets out: one raised surface with the `menu` glyph at its start and a flat title for each menu, the open one pressed in. The tool groups follow it in the same row. The menu group has the highest priority, so it folds last, into one menu button showing the `menu` glyph alone, whose menu holds one row for each menu, each opening that menu as a submenu.

Every tool's command SHOULD also be in a menu, so a reader who never uses the tools still has every command. A tool group therefore folds into a menu button of its own and never into the menu its commands also live in, since a reader would see no sign that the group had moved.

While one of the command bar's menus is open, Left and Right open the menu before or after it, and the pointer moving onto another title opens that title's menu, as in a menu bar.

## States

The controls have the states of their own sections. A control whose state the cursor is in, such as Bold while the cursor is in bold text, is **latched**: it is drawn pressed in, as a toggle button latched on is, and exposed as pressed. A menu button whose every command is disabled is disabled with them, so the toolbar never shows a button that can do nothing, and is enabled again as soon as a command is.

## Interaction

The toolbar is one stop in the keyboard's tab order, on the control last used or else the first. Left and Right move focus along the toolbar's enabled controls, across every group, from the last back to the first; Home and End move to the first and last; Tab leaves the toolbar; and each control responds to its own keys. A disabled control, and a control a fold has put out of sight, is skipped. In a right-to-left page the arrows follow the reading direction.

A field is a tab stop of its own, as in a form. Left and Right move its caret; Left with the caret at the field's start moves to the control before it, and Right at its end to the control after it.

## Accessibility

The toolbar is exposed as a toolbar named for what it holds, each group as a group named for what it does, each control with its own name and state, and a latched control as pressed. A fold button is a menu button named for its group. In the platform's high-contrast mode the controls keep their borders and a latched control takes the system's highlight colours, as a latched toggle button does.

## Conformance checklist

1. A toolbar's controls are raised, grouped `space-1` apart in groups set apart by a hairline; a wrapping toolbar wraps with groups whole.
2. A latched control is pressed in and exposed as pressed; a menu button with only disabled commands is disabled.
3. The toolbar is one tab stop, Left and Right move along its enabled controls in sight from end to end, Home and End move to the ends, a disabled control is skipped, and a field is a tab stop of its own that its edges leave by the arrows.
4. The toolbar, its groups and its controls are exposed with their roles and names.
5. A folding toolbar keeps to one row, its groups passing through the five stages in the order this section sets out, and back as the row widens.
6. A command marked to show its glyph alone does so at every stage, with its words as its accessible name and tooltip; captions show or not as the application chose for the whole toolbar.
7. A fold menu holds everything its group holds: commands, ticked switches that keep the menu open, ticked choices under a heading, a select's options in a submenu, stepping rows that keep the menu open, fields in a popover, and menus as submenus, shown in place with a Back row on a narrow window.
8. A command bar's menu group is a menu bar, folds last into the `menu` glyph alone, and its menus open beside their rows when folded; Left and Right and the pointer move between its open menus.
