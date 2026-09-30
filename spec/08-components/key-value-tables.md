# Key and value tables

A key and value table shows the fields of one record that the reader can read but not change, each as a label beside its value. A record's detail view uses it wherever a field is on display only. A field that cannot be typed into is never drawn as a sunken box, because a sunken surface promises input, so the table draws everything in it flat.

## Anatomy

A key and value table is a column of rows, each holding one field. It fills the width it is given, and its text is set at `text-md` with tabular figures.

Each row has two cells. The **label** comes first, at the start edge, set at `text-sm` and weight 600 in `text-muted`. Labels never wrap, and the label column is only as wide as its longest label. A label has `space-2` of padding above and below it, `space-4` after it, and none before it. The **value** follows in `text`, with `space-2` above and below and no padding at either side. A value wraps onto as many lines as it needs, and may break inside a long word, such as an identifier or an address, rather than overflow the table. Label and value align to the top of their row, so a value of several lines keeps its label beside its first line.

Every row after the first has a 1px hairline in `border` along its top. The table has no border of its own and no fill, so it takes the surface it sits on.

A value is usually text, a number or a time. It MAY be a link, or a badge or chips, when those describe the field better than words would.

## States

A key and value table has no states. It takes no focus and does not respond to the pointer. A link inside a value keeps the states of a link.

## Interaction

The table itself does nothing when pressed. A reader who wants to change a field does it elsewhere, in a form or dialog the application offers, and the table then shows the new value.

## Accessibility

A key and value table is exposed as a table in which each label is the header of its row, so a screen reader announces a value together with its label.

## Questions this section must settle

- What happens on a narrow screen when a label is long. Labels never wrap, so the label column can crowd the values; the language has yet to say whether a label may wrap there, or whether the label should sit above its value.
- Whether a value may be edited in place, and if it may, what the field looks like while it is being edited and how the reader leaves it.

## Conformance checklist

1. Labels are `text-sm` at weight 600 in `text-muted`, and values `text-md` in `text`, with tabular figures.
2. Labels do not wrap, and the label column is as wide as its longest label.
3. A long value wraps within the table rather than overflowing it.
4. Every row after the first is divided from the one before by a 1px hairline in `border`.
5. Nothing in the table is raised or sunken, except a control a value holds.
6. The table takes no focus and responds to no press.
7. Each value is exposed with its label as its row header.
