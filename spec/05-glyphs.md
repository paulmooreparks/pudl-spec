# 5. Glyphs

A glyph is a small drawn shape that carries meaning, such as the triangle on a warning badge or the cross on a close button. PUDL's glyphs are in `glyphs/`, one SVG file each, and every glyph an implementation draws in PUDL's chrome MUST be one of them.

## How a glyph is drawn

Each glyph is drawn on a grid of 16 by 16 units, in black, with fills and strokes only. An implementation draws it as a mask filled with the colour of the text beside it, so that a glyph always takes the colour of its context and follows the theme. By default it is as tall as the text beside it, and a component MAY set another size, which its section in chapter 8 names.

A glyph is never a character from a font. A character can fall back to another face, render as a colour emoji or be missing altogether, and then it no longer means what it did. A platform that has no way to draw vector shapes is the one exception, and the question at the end of this chapter covers it.

A glyph that stands beside words saying the same thing is decoration to assistive technology, and MUST be hidden from it. A glyph that stands alone, such as the only content of a button, MUST have an accessible name that says what it means.

## The glyphs and their meanings

### Status

Each status colour has a glyph of its own, so that a status is never told by colour alone, as chapter 2 requires. A status badge carries the shape; a notice or a toast, which has more room, carries the fuller glyph.

| Status | Badge | Notice and toast |
|---|---|---|
| Needs attention (`warn`) | `triangle` | `warning` |
| Failed or destructive (`danger`) | `square` | `stop` |
| Done (`positive`) | `circle` | `check` |
| The accent | `diamond` | |
| Information | | `info` |

`warning` also marks a field's error message.

### Windows and panes

| Glyph | Meaning |
|---|---|
| `minimize` | Minimise a window, or collapse a docked one |
| `maximize` | Maximise a window |
| `restore` | Restore a maximised or snapped window |
| `close` | Close a window, a tab, a notice or a chip |
| `open` | Open the window's content as a page of its own |
| `dock` | Dock a window at the foot of the workspace |
| `undock` | Float a docked window again |
| `caret` | Open a menu, including a window's menu, and a select's list |
| `branch` | A child window's row beneath its parent in a list |
| `circle` | The dock tab of a window that is showing, and a document tab with unsaved changes |
| `ring` | The dock tab of a minimised window |

### Actions and places

| Glyph | Meaning |
|---|---|
| `search` | Search or filter |
| `back` | Go back to the list from a record |
| `copy` | Copy to the clipboard |
| `download` | Download a file |
| `gear` | Settings, or the commands an applet offers |
| `menu` | A menu bar's menus, and the menu bar as one button when it does not fit |
| `pin` | A menu bar's pins group, the items a reader has pinned |
| `comments` | Comments and messages, such as a status item for a queue of them |
| `account` | A person's account where it has no picture, drawn at the picture's size, such as the reader's account in the status area |
| `theme` | Switch between the light and dark themes |
| `tick` | A menu command that is switched on |
| `sort`, `sort-up`, `sort-down` | A column that can be sorted, and one sorted ascending or descending |
| `slash` | The separator between the places in a path |
| `grip` | A handle the reader drags, such as the one between two panes |
| `home` | The top of a hierarchy |
| `empty` | Nothing to show, in an empty state |

### Kinds of thing

These mark what an item in a list is, in file managers, document lists and attachments. They carry no colour of their own, because the shape says the kind, and the status colours stay free to mean status.

| Glyph | Kind |
|---|---|
| `folder` | A folder |
| `file` | A file of no particular kind |
| `document` | A document to read |
| `app` | An application |
| `script` | A script or a program's source |
| `link` | A link to somewhere else |

## Adding a glyph

A glyph is added to the language by adding its file here, drawn to the same grid and stroke weights as the others, with its meaning in this chapter. An application that needs a shape PUDL does not have MAY draw its own in the same manner, and SHOULD propose it here if others would need it too.

## Questions this chapter must settle

- What a platform that can only show characters, such as a terminal, draws for each glyph. The rule above against font characters needs a stated exception for it, with safeguards of its own, such as a fixed set of characters known to render in the common terminals.
- Whether `circle` and `ring` should have names of their own for the unsaved and minimised states, so that a platform can draw them differently from the status circle.
