# Diffs

A diff shows the difference between two texts, such as two versions of a file in a code review, a document compared with an earlier revision, or an edit someone proposes. An application computes the diff and decides what can be done with it. This section settles how a diff looks, how its parts are marked, and how it is read and chosen from, so that every diff in a PUDL application reads alike. A read-only diff is plain markup that the stylesheet draws with no script. A diff drawn by an editor component, which keeps markup of its own, meets the same rules through the same tokens.

## Anatomy

A diff has one of two layouts. In the **inline** layout the removed lines stand above the lines that replace them. In the **side-by-side** layout the earlier text stands at the start edge and the later text at the end edge, aligned line for line.

| Part | What it is |
|---|---|
| Line | One line of either text, of one of four kinds: unchanged, added, removed, or an unmatched region |
| Unmatched region | The space on one side of a side-by-side diff opposite lines that exist only on the other side, which keeps the two sides aligned |
| Gutter | The columns before a line's text: its number in the earlier text and in the later text (the inline layout shows both, and each side of a side-by-side diff shows its own), its sign, and its choice box where lines can be chosen |
| Sign | The `plus` glyph on an added line and the `minus` glyph on a removed one |
| Changed words | The part of a changed line that differs from its counterpart, marked within the line |
| Hunk heading | A strip above each run of changes, with its range in unified-diff form, its place, such as "Hunk 2 of 5", and the actions the application offers for it |
| Folded lines | A band standing for a run of unchanged lines that are not shown, with a button that shows them |
| Summary | The number of hunks, added lines and removed lines, as words in the diff's head |

A line's text is set in `mono` at `text-sm`, in the colours the application's highlighting gives it, as chapter 8's code roles set them. The gutter's numbers are `mono` at `text-xs` in `text-muted`, aligned to the end. The sign is drawn at 12px, in `diff-add` on an added line and in `diff-del` on a removed one. The sign column is always drawn, in both layouts, because the sign is what states a line's kind: a line's tint alone is far below 3:1 against the surface and MUST NOT be the only mark.

An added line and its gutter are filled with `diff-add-bg`, and a removed line and its gutter with `diff-del-bg`. Changed words take a 2px underline in `diff-add` or `diff-del` at full strength. They MUST NOT take a stronger fill, which would take the syntax colours below 4.5:1. An unmatched region is hatched at 45 degrees in `border` at half strength. A hunk heading takes `surface-alt`, with a 1px line in `border` above and below, and its range in `mono` in `accent`. Folded lines are a band of `surface-alt` in `text-muted`. The summary is set at `text-sm` in `text-muted`.

### The tokens

| Token | Default | Use |
|---|---|---|
| `diff-add` | `positive` | The sign of an added line, and the underline of added words |
| `diff-del` | `danger` | The sign of a removed line, and the underline of removed words |
| `diff-add-bg` | `diff-add` at 10% | The fill of an added line and its gutter |
| `diff-del-bg` | `diff-del` at 10% | The fill of a removed line and its gutter |

`diff-add` and `diff-del` are tokens of their own, with the status colours as their defaults, because red and green are the convention readers know for removal and addition while the status colours mean something else. A theme MAY point them elsewhere, such as blue and orange for readers with red-green colour blindness. Whatever they are, a theme keeps two rules: every syntax colour reaches 4.5:1 on `diff-add-bg` and `diff-del-bg` laid over `input-bg`, and each sign reaches 3:1 against its line's fill. The tint is the strongest at which the first rule holds, and 10% is the default because it holds for the default palette with some margin; a theme with other syntax colours sets its own amount.

## States

| State | Appearance |
|---|---|
| An unchanged line | `input-bg`, with no sign |
| An added line | `diff-add-bg`, with the `plus` sign in `diff-add` |
| A removed line | `diff-del-bg`, with the `minus` sign in `diff-del` |
| An unmatched region | Hatched, and hidden from assistive technology |
| A chosen line | Its choice box ticked, and a 3px edge in `accent` on its start side, as a current tree row has |
| Folded lines | A band of `surface-alt` with a button that shows them |

## Interaction

Next Change and Previous Change move to the first line of the next or previous hunk, bring it into view below its heading, and announce the hunk's heading and its counts politely. An application that offers them MAY bind them to keys and SHOULD put them on the diff's toolbar.

A hunk heading's actions are ordinary buttons in the Tab order, each with an accessible name that includes the hunk's number, such as "Stage hunk 2".

Where lines can be chosen, each changed line's gutter holds a PUDL checkbox. The choice boxes are one stop in the Tab order, as chapter 6 asks of any set of items: Up and Down move between the boxes of changed lines, Space ticks or clears one, and Shift with Up or Down extends the choice. A pointer may Shift-click to choose a run. The whole gutter cell of a line is the box's target, and a diff whose lines can be chosen draws each line at least 24px tall, so the target meets WCAG 2.2's minimum without resting on its exceptions. Actions on the chosen lines stand at the diff's foot with the count in their words, such as "Stage 3 Lines", and are disabled until a line is chosen.

Selecting and copying takes the lines' text alone. Gutters, signs, hunk headings and folded bands are not selectable, and in a side-by-side diff a selection stays within one side.

## Accessibility

Each side of a side-by-side diff is a region labelled "Before" or "After" with the text's name, and an inline diff has one label for the whole. An added line is exposed with the insertion role and a removed line with the deletion role, and each carries a visually hidden "Added" or "Removed" before its text, so a screen reader hears the kind without a colour it cannot see. Changed words are HTML's `ins` and `del`. A line exposes one number, from the side the line belongs to. An unmatched region is hidden from assistive technology. The summary is text, and it changes when the texts do.

In a right-to-left page the gutters and the two sides mirror, as every component does, and the text itself keeps its own direction.

In the platform's high-contrast mode the tints are gone, and these replace them. The signs paint in the system's text colour, as every glyph does. An added line has a 2px solid rule on its start edge and a removed line a 2px dashed one, both in the system's text colour, so the kinds can be scanned down the edge. Added words are underlined and removed words struck through. An unmatched region keeps its hatch in the system's grey text colour. A chosen line's edge takes the system's highlight colour. Hunk headings and the folded band keep their borders.

## What stays with the application

The application computes the diff, decides where hunks begin and end, highlights the syntax, chooses the layout a reader starts in and remembers the last one chosen, and decides which actions a file, a hunk and chosen lines offer and whether they ask first. Three-way views for resolving conflicts are the application's own until they are specified.

## Questions this section must settle

- How a three-way view for resolving conflicts is drawn: its parts, its layout and its choices.
- Whether a diff of long lines wraps them or scrolls each side sideways, and whether the reader chooses.

## Conformance checklist

1. Every changed line shows its sign, `plus` or `minus`, in `diff-add` or `diff-del`, in both layouts; the tint is never the only mark.
2. Added and removed lines and their gutters are filled with `diff-add-bg` and `diff-del-bg`, at which every syntax colour reaches 4.5:1 over `input-bg` and each sign reaches 3:1.
3. Changed words are `ins` and `del`, marked by a 2px underline in `diff-add` or `diff-del` and no stronger fill.
4. An added line has the insertion role and a removed line the deletion role, each with a visually hidden word stating its kind; an unmatched region is hidden from assistive technology.
5. Hunk headings take `surface-alt` with lines in `border`, their range in `mono` and `accent`, and their actions are named with the hunk's number.
6. Where lines can be chosen, the choice boxes are one Tab stop with the arrow keys, each line is at least 24px tall with its whole gutter cell as the target, and a chosen line has a 3px `accent` edge.
7. Gutters, signs, headings and folded bands are not selected or copied with the text.
8. In high-contrast mode, added lines have a solid start edge, removed lines a dashed one, removed words are struck through, and the hatch and the chosen edge use the system's colours.
