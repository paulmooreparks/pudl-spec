# Segmented controls

A segmented control offers a small set of choices side by side, of which exactly one is chosen at a time, and shows which one it is. It suits a unit (kg or lbs), a mode (Read or Edit) or a span of time (Today, Week or Month). Its choices either change something in place or lead to other views, and in the second case the chosen one is the view the reader is on.

## Anatomy

A segmented control is a switch with more than two positions, as chapter 2 sets out, and is drawn as macOS and iOS draw it. It is a recessed trough, the track, holding a row of segments. The trough is filled with `recess-bg`, bounded by a 1px hairline in `border` and shaded inside its top edge by `entry-shadow`, and its corners are `radius-sm`. It has 3px of padding on every side, and its segments sit 2px apart.

Each segment holds a short label, set in the interface face at `text-sm` and weight 600, in `text`, on one line, with 4px of padding above and below and 12px either side. A segment is as wide as its label needs, and its corners are `radius-xs`. The chosen segment is the thumb, raised in the trough and drawn as a button is: its fill is `raise-grad`, its border a 1px hairline in `raise-border`, and its shadow `raise-shadow`. The other segments are positions marked on the track, flat, with no fill and no visible border, and pressing one moves the thumb there.

Every label is in `text`, whether its segment is chosen or not. The muted colour would not reach readable contrast on the trough, and the chosen segment is already marked by its elevation.

A segmented control has two sizes. The small size, for toolbars, has 2px of padding above and below each label and 9px either side, and sets the labels at `text-xs`. Either size MAY have fully rounded ends, with the trough and every segment at `radius-pill`.

A segmented control SHOULD hold two to four segments. More choices than that belong in a select or a menu.

## States

| State | Appearance |
|---|---|
| Not chosen | Flat on the track, with its label in `text` |
| Chosen | Raised, the thumb: the fill `raise-grad`, the border `raise-border` and the shadow `raise-shadow` |
| Under the pointer, not chosen | A faint fill of `text` at 7% over the trough |
| Pressed, while the pointer or key is down, not chosen | A deeper fill of `text` at 13% over the trough |
| Focused from the keyboard | A 3px ring in `focus-ring` outside the segment |
| Disabled | Drawn as it would be otherwise, and dimmed to 45% opacity; it takes no pointer or key presses |

The chosen segment MUST differ from the others in elevation, so the choice never rests on colour. Its state MUST be exposed to assistive technology: as pressed or checked for a choice that changes something in place, and as current for a choice that leads to a view.

## Interaction

Pressing a segment that is not chosen chooses it, and the segment that was chosen stops being chosen. Pressing the chosen segment changes nothing. A segment that leads to a view goes there when pressed, and the view's own segmented control shows that segment chosen. A press with the pointer counts when the pointer is released over the segment.

A segment MUST NOT act on a pointer entering it or resting on it.

Every segment can be reached and pressed from the keyboard with the platform's usual keys. How the keyboard moves between segments is one of the questions below.

## Accessibility

A segmented control is exposed as a group, with an accessible name that says what the choices choose between, such as "Theme". Each segment is exposed with its label as its accessible name and with its state, as the States section says. In the platform's high-contrast mode the trough keeps a visible border, the chosen segment takes the system's highlight colours, since its change of elevation would not show there, and focus is drawn as a solid outline in the system's highlight colour.

## Questions this section must settle

- How the keyboard moves through a segmented control. The web implementation makes each segment a tab stop, where the platforms' radio groups make the whole control one stop and move the choice with the arrow keys.
- Which state a segment that changes something in place exposes. The web implementation accepts either pressed or checked, and the language should name one.
- Whether four segments is a limit. The web implementation's reference page shows five in the small size.
- What a segmented control does when its segments do not fit the width, as on a phone.
- Whether the fully rounded shape means anything, such as a choice among views, or is only a look an application may pick.

## Conformance checklist

1. The trough is recessed, in both themes.
2. Exactly one segment is chosen, and it is raised as the thumb while the others lie flat on the track.
3. Segments have corners of `radius-xs`, or `radius-pill` in the fully rounded form.
4. A segment that is not chosen shows a deeper fill while it is pressed.
5. The chosen segment is exposed as pressed or checked, or as current where it leads to a view.
6. The control is exposed as a group with an accessible name, and each segment's accessible name is its label.
7. Labels are `text-sm` at weight 600 in the default size and `text-xs` in the small size, and every label reaches 4.5:1 against what it sits on, in both themes.
8. Pressing a segment that is not chosen chooses it; pressing the chosen one changes nothing.
9. A pointer press counts only when released over a segment, and a pointer resting on one does nothing.
10. Focus from the keyboard shows a ring at least 3:1 against its surroundings.
11. A disabled segment is dimmed to 45%, takes no presses and is exposed as disabled.
12. In high-contrast mode the trough keeps a border, and the chosen segment and focus stay visible.
