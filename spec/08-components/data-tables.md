# Data tables and rows to choose from

A data table lists many records of one kind, one record to a row and one field to a column, such as the expenses on a trip or the files in a folder. The reader scans it, sorts it and picks records out of it. A table whose rows are choices, such as a file list, an inbox or a picker, is a grid, in which the reader moves a selection through the rows and opens the one they want, as they would in a desktop file manager.

## Anatomy

A data table sits in a frame of `surface` with a 1px border in `border` and corners of `radius`. When its columns are wider than the space it has, the frame scrolls sideways, and the page around it does not. The table fills the frame's width, and its text is set at `text-md` with tabular figures.

A table MAY have a **caption** above its header, set at `text-sm` and weight 600 in `text-muted`, with `space-3` of padding above it, `space-2` below and `space-4` either side.

The **header row** names each column. Its cells are `surface-alt`, set at `text-sm` and weight 600 in `text-muted`, and do not wrap. The header row SHOULD stay in view at the top of the frame while the rows scroll beneath it.

Every **cell** has `space-2` of padding above and below and `space-3` either side. Its contents align to the start edge and the top of the row, and a 1px hairline in `border` runs along its foot, except in the last row, where the frame's own border serves. A column of numbers aligns its cells, header included, to the end edge, so the digits line up by place.

A **sortable column** has a header that is a raised control filling its cell. Its fill is `raise-grad`, it has a 1px border in `raise-border` along its end edge and a line of light along its top, drawn with `light` at `lit`, and its words are in `text` rather than `text-muted`. After its words, 6px away, it carries a 12px glyph that says how the column is sorted.

| Sort | Glyph | Words |
|---|---|---|
| Not the sort | `sort`, two small arrows, at 55% opacity | Weight 600 |
| Ascending | `sort-up`, at full opacity | Weight 700 |
| Descending | `sort-down`, at full opacity | Weight 700 |

A **selection column** MAY come first, holding a 16px checkbox in each row, and a checkbox in its header that selects or clears every row. It is only as wide as the checkbox.

A **selected row** is tinted with `accent` at 12% and carries a 3px edge of `accent` along its start side, on the left in a left-to-right language and on the right in a right-to-left one. The edge is the signal that does not rely on colour, since a reader who cannot see the tint still sees which rows carry the edge.

A table with no rows to show holds a single **empty row** spanning every column, which says in words that there is nothing to show and, where it helps, why. Its words are centred in `text-muted`, with `space-6` of padding above and below and `space-4` either side. An empty row is not a record and is never selected.

## Kinds

- A **plain data table** shows records to read. It may have sortable columns and a selection column. A reader selects rows by checking their checkboxes, and may select several, for an action on all of them.
- A **grid** is a data table whose rows are choices. It has a single selection, which the reader moves from row to row, and each row stands for one record the reader can open. A grid does not have a selection column. Its rows are a list of choices, the category chapter 2 describes, so they are flat, they respond under the pointer, and the selected row is marked by its edge as well as its tint. A grid's rows are not underlined, and neither are the links inside them, since the grid already says what its rows are.

## States

| State | Appearance |
|---|---|
| A row of a grid under the pointer | Tinted with `text` at 4% |
| A row of a plain data table under the pointer | Tinted with `text` at 4%; a pointer convenience only, which an implementation MAY leave out |
| A selected row | Tinted with `accent` at 12%, with a 3px `accent` edge on its start side |
| A focused row, in a grid | A 3px ring in `focus-ring` drawn inside the row's bounds, together with the start edge if it is selected |
| A sortable header under the pointer | The fill becomes `raise-grad-hover` |
| A sortable header while pressed | Pressed in, with the fill `raise-active-bg` |
| A sortable header focused from the keyboard | A 3px ring in `focus-ring` inside its bounds |
| The sorted column's header | The direction's glyph at full opacity, and its words at weight 700 |

A badge in a selected row keeps its words at 4.5:1 against the combined tint, as the badges section requires.

## Interaction

### Sorting

Pressing a sortable column's header sorts the table by that column. Pressing the header of the column that is already the sort reverses the direction. The sort in force is restorable state, as chapter 7 describes, so a reader who leaves a sorted table and returns, or hands it to somebody else, finds it sorted the same way. Each sortable header is one stop in the keyboard's tab order and is pressed with the platform's usual keys.

### Selection in a plain data table

Checking a row's checkbox selects the row, and clearing it deselects the row. Checking the header's checkbox selects every row the table shows. The checkboxes are ordinary checkboxes, each a stop in the tab order.

### Rows to choose from

A grid is one stop in the tab order, and that stop is its selected row, or its first row when none is selected. Within the grid the selection follows focus.

| Key | Moves the selection to |
|---|---|
| Down arrow | The next row |
| Up arrow | The previous row |
| Home | The first row |
| End | The last row |
| Page Down | The row ten rows further on, or the last row |
| Page Up | The row ten rows back, or the first row |

Enter opens the selected row. Pressing a row with the pointer selects it, and pressing it twice in quick succession opens it. Opening a row does what following its own address would do, and when a row has no address the application is told which row was opened and acts on it. The application is also told each time the selection moves to another row.

The links and other controls inside a grid's rows leave the tab order, since the row stands for them. An action on a row belongs on a toolbar or menu that acts on the selected row. The selected row is restorable state when it is the record in view.

### Narrow screens

A data table MAY be marked by its application to stack when it is narrow. When the table's frame is 560px wide or less, a stacking table hides its header row from sight and shows each record as a small block of lines, one line per field. Each line has the column's label at its start, at `text-sm` and weight 600 in `text-muted`, and the value at its end, with `space-1` of padding above and below and `space-4` either side. Each block has `space-2` of padding above and below, and a 1px hairline in `border` divides it from the next. A table that is not marked to stack scrolls sideways within its frame instead.

## Accessibility

A data table is exposed as a table, with its header cells as the headers of their columns and its caption, when it has one, as its name. A sortable column's header is exposed with the direction the table is sorted in, ascending, descending or not sorted, and its control is exposed with its name, so a screen reader announces the sort as well as the column. A row selected by its checkbox is exposed through the checkbox as checked.

A grid is exposed with the grid role and a name that says what it lists. Each of its rows is exposed as selected or not selected. The row with focus is the one a screen reader announces as the reader moves.

When a table stacks, its header row stays exposed to assistive technology, so the table is still read as a table. The empty row is exposed as ordinary text.

In the platform's high-contrast mode the frame and each sortable header keep a visible border, a selected row takes the system's highlight colours, since its tint and edge would not show there, and the sort glyphs are drawn in the system's button text colour. In print the frame loses its border, the header row stops following the scroll, and sortable headers are drawn flat.

## Questions this section must settle

- How a reader opens a row of a grid on a touch screen. Selecting and opening are separate on the desktop, by a single press and a double one, and a tap cannot be both; the language has to choose whether a tap selects, opens, or does one and offers the other.
- Whether a grid may allow more than one selected row, and if so by which keys and pointer gestures. The web implementation allows one.
- Whether a sortable header counts as raised under chapter 2. It has a graded fill and a lit top edge but only an end border and no shadow of its own, so it is lighter than every other raised control.
- Whether stacking on a narrow screen is the application's choice, as it is on the web, or the rule for every data table, and whether 560px is part of the language or the web implementation's own threshold.
- Whether Page Up and Page Down move ten rows, as the web implementation does, or a screenful of rows, as most desktop platforms do.

## Conformance checklist

1. The table sits in a `surface` frame with a 1px `border` hairline and corners of `radius`, and scrolls sideways inside it when too wide.
2. Header cells are `surface-alt`, `text-sm` at weight 600 in `text-muted`, and do not wrap.
3. Cells are `text-md` with tabular figures, and a column of numbers aligns to the end edge.
4. A sortable header is drawn raised, shows the `sort` glyph when its column is not the sort and `sort-up` or `sort-down` when it is, and sets its words at weight 700 while its column is the sort.
5. Pressing a sortable header sorts by its column, and pressing the sorted column's header again reverses the direction.
6. The sort in force is restored when the reader returns to the table.
7. A sortable header is exposed with the table's sort direction on that column.
8. A selected row shows an `accent` tint and a 3px `accent` edge on its start side, on the right in a right-to-left language.
9. A table with no rows shows an empty row in words, spanning every column.
10. A grid is one tab stop, on its selected row or else its first.
11. In a grid, the arrow keys, Home, End, Page Up and Page Down move the selection, and the selection follows focus.
12. In a grid, Enter or a double press opens the selected row, and a single press selects it.
13. A grid's rows are flat, respond under the pointer, and are not underlined.
14. A grid is exposed with the grid role, and each row as selected or not selected.
15. A focused row in a grid shows a ring at least 3:1 against its surroundings, and a focused sortable header does the same.
16. A table marked to stack shows each record as labelled lines when its frame is 560px wide or less, and keeps its headers exposed.
17. In high-contrast mode the frame and sortable headers keep a border, and a selected row takes the system's highlight colours.
