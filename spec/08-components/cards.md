# Cards

A card gathers what belongs to one thing, such as an expense, a document or a person, onto a surface lifted slightly off the page. It lets a reader see at a glance where one thing's details end and the next thing's begin. A card is for reading, and whatever can be pressed or typed into inside it keeps its own elevation.

## Anatomy

A card is a panel of `surface` with a 1px border in `border`, corners of `radius`, `space-4` of padding on every side, and the shadow `shadow-card`. That shadow is a soft shadow 1px below the card with a 3px blur, drawn with `shade` at `depth` times 0.6, together with a faint 1px ring of `shade` at `depth` times 0.25. It separates the card from the page without the lit top edge and graded fill of a raised control, so a card never looks pressable.

A card may hold, in this order, any of these parts.

- A **title**, set in the display face at `text-lg` and weight 700, with 6px below it.
- A **subtitle**, at `text-sm` and weight 600 in `text-muted`, with 6px below it.
- A **description**, a line or two at `text-sm` in `text-muted`, with `space-3` below it.
- **Content**, which is any other component: badges and chips, a key and value table, notices or buttons.

Every part is optional. A card with no title SHOULD have content that makes plain what it is about.

A **settings panel** is a column of cards, one for each group of settings, `space-3` apart and at most 720px wide, centred in a page or a window. Each card has its title, a description in `text-muted`, its controls, and at its foot a row of the buttons that act on that group, `space-2` apart. A line under the row MAY say what the last action did, such as that the settings were saved, and takes no room while it has nothing to say.

## States

A card has no states of its own. It does not respond to the pointer, and it takes no focus. The components inside it keep all of their own states.

## Interaction

A card is not a control and does nothing when pressed. Its title MAY be, or hold, a link to the thing the card describes, and the link then behaves as any link does.

## Accessibility

A card's title, when it has one, SHOULD be exposed as a heading at the level that fits its place in the page, so a reader moving by headings can reach each card. The card itself needs no role. In the platform's high-contrast mode, where shadows are not drawn, a card keeps a visible border so its bounds still show. In print a card keeps its border and loses its shadow.

## Questions this section must settle

- Whether a whole card may be pressable, as a card in a gallery of choices often is. Chapter 2 lets a flat thing be pressed only as a row of a list of places or choices, and a card is neither raised nor such a row, so a pressable card would need either a treatment of its own or a rule against it.
- Whether a card may be selected, as one of a set of cards to choose from, and how the selection would show.
- Whether the lift that `shadow-card` gives is a fourth kind of surface in the grammar, or a variety of flat. Chapter 2 names three elevations, and a card's shadow is neither raised nor sunken.

## Conformance checklist

1. A card is `surface` with a 1px `border` hairline, corners of `radius`, `space-4` of padding and the `shadow-card` shadow, in both themes.
2. A card cannot be mistaken for a raised control: it has no lit top edge and no graded fill.
3. Its title is `text-lg` at weight 700; its subtitle `text-sm` at weight 600 in `text-muted`; its description `text-sm` in `text-muted`.
4. A card takes no focus and responds to no press, while the controls inside it respond as they would elsewhere.
5. A card's title is exposed as a heading.
6. In high-contrast mode a card keeps a visible border.
7. A settings panel is a column of cards `space-3` apart, at most 720px wide, each card's actions in a row at its foot.
