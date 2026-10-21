# Segmented controls

A segmented control offers a small set of choices side by side, of which exactly one is chosen at a time, and shows which one it is. It suits a unit (kg or lbs), a mode (Read or Edit) or a span of time (Today, Week or Month). Its choices either change something in place or lead to other views, and in the second case the chosen one is the view the reader is on.

## Anatomy

A segmented control is a row of keys joined side by side, of which one is in, as on a bank of radio buttons. Every segment that can be pressed is raised, as chapter 2 requires of everything that can be pressed, and the chosen one is pressed in, as a pressed button is. Until specification 0.30.0 the segments lay flat on a recessed track with the chosen one raised, which drew the controls the reader can press as flat and the one that does nothing when pressed as raised, the opposite of the rest of the grammar.

Each segment is drawn as a button is: its fill is `raise-grad`, its border a 1px hairline in `raise-border`, and its shadow `raise-shadow`. Neighbouring segments share their border, so the row reads as one control, and only its two ends are rounded, at `radius-sm`. Each segment holds a short label, set in the interface face at `text-sm` and weight 600, in `text`, on one line, centred in a key 30px tall, the height of a menu bar's groups so that the two line up in an application bar, with 12px of padding either side, and it MAY lead with a glyph, 6px before the label. A segment is as wide as its label needs.

The chosen segment is pressed in: its fill is `raise-active-bg`, its shadow `raise-active-shadow`, which falls inside its top edge, and its border `border`. It is drawn above its neighbours, so its border shows whole.

Every label is in `text`, whether its segment is chosen or not. The chosen segment is marked by its depth, and its state is exposed to assistive technology.

A segmented control has two sizes. The small size, for toolbars, is 28px tall, the height of every small raised key, as a small button and a glyph button are, with 9px either side, and sets the labels at `text-xs`. Either size MAY have fully rounded ends, at `radius-pill`.

A segmented control SHOULD hold two to four segments. More choices than that belong in a select or a menu.

## States

| State | Appearance |
|---|---|
| Not chosen | Raised: the fill `raise-grad`, the border `raise-border` and the shadow `raise-shadow` |
| Chosen | Pressed in: the fill `raise-active-bg`, the shadow `raise-active-shadow` and the border `border` |
| Under the pointer, not chosen | The fill becomes `raise-grad-hover` and the border `raise-border-hover` |
| Pressed, while the pointer or key is down, not chosen | Pressed in, as the chosen segment is |
| Focused from the keyboard | A 3px ring in `focus-ring` outside the segment, drawn above its neighbours |
| Disabled | Drawn as it would be otherwise, and dimmed to 45% opacity; it takes no pointer or key presses |

The chosen segment MUST differ from the others in elevation, so the choice never rests on colour. Its state MUST be exposed to assistive technology: as pressed or checked for a choice that changes something in place, and as current for a choice that leads to a view.

## Interaction

Pressing a segment that is not chosen chooses it, and the segment that was chosen stops being chosen. Pressing the chosen segment changes nothing. A segment that leads to a view goes there when pressed, and the view's own segmented control shows that segment chosen. A press with the pointer counts when the pointer is released over the segment.

A segment MUST NOT act on a pointer entering it or resting on it.

Every segment can be reached and pressed from the keyboard with the platform's usual keys. How the keyboard moves between segments is one of the questions below.

## Accessibility

A segmented control is exposed as a group, with an accessible name that says what the choices choose between, such as "Theme". Each segment is exposed with its label as its accessible name and with its state, as the States section says. In the platform's high-contrast mode every segment keeps a visible border, the chosen segment takes the system's highlight colours, since its change of elevation would not show there, and focus is drawn as a solid outline in the system's highlight colour.

## In a narrow space

Where a segmented control would take more room than a narrow screen can give it, such as in an application bar on a phone, an application MAY ask for it to become a pop-up button, as a desktop view switcher does in a narrow window. The pop-up button is a menu button labelled with the current choice, whose accessible name joins the control's name to that choice, such as "View: Window". Its menu lists every choice, in the same order, with the `tick` glyph beside the current one. Choosing one has the same effect as pressing its segment, and the button's label follows. The application decides which controls may collapse; the implementation decides when the space is narrow, and the web implementation does it at a screen 640px wide or less.

A pop-up button takes two presses where segments take one, which is a fair price where segments do not fit and a poor one where they do, so a control never collapses on a wide screen.

## Questions this section must settle

- How the keyboard moves through a segmented control. The web implementation makes each segment a tab stop, where the platforms' radio groups make the whole control one stop and move the choice with the arrow keys.
- Which state a segment that changes something in place exposes. The web implementation accepts either pressed or checked, and the language should name one.
- Whether four segments is a limit. The web implementation's reference page shows five in the small size.
- Whether the fully rounded shape means anything, such as a choice among views, or is only a look an application may pick.

## Conformance checklist

1. Every segment that is not chosen is raised, in both themes, and neighbours share their border.
2. Exactly one segment is chosen, and it is pressed in while the others stand raised.
3. Only the row's two ends are rounded, at `radius-sm`, or `radius-pill` in the fully rounded form.
4. A segment that is not chosen is drawn pressed in while it is pressed.
5. The chosen segment is exposed as pressed or checked, or as current where it leads to a view.
6. The control is exposed as a group with an accessible name, and each segment's accessible name is its label.
7. Labels are `text-sm` at weight 600 in the default size and `text-xs` in the small size, and every label reaches 4.5:1 against what it sits on, in both themes.
8. Pressing a segment that is not chosen chooses it; pressing the chosen one changes nothing.
9. A pointer press counts only when released over a segment, and a pointer resting on one does nothing.
10. Focus from the keyboard shows a ring at least 3:1 against its surroundings.
11. A disabled segment is dimmed to 45%, takes no presses and is exposed as disabled.
12. In high-contrast mode every segment keeps a border, and the chosen segment and focus stay visible.
13. A control the application lets collapse becomes, in a narrow space only, a menu button labelled with the current choice and named with the control's name and that choice, whose menu lists every choice with the current one ticked, and choosing one has the effect of pressing its segment.
