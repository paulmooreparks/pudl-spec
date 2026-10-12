# Row editors

A row editor edits a list of like things as rows of fields, where each row has the same fields and a reader adds rows and takes them away: the inputs a flow takes, the questions a step asks, the exits a step may leave by. It is a table, because that is what it is, and a table is what assistive technology reads best for it: the headings say what each column holds, and each field says which row it belongs to.

## Anatomy

A row editor is a table with a heading row, the rows, and an **Add** button beneath.

- The **headings** are flat, at `text-xs` and weight 600 in `text-muted`, one per column; they are not the raised sortable headers of a data table, since nothing here sorts. The last column, which holds each row's remove button, has a heading that is hidden from sight and read as "Remove".
- Each **row** holds one field per column, sunken as fields are, and at its end a **remove** button, a danger glyph button of the standalone size carrying `close`. The remove column is as wide as its button and no wider; the other columns take the width of their content, and a column of text fields stretches to what is left.
- A row MAY have a **second line**, one field that spans the columns, beneath its first, such as the value a flow returns for an output.
- The **Add** button is a plain button beneath the table, `space-2` below it, led by the `plus` glyph and saying what it adds, such as "Add an Input".

Rows are divided by the data table's 1px line in `surface-alt`, and there is `space-2` between a row's cells.

When the editor's own width is 480px or less, measured on the editor and not the screen, since an editor sits in windows of every width, each row becomes a block of its fields one above another, each under its heading as a label at `text-sm` and weight 600 in `text-muted`, with the remove button at the block's top end, as a data table's rows stack on a phone. The heading row is then hidden from sight and still read.

## States

The fields, the remove buttons and the Add button have the states of their own sections, and the editor adds none.

## Interaction

Add appends a row and moves focus to its first field. Remove takes its row away, with the row's second line, and moves focus to the first field of the row that followed it, or of the row before it when it was last, or to Add when it was the only row. Removing MAY ask for confirmation or offer an undo, as a danger action does; the application decides, and it is told before and after each removal. The application builds each row, since only it knows the fields; the editor places them and keeps focus where a reader expects it.

## Accessibility

The editor is exposed as a table, named for what it holds, such as "Inputs", with its column headings. Each field has a name of its own that says both what it holds and which row it is in, such as "Name of input 2", because a reader moving through the fields hears the field and not the column. Each remove button's name says which row it removes. In the stacked layout the headings read as before, and each field's label shows above it.

## Questions this section must settle

- Whether rows may be reordered by dragging, as a tab can be; the web implementation offers no reordering.
- Whether a row may be given a title of its own, as a card has, when its fields are many.

## Conformance checklist

1. A row editor is a table with flat headings at `text-xs`, a sunken field in each cell, a danger glyph button carrying `close` at each row's end in a column no wider than it, and a plain Add button led by `plus` beneath.
2. A row's second line spans the columns.
3. At an editor width of 480px or less each row stacks its fields under their headings as labels, with the remove button at its top end, and nothing runs wider than the editor.
4. Add focuses the new row's first field; Remove focuses the next row's first field, else the previous row's, else Add.
5. The editor is a named table with headings, each field names its row as well as what it holds, and each remove button names its row.
