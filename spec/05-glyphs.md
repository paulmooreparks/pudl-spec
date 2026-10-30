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
| `window` | A window's menu, before the button's `caret` |
| `minimize-all` | Minimise every window, a screen with a chevron pointing down |
| `restore-all` | Restore every minimised window, the screen with the chevron pointing up |
| `close-all` | Close every window, two windows stacked with a cross on the front one |
| `more` | A row's actions button, which opens the row's context menu: three dots in a row |
| `branch` | A child window's row beneath its parent in a list. For a line of work that splits off, as in version control, use `fork` |
| `circle` | The dock tab of a window that is showing, and a document tab with unsaved changes |
| `ring` | The dock tab of a minimised window |

### Actions and places

| Glyph | Meaning |
|---|---|
| `search` | Search or filter |
| `back` | Go back to the list from a record, or to the previous page, month or item |
| `forward` | Go on to the next page, month or item; `back` mirrored without turning a glyph |
| `eye` | Show what is hidden, such as a password |
| `eye-off` | Hide it again; the eye struck through |
| `copy` | Copy to the clipboard |
| `pencil` | Edit or rename something in place |
| `reload` | Load what is shown again, as a browser's reload does |
| `flag` | Something marked or reported for attention, such as reports of abuse |
| `inbox` | Items waiting to be dealt with, such as drafts waiting for review |
| `shield` | Protection, security or moderation |
| `terminal` | A command line or console, where `script` is a program's source |
| `plus` | Add one, or zoom in: a row to a list, a step of scale; and, as a state, something added, such as an added line in a diff or an added file |
| `minus` | Take one away, or zoom out; and, as a state, something removed |
| `arrow-up`, `arrow-down` | Move something up or down, such as a step in a list; a chevron says direction, an arrow with a stem says movement |
| `new-window` | Open something in a window of its own, where `open` means go to its page |
| `pencil-off` | A place that cannot be written to, such as a read-only folder; `shield` marks what needs elevation |

### Editing text

The commands of a page editor's toolbar, each the mark its command leaves or the thing it inserts.

| Glyph | Meaning |
|---|---|
| `bold`, `italic`, `underline`, `strike`, `code` | The text's treatment |
| `list`, `list-numbered` | A bulleted and a numbered list |
| `quote` | A quotation |
| `table` | A table, and the table commands |
| `panel` | A panel inserted into the page, such as a note or a warning |
| `colour` | A colour to choose, such as a cell's |
| `paragraph` | The paragraph's style, such as a heading level |
| `image` | Insert a picture |
| `clip` | Attach a file |
| `download` | Bring something here from elsewhere, such as downloading a file or pulling changes |
| `upload` | Send something from here to elsewhere, such as uploading a file or pushing changes |
| `gear` | Settings, or the commands an applet offers |
| `menu` | A menu bar's menus, and the menu bar as one button when it does not fit |
| `ribbon` | A ribbon's tools shown as a row under its tabs, on the Show as ribbon toggle |
| `pin` | A menu bar's pins group, the items a reader has pinned |
| `comments` | Comments and messages, such as a status item for a queue of them |
| `account` | A person's account where it has no picture, drawn at the picture's size, such as the reader's account in the status area |
| `chevron` | A disclosure button: content shown or hidden in place, pointing down while hidden and up while shown |
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
| `board` | A project, a board or a backlog, such as a tracker's project |
| `ticket` | An issue, a task or a request in a tracker |

### Versions and changes

These mark the history of a body of work, in version control and in anything else that keeps versions, such as a wiki's page history or a document's revisions.

| Glyph | Meaning |
|---|---|
| `commit` | A saved revision of a body of work, such as a commit or a version |
| `fork` | A line of work that splits from another, such as a branch in version control or a copy of a repository |
| `merge` | Two lines of work joined into one |
| `tag` | A label fixed to one thing to find it again, such as a release tag or a note's tag |
| `stash` | Work set aside, to be taken up again later |
| `history` | The earlier states of something, in time order |
| `compare` | Two versions shown together to see what changed, such as a diff |
| `move` | Moved from one place to another, such as a renamed file or one moved between folders |

## Adding a glyph

A glyph is added to the language by adding its file here, drawn to the same grid and stroke weights as the others, with its meaning in this chapter. An application that needs a shape PUDL does not have MAY draw its own in the same manner, and SHOULD propose it here if others would need it too.

## Questions this chapter must settle

- What a platform that can only show characters, such as a terminal, draws for each glyph. The rule above against font characters needs a stated exception for it, with safeguards of its own, such as a fixed set of characters known to render in the common terminals.
- Whether `circle` and `ring` should have names of their own for the unsaved and minimised states, so that a platform can draw them differently from the status circle.

## Execution states

Working uses the open arc `working`, Waiting uses `flag`, Stuck uses `warning`, and Idle uses the hollow `ring`. Working may rotate, but remains an open arc when reduced motion stops animation. These glyphs are distinct without colour. Their semantic colours are accent, warn, danger and text-muted respectively.
