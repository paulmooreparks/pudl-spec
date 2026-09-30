# Badges, chips and filter chips

Badges, chips and filter chips are three small labels that sit beside the thing they describe. A status badge states the condition an entity is in, such as done or overdue. A chip names an attribute the entity carries, such as a tag or the trip an expense belongs to. A filter chip stands for a filter the reader has applied to a list, and carries the control that removes it. Chapter 2 requires each of them to look unlike the other two and unlike buttons, links and tabs, since a reader who mistakes one for another will expect it to do something it does not.

## Anatomy

All three sit on one line, are as wide as their contents, and set their figures tabular, since what they carry is data. A badge and a chip are flat, so neither responds to the pointer, takes focus or can be pressed. The one part of the three that can be pressed is a filter chip's remove control, and it is raised.

A **status badge** has fully rounded ends, `radius-pill`, with 1px of padding above and below its words and 8px either side. Its words are set at `text-2xs` and weight 700, with a line height of 1.55. A badge of any kind but the neutral one leads with a 9px glyph, 4px (`space-1`) before its words, filled with the colour of those words. The neutral badge carries no glyph.

A **chip** has corners of `radius-sm` and the same padding as a badge. Its words are set at `text-xs` and weight 600, in `text`, and its fill is `text` at 8% opacity over whatever lies behind it. A chip carries no glyph and no status colour. Its squarer corners, its larger words and its neutral fill are what keep it from being read as a badge.

A **filter chip** has fully rounded ends, a 1px border of `accent` at 55% opacity and a fill of `accent` at 8%, and its words are in `accent` at `text-xs` and weight 600. It has 2px of padding above and below, 10px before its words and 3px after its remove control, and its parts are 6px apart. It may begin with the kind of filter, such as "trip" or "account", set at `text-2xs` and weight 500 in capitals with 0.04em of added letter spacing. Size, weight and capitals mark the kind as secondary; it is not faded, because fading it would take it below readable contrast. The value of the filter follows, and then the remove control, an 18px circle drawn raised: its fill is `raise-grad`, its border a 1px hairline in `raise-border`, its shadow `raise-shadow`, and it holds the `close` glyph in `text-muted`.

The filter chips in force on a list gather in a row beside the list's toolbar, 6px apart and wrapping onto further lines as they need, with `space-2` of padding above and below the row and `space-4` either side. The row is `surface`, with a 1px hairline in `border` along its foot. It may end in a link that clears every filter at once. A row with no filter chips in it is not shown.

## Kinds

A status badge is one of five kinds. Each kind but the neutral one fills the badge with its colour at the opacity in the table, over whatever lies behind the badge, and sets the words in its colour mixed 62% into `text`. Mixing toward `text` darkens the words in a light theme and lightens them in a dark one while keeping their hue, so they reach 4.5:1 against the tint, even inside a selected table row whose own tint darkens the ground further. The palette's status colours stay as the theme set them.

| Kind | Meaning | Fill | Glyph |
|---|---|---|---|
| Neutral | A state that asks nothing of the reader, such as ready | `text-muted` at 18%, with words in `text` | None |
| Accent | A state in progress, such as active | `accent` at 18% | `diamond` |
| Warning | A state that needs attention soon, such as a receipt due | `warn` at 22% | `triangle` |
| Danger | A state that has failed or is overdue | `danger` at 18% | `square` |
| Positive | A state that is complete, such as done | `positive` at 22% | `circle` |

Each status kind has a glyph of a different shape, so the kind still reads for a reader who sees no colour, as chapter 2 requires. The words of the badge name the state as well, and the glyph never stands in for them.

Chips and filter chips have no kinds.

## States

A status badge and a chip have no states of their own. A filter chip's body has none either; its remove control has the states of a button.

| State of the remove control | Appearance |
|---|---|
| At rest | Raised, as above |
| Under the pointer | The fill becomes `raise-grad-hover`, the border `raise-border-hover`, and the glyph `text` |
| Pressed, while the pointer or key is down | Pressed in: the fill becomes `raise-active-bg` and the shadow `raise-active-shadow` |
| Focused from the keyboard | A 3px ring in `focus-ring` outside its border, in addition to its other state |

## Interaction

A badge and a chip take no focus and do nothing when pressed. A filter chip's remove control is one stop in the keyboard's tab order and is pressed with the platform's usual keys. Pressing it removes that one filter and shows the list without it. The filters in force are restorable state, as chapter 7 describes, so removing one changes what the reader returns to.

## Accessibility

A badge and a chip are exposed as their words, with the glyph hidden from assistive technology, since the words already say what the glyph shows. The remove control is exposed as a control that can be pressed, with an accessible name that says which filter it removes, such as "Remove the trip filter", and it SHOULD show that name as a tooltip. In the platform's high-contrast mode a badge, a filter chip and its remove control each keep a visible border, and the glyphs are drawn in the system's text colour.

## Questions this section must settle

- Whether a chip may ever be pressable, for instance to go to everything that carries the same tag. The web implementation has no such chip, and a pressable chip would need an appearance that does not borrow a button's or a link's.
- How large the remove control's target is on a touch screen. At 18px it is below any usual minimum target size, which chapter 6 has yet to set.
- Whether the accent badge's meaning, a state in progress, is fixed by the language or left to each application.

## Conformance checklist

1. A status badge, a chip and a filter chip can each be told from the others, and from buttons, links and tabs, in both themes.
2. A badge's words are `text-2xs` at weight 700, a chip's and a filter chip's `text-xs` at weight 600, and their figures are tabular.
3. Each status badge but the neutral one leads with its own glyph: `diamond` for accent, `triangle` for warning, `square` for danger and `circle` for positive.
4. A badge's words reach 4.5:1 against its fill in every kind, in both themes, including inside a selected table row.
5. A badge and a chip take no focus and respond to no press.
6. A filter chip's remove control is raised, draws the `close` glyph, is pressed in while pressed, is one tab stop, and removes its filter when pressed with the pointer or the platform's usual keys.
7. The remove control's accessible name says which filter it removes.
8. Focus on the remove control from the keyboard shows a ring at least 3:1 against its surroundings.
9. The glyphs are drawn from the glyph set, not taken from a font.
10. A row of filter chips with no chips in it is not shown.
11. In high-contrast mode a badge, a filter chip and its remove control keep a border, and their glyphs stay visible.
