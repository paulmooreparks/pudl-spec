# Master-detail layouts

A master-detail layout shows a list of records beside the one record the reader has chosen from it. It is the primary layout for an application that works through records one at a time, such as expenses, articles or files, and the reader moves through the list without losing sight of where they are in it. On a narrow screen the same layout shows one pane at a time.

## Anatomy

A master-detail layout fills the area it is given and is made of four parts, from top to bottom and then from the start of the reading direction to its end.

- A toolbar, holding what acts on the list.
- A row of filter chips, one for each filter in force.
- A sidebar, holding the list.
- A detail pane, holding the record, with a divider between it and the sidebar.

The toolbar is a flat band of `surface` with a 1px hairline in `border` along its foot, padded 8px above and below and 16px at each end, with 10px between the things it holds. Every control in it is 30px tall, so that small buttons, segmented controls and fields line up. It MAY hold a filter field, which is sunken like any field, 220px wide, with its text at `text-sm`; a filter that applies when submitted joins the field to a raised glyph button, 32px wide, carrying the `search` glyph, drawn so that the sunken field meets the raised button with no gap. Groups of commands in the toolbar are 6px apart and MAY be divided by a 1px rule in `border` the height of a control. The toolbar SHOULD hold at most one primary button, as chapter 2 requires of any visible context.

The chip row is a flat band of `surface` with a hairline in `border` along its foot, padded 8px by 16px, with 6px between chips. It holds a filter chip for each filter in force and MAY end in a link that clears them all. A chip row with no chips takes no space.

The sidebar is a flat band of `surface` with a 1px hairline in `border` on the side that faces the detail pane, and it scrolls on its own. Its width is the reader's preferred width held between two limits, 180px by default at the least and half the layout at the most, and its preferred width is 260px until the reader moves the divider. The limits hold however the width was set, and they still hold when the layout narrows after the width was chosen.

The list in the sidebar is made of section labels and rows.

- A **section label** heads a group of rows. It is set at `text-2xs`, weight 700, in capitals spaced 0.06em apart, in `text-muted`, with 14px above it and at its sides and 4px below.
- A **row** is one link to its record. The rows are a list of places, the category chapter 2 describes, so each row is flat, responds under the pointer, and is not underlined. Its title is set at `text-sm` in `text`, on one line, padded 5px above and below and 14px at the sides, and it ends in an ellipsis when the sidebar is too narrow for it. Beneath the title a row MAY carry any number of metadata lines, such as a date and then a description, set at `text-2xs`, weight 500, in `text-muted`. Metadata lines wrap rather than being cut short, since the ellipsis marks the end of only the title's line. Rows are divided by a 1px line in `surface-alt`, and numbers in them are tabular.

The detail pane fills the rest of the layout. It is `bg`, padded 24px, and scrolls on its own.

The divider sits on the boundary between the sidebar and the detail pane, over the sidebar's hairline. It is drawn and behaves as a splitter's handle, which [its own section](splitters.md) specifies: it is flat, and it carries the `grip` glyph in `text-muted` at rest. The differences are listed under Interaction below.

## States

| Part | State | Appearance |
|---|---|---|
| Row | At rest | Flat on `surface` |
| Row | Under the pointer | Filled with `surface-alt` |
| Row | Current, the record in the detail pane | Filled with `surface-alt`, a 3px edge in `accent` on the side facing the detail pane, and the title at weight 700 |
| Row | Focused from the keyboard | The focus ring of a link, in addition to its other state |
| Chip row | No filters in force | Takes no space |
| Divider | At rest | Flat; the `grip` glyph shows in `text-muted` on the sidebar's hairline, and the rule is unseen |
| Divider | Under the pointer, while dragged, or focused | The glyph and a rule in `accent`, with a 3px ring in `focus-ring` while focused |
| Detail pane | Focused from the keyboard | A 3px ring in `focus-ring` drawn inside its edge |

The current row carries three signals besides its colour: the edge, the weight of its title and its position beside the record it names. It MUST be exposed as the current item.

## Interaction

Choosing a row shows its record in the detail pane. The record in view is part of the state the reader can return to, as chapter 7 describes, and so are the filters in force; the list's scroll position is not.

The detail pane is a stop in the tab order, so that a reader with only a keyboard can scroll a record that has no link or field inside it.

The divider differs from a plain splitter in four ways. Its limits come from the layout, as set out under Anatomy, rather than from the divider itself. Its default size is the sidebar's preferred width, and a double-click returns it there. Left and Right move it 16px, and 64px with Shift, and Home and End take it to its limits. In a right-to-left layout the sidebar sits at the right, and the divider widens it by moving left.

### One pane at a time

When the layout itself is 640px wide or less, it shows one pane at a time: the list, or the record. The width that counts is the layout's own, not the screen's, so a layout inside a narrow window or panel on a large screen behaves as it does on a phone. On a wider layout nothing in this subsection applies.

Which pane shows follows from the state the reader can return to. The record shows when a record is in view, or when the layout shows something that stands in for one, such as the form for a new record; otherwise the list shows. Choosing a row shows the record, and the platform's usual way back returns to the list.

While the list shows, it fills the layout, and its rows are 10px taller above and below so that they serve as touch targets. The toolbar wraps, and a filter field in it takes a line of its own.

While the record shows, the detail pane fills the layout with 16px of padding, and it begins with a back control: a link that names the list, such as "Expenses", led by the `back` glyph, at `text-md` and weight 600. The back control returns to the list the record lives in, with the filters that were in force, scrolled so that the record's row is in view. It goes back one step, to a list, and the layout offers no trail of the places above the record. While the record shows, the list's toolbar and its chip row step aside, since they act on the list. A toolbar that holds tools for the whole application rather than for the list, such as a launcher or the dock of open windows, stays in both panes.

The divider does not show while one pane shows at a time.

When windows are the detail pane, as [the windows section](windows.md) describes, the layout shows the windows in place of a record.

## Accessibility

The sidebar is exposed as navigation, named for the list it holds. Each row is a link named by its title and its metadata, and the current row's link is exposed as the current item. The divider is exposed as a splitter is, as a separator that controls the sidebar, with its value in px.

In a right-to-left layout the whole layout mirrors: the sidebar sits at the right, the current row's edge stays on the side facing the detail pane, the divider and its keys follow the sidebar, and the `back` glyph turns round.

In the platform's high-contrast mode the current row takes the system's highlight colours, since its fill and edge would not show there, and the divider's rule and glyph are drawn in the system's text colour, and in its highlight colour while hovered, dragged or focused.

A printed layout carries the content without the toolbar, the chip row, the divider or the back control. A layout showing a record prints the record alone.

## Questions this section must settle

- Whether the sidebar's width is part of the state the reader returns to. The web implementation treats it as the reader's convenience and keeps no state for it, leaving the application to remember it; chapter 7 holds the general question of which state is the reader's own and which belongs to the application.
- Whether Enter returns the divider to its default size, as it does for a splitter. The web implementation's divider returns only on a double-click, so the two handles answer the same gesture differently.
- How the divider is grabbed on a touch screen. Its grip is 6px wide, which is narrow for a finger; chapter 6 holds the minimum target size.

## Conformance checklist

1. The layout shows a toolbar, a chip row, a sidebar and a detail pane, and the chip row takes no space when no filter is in force.
2. Every control in the toolbar is 30px tall.
3. The sidebar's width stays between its minimum, 180px by default, and half the layout, however it was set, and starts at 260px.
4. A row's title stays on one line and ends in an ellipsis when cut short, and its metadata lines wrap.
5. The rows are flat, respond under the pointer and are not underlined.
6. The current row shows a 3px `accent` edge on the side facing the detail pane and a bold title, and is exposed as current.
7. The detail pane is a tab stop, and its focus ring is drawn inside it.
8. The divider is flat and shows the `grip` glyph at rest, taking `accent` under the pointer, while dragged and while focused.
9. The divider moves 16px per arrow key and 64px with Shift, Home and End take it to its limits, and a double-click returns it to the default width.
10. At a layout width of 640px or less, the layout shows either the list or the record, never both, and the choice follows the record in view.
11. While the record shows on a narrow layout, a back control naming the list is its first element, and it returns to the list with the filters kept and the record's row in view.
12. While the record shows on a narrow layout, the list's toolbar and chip row are hidden, and a toolbar of application-wide tools stays.
13. The divider is hidden while one pane shows at a time.
14. In a right-to-left layout the sidebar sits at the right and the divider and its keys follow it.
15. In high-contrast mode the current row takes the system's highlight colours.
