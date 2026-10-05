# Menus

A menu gathers places to go and actions to take behind one button, and shows them in a panel when the reader presses it. The panel closes again as soon as the reader has chosen, or has turned to something else. An open menu is momentary, as a pointer resting over something is, so it is not part of the reader's restorable state, and everything it leads to has an address or an action of its own.

This section covers the menu button and its panel, the launcher, filtering a panel as the reader types, and summoning a panel with a key. A window's menu is a menu of this kind, and the windows section specifies what it holds.

## Anatomy

### The menu button

A menu button is a button, as the buttons section specifies, in either size, with the caret glyph at 12px after its label, drawn at 75% opacity. The caret says that pressing the button opens something rather than doing something. While its panel is open, the button is drawn pressed in, with the fill `raise-active-bg` and the shadow `raise-active-shadow`, as a latched toggle button is.

### The panel

The panel is lifted above the page, like a dialog without a backdrop, because it is not modal. It is filled with `dialog-bg`, bounded by a 1px line in `border`, has `radius` corners, and casts `shadow-card` together with a broad soft shadow of `shade`, 16px below it and blurred over 40px, at 1.6 times the strength `depth` sets. It has 6px of padding above and below its contents and none at the sides. It is at least 224px wide, and no wider than 352px or the window less 16px, whichever is smaller. It is no taller than 512px or the window less 16px, and when its contents are taller it scrolls. The panel sits above every other surface in the application.

A panel holds any of these, in this order from top to bottom.

- **A filter**, at the top, which narrows the panel's rows as the reader types into it. It is a sunken field, filled with `input-bg`, bounded by `input-border` with `radius-sm` corners and shadowed with `entry-shadow`, set at `text-sm` with 6px of padding above and below and 11px either side. It spans the panel less 10px at each side, with 4px above it and 6px below.
- **Section labels**, which group the rows beneath them, such as "Go to". A label is set at `text-2xs`, weight 700, in capitals spaced 0.06em apart, in `text-muted`, with 10px of padding above, 14px either side and 4px below, or 6px above when it is first in the panel.
- **Places**, each a row holding a link to a place. A place row is a list row, as a master-detail sidebar's rows are, so it is flat, responds under the pointer, and is not underlined. Its title is set at `text-sm` with a line height of 1.5, in `text`, on one line ending in an ellipsis when it is too long, with 5px of padding above and below and 14px either side.
- **A separator**, a 1px rule in `border` with 6px above and below, which sets the actions apart from the places.
- **Actions**, each a row that performs something when pressed. An action row is a list row as a place row is, flat and responding under the pointer. It leads with a glyph, 8px (`space-2`) before its label, and is set at `text-sm` with a line height of 1.5, with 6px of padding above and below and 14px either side. An action that destroys something, or cannot be undone, is set in `danger` and leads with the warning glyph, so its danger never rests on colour.

An action that switches something on and off shows the tick glyph at 12px before its label while it is on, and leaves the tick's space empty while it is off. In a panel with any such action, every other action leaves the same space empty, so that every label in the panel starts in one line.

A place row for the place the reader is in, or for a window that is in front, is marked current as a list row is, with a fill of `surface-alt`, a 3px `accent` edge on its end side and its title in weight 700.

When a filter leaves no row, the panel says so in a line of text, "Nothing matches." by default and in the application's own words where it gives them. The line is set at `text-sm` in `text-muted`, with 6px of padding above and below and 14px either side.

## Kinds

- A **menu** is a menu button and its panel, holding the places and actions that belong to one thing, such as a record.
- A **launcher** is a menu whose panel reaches everything an application offers, with one section for each category of place, a filter at the top, and the application's own actions at the foot. Its button comes first in the row that holds the window dock, and it stays on screen when a narrow layout shows one record, so the reader can reach everything from anywhere.
- A **filter menu** holds checkbox rows that filter a list, such as the categories or the sources a list shows. Each row is a checkbox and its words, set as a menu row, and choosing one applies the filter at once, without a button to confirm it. The panel stays open while the reader chooses, so several boxes can be ticked in a row: where applying the filter reloads the part of the page that holds the menu, the panel opens again on the new page with focus on the box the reader chose. Each box belongs to the filter's form, so the filter works without script as an ordinary form.
- A **summoned menu** is a panel that a key opens, as described under Interaction. It MAY have a button as well. A summoned menu with no button is a palette, opened near the top of the window.

## States

| State | Appearance |
|---|---|
| The menu button at rest | Raised, with the caret after its label |
| The menu button while its panel is open | Pressed in, until the panel closes |
| A row under the pointer | Filled with `surface-alt` |
| A row focused from the keyboard | Filled with `surface-alt`, with a 3px `accent` edge on its start side |
| The current place row | Filled with `surface-alt`, with a 3px `accent` edge on its end side and its title in weight 700 |
| An action switched on | The tick shows before its label |
| A disabled action | Its label in `text-muted`; it takes no presses and does not respond to the pointer |
| A destructive action | Its label in `danger`, led by the warning glyph |

A disabled action stays in the panel, so the reader learns that it exists.

## Interaction

### Opening and closing

Pressing a menu button with the pointer, or with the platform's usual keys, opens its panel, and pressing it again closes the panel. Down on a menu button opens the panel if it is closed and moves focus to its first row, or to its filter where it has one.

The panel closes when the reader chooses a place or an action in it, when they press Escape, or when they press anywhere outside it. When a panel closes while focus is inside it, focus returns to its menu button. A panel opens with its filter empty every time, whatever was typed into it before.

### Placement

A panel opens against its button, 4px away from it, below the button unless there is more room above it and the panel does not fit below. Its start edge lines up with the button's start edge, which is its left edge in a left-to-right layout and its right edge in a right-to-left one. It keeps 8px from every edge of the window, and when the room available is less than its height it takes the room available, down to 120px, and scrolls. While a panel is open it follows its button as the page scrolls and the window changes size.

A palette opens centred across the window, 15% of the window's height down from its top.

A panel that an application opens from something that is not its button, such as the maximise button of a window, is placed against that thing as it would be against a button.

An implementation MAY open a panel as a sheet across the full width of a narrow window, with a border only along its foot, `radius` corners only at its foot, and 10px of padding above and below each place row so the rows are large enough to tap. The web implementation does so on a window 640px wide or less, and opens a palette there at the window's top edge. Whether every platform must do the same is one of the questions below.

### Moving within the panel

Up and Down move focus between the panel's filter and rows, in order, stopping at the last. Up from the first moves focus back to the menu button. Home and End move focus to the first and the last, except in the filter, where they move within the typed text. Pressing a place goes to it, and pressing an action performs it.

### Filtering

As the reader types into a panel's filter, the panel shows only the rows whose text contains what has been typed, ignoring case, and hides a section label whose rows have all gone. When nothing is left, it shows its "Nothing matches" line. Enter in the filter goes to the first place left. With no place left, Enter hands the typed text to the application, which MAY take the reader to a page of its own for it, such as a "go to" page that finds a place by name.

A filter that narrows as the reader types needs no button to apply it, because there is nothing to apply.

### Summoning by key

A panel MAY be summoned by a single printable key, such as "/". Pressing that key, with no modifier, anywhere outside a field that takes text, opens the panel and puts focus in its filter, or on its first row where it has no filter. Inside a field that takes text, the key types as usual.

## Accessibility

A menu button is exposed as a button with its accessible name, and as expanded while its panel is open and collapsed while it is closed. A menu button whose panel can be summoned by a key also exposes that key as its keyboard shortcut.

The panel is exposed with an accessible name, such as the name of the thing it belongs to. Its place rows are exposed as links, and its actions as buttons. An action that switches something on and off is also exposed as pressed or not pressed, and a disabled action as disabled. The glyph that leads an action is not exposed, since its label says what it does, and a destructive action's label says what it destroys. The filter is exposed as a search field with an accessible name.

In the platform's high-contrast mode, the panel keeps a visible border, a menu button whose panel is open takes the system's highlight colours, and the caret and the tick are drawn in the system's text colours.

## Questions this section must settle

- Whether a panel exposes the menu role, with menu items, or a named group of links and buttons as the web implementation does today. The menu role brings a keyboard model and announcements the desktop platforms expect, and it fits a panel of places poorly.
- Whether a panel on a narrow screen becomes a sheet across the full width on every platform, and whether "narrow" is measured by the window, as it is today, or by the device.
- Whether a panel may hold another menu, opening to its side.
- Whether a panel's rows respond to type-ahead when it has no filter, as a tree's do.
- Whether the number of rows a filter leaves should be announced as the reader types.
- Whether a key that summons a panel may carry a modifier, and how an application avoids taking a key that assistive technology or the platform already uses.

## Conformance checklist

1. A menu button is a raised button with the caret glyph after its label, and it is drawn pressed in while its panel is open.
2. A menu button is exposed as expanded while its panel is open and as collapsed while it is closed.
3. A panel is lifted above every other surface, with no backdrop, and scrolls when its contents are taller than the room it has.
4. A panel opens against its button, below it or above it, aligned with the button's start edge and kept 8px from the window's edges.
5. Down on a menu button opens its panel and moves focus into it, and Up and Down move between the panel's filter and rows.
6. Choosing a place or an action, Escape, and a press outside the panel each close it, and focus inside a closing panel returns to its button.
7. Places and actions are flat list rows that respond under the pointer and are not underlined; actions are led by a drawn glyph and set apart from the places by a rule.
8. A destructive action is set in `danger` and led by the warning glyph.
9. An action that switches something on and off shows a tick while it is on, is exposed as pressed or not pressed, and keeps every label in the panel aligned.
10. A disabled action stays in the panel, takes no presses and is exposed as disabled.
11. A filter narrows the rows as the reader types, ignoring case, hides section labels left with no rows, and says so when nothing matches.
12. Enter in a filter goes to the first place left, and with none left hands the typed text to the application.
13. A panel opens with its filter empty.
14. A panel summoned by a key opens on that key outside a text field, with focus in its filter, and the key types as usual inside a text field.
15. An open menu is not part of the restorable state.
16. Choosing a row of a filter menu applies the filter at once, and the panel stays open, or opens again where the filter reloads what holds it, with focus on the same row.
