# Progress bars and meters

A progress bar says how far a task has got, such as an upload or an export, and a meter says where a level stands within a known range, such as storage used or an agent's context window. Both are display: they are drawn flat, since nothing about them is pressed or typed in.

## Anatomy

Both are a bar 16px tall with fully rounded ends, its track filled with `text` mixed at 9% into `surface` and bounded by a 1px line in `border`, with no shadow. The value fills the track from its start edge.

Words always go with the bar, since the bar alone says nothing to a reader who cannot see it. In a row, the bar stands beside its value in words, in `text-muted` with tabular figures, such as "42%" or "4 of 10", under its name in `text` at weight 600.

- A **progress bar** fills in `accent`. A task whose length is not known shows a block a third of the track wide sliding along it, and its words say it is working; where the reader has asked for less motion, the block stands still in the middle and the words still say it.
- A **meter** never moves by itself and never animates, so it is not mistaken for progress. The application says which values are good, and where the bands begin, through the meter's lowest, low, high, highest and best values, so that a low level can be the bad one, as with fuel, or the good one, as with pollution. A meter in the good band fills in `positive`, in the fair band in `warn` with its words led by the `warning` glyph, and in the poor band in `danger` with its words led by the `stop` glyph, so fair and poor differ in shape as well as colour. A meter MAY instead fill in `accent` and show a mark across the track at each threshold, its words saying the band, such as "78%, high", for a level the reader judges against the marks.

## States

A progress bar's value only rises. A task that starts a new stage shows a new bar with words of its own rather than running one bar backwards, which is the complaint made most often about progress bars.

## Accessibility

A progress bar is exposed as a progress bar and a meter as a meter, each with its name, its value and its range, and the value in words as its text. A progress bar with no known length is exposed as busy.

In the platform's high-contrast mode the track keeps a border and the fill takes the system's highlight colour.

## Conformance checklist

1. The bar is 16px tall, flat, with fully rounded ends and a hairline border.
2. Words always go with the bar, and a progress bar of unknown length says it is working.
3. The sliding block of a progress bar of unknown length stands still where the reader asks for less motion.
4. A meter's band follows its application's thresholds and best value, in either direction.
5. A meter in the fair or poor band leads its words with the band's glyph, and its fill takes the band's colour; a meter with marks keeps the accent and marks its thresholds.
6. A progress bar's value never runs backwards.
7. Both are exposed with their name, value and range.
