# Splitters

A splitter divides a component into two panes and lets the reader move the boundary between them, such as a folder tree beside a file list or an editor above a terminal. The divider of a [master-detail layout](master-detail.md) is a splitter with limits of its own.

## Anatomy

A splitter holds two panes and a handle between them. The panes sit side by side, or one above the other, which is the stacked form. Each pane scrolls on its own.

The handle resizes the first pane, the one at the start of the reading direction or at the top, and the second pane takes whatever is left. The first pane's size is set in px; until the reader or the application sets it, the application's default applies, and without one the panes share the space equally.

The reader drags the handle rather than pressing it, so it is a handle in chapter 2's sense and is drawn flat. Its grip is 6px across and straddles the boundary, 3px into each pane, so that it can be taken without covering either pane's content. At the middle of the boundary the handle carries the `grip` glyph at 16px in `text-muted`, turned a quarter where the panes are stacked so that its dots run along the boundary. The glyph shows at rest, so a reader can find the handle without a pointer resting on it.

Inside the grip the handle draws a 1px rule in `border` with rounded ends, running the full length of the boundary. The rule remains visible at rest, with the grip glyph at its center.

The handle has two limits. The least the first pane may be is 80px unless the application sets another. The most it may be is set by the application in px or as a share of the splitter, and is by default the whole splitter less the least, so that the second pane never vanishes. The limits hold however the size was set, and a size beyond a limit is brought back within it when the splitter itself changes size.

## States

| State | Appearance |
|---|---|
| At rest | Flat; the `grip` glyph shows in `text-muted`, and the rule shows in `border` |
| Under the pointer | The glyph and the rule are drawn in `accent` |
| Dragged | The glyph and the rule are drawn in `accent` until the pointer lifts |
| Focused from the keyboard | The glyph and the rule are drawn in `accent`, with a 3px ring in `focus-ring` around the rule |

## Interaction

Dragging the handle moves the boundary, and the first pane follows the pointer, held within its limits. In a right-to-left interface the first pane of a side-by-side splitter is at the right, so the handle widens it by moving left.

The handle is one stop in the keyboard's tab order. With it focused:

| Keys | Effect |
|---|---|
| The two arrow keys along its axis, Left and Right or Up and Down | Move the boundary 16px |
| The same keys with Shift | Move the boundary 64px |
| Home and End | Take the first pane to its least and its most |
| Enter | Return to the default size |

A double-click on the handle also returns it to the default size.

When a change ends, at the end of a drag or once the keys have been quiet for a moment, the application is told the new size, or that the size returned to the default. The implementation does not remember the size between visits. An application that wants it remembered stores it and applies it before the splitter is first drawn, so the reader never sees the default size jump to theirs. Whether such a size is part of the state the reader returns to is a question for chapter 7.

## Accessibility

The handle is exposed as a separator, oriented across the boundary: vertical when the panes sit side by side and horizontal when they are stacked. It controls the first pane, and it has an accessible name that says which pane it resizes, such as "Resize the folders". It exposes its value, its least and its most in px, and a spoken form of its value in the application's own words, "240 pixels" by default.

The glyph is drawn and is not exposed, since the separator's role and name already say what it is.

In the platform's high-contrast mode the rule and the glyph are drawn at rest in the system's text colour, and in its highlight colour while hovered, dragged or focused.

## Questions this section must settle

- The size of the grip on a touch screen, where 6px is narrow for a finger. Chapter 6 holds the minimum target size.

## Conformance checklist

1. A splitter lays out two panes side by side or stacked, and the handle resizes the first.
2. Without a size set, the panes share the space equally.
3. The first pane never goes below its least, 80px by default, and the second pane never vanishes, however the size was set and whatever size the splitter becomes.
4. The handle is flat and shows the `grip` glyph in `text-muted` at rest.
5. The glyph and the rule take `accent` under the pointer, while dragged and while focused, and focus adds a 3px `focus-ring`.
6. The handle is one tab stop; the arrow keys along its axis move it 16px, 64px with Shift, Home and End take it to its limits, and Enter returns it to the default.
7. A double-click returns it to the default.
8. The application is told the size when a change ends, and told when it returns to the default.
9. The handle is exposed as a separator with the right orientation, a name, and its value, least and most.
10. In a right-to-left interface a side-by-side splitter's first pane is at the right, and the handle and its keys follow it.
11. In high-contrast mode the rule and the glyph are visible at rest.
