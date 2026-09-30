# Glyph buttons

A glyph button is a button that shows a drawn glyph and no words. It is small and square, and it suits actions that repeat along the rows of a list or sit in a toolbar or a title bar, where a worded button on every row would crowd the line: remove, drag to reorder, copy, dismiss. Everything the [buttons](buttons.md) section says of a button holds for a glyph button, except where this section says otherwise.

## Anatomy

A glyph button is a raised surface holding one glyph from chapter 5, centred in it. The surface is drawn as a button's is: its fill is `raise-grad`, its border a 1px hairline in `raise-border`, and its shadow `raise-shadow`. At rest the glyph is filled in `text-muted`, so a column of glyph buttons down a list stays quieter than the content it acts on.

A glyph button standing on its own is 28px square with corners of `radius-sm`. Its size is fixed, so it has no padding of its own. In a dense strip, such as the header of a code block, it MAY be 26px square, and the glyph there is 14px.

Several components carry a glyph button of their own, sized to fit where it sits. Each of those components' sections sets its metrics, and this section sets what they all share. The web implementation draws them as follows.

| Where it sits | Size | Shape | Glyph |
|---|---|---|---|
| A notice or a toast, to dismiss it | 24px | Circle | 12px |
| A window's title bar | 24px, or 20px on a window docked to an edge | Circle | 12px, or 10px |
| A filter chip, to remove the filter | 18px | Circle | Set by the chip |
| A document tab, to close it | 18px | Circle | 9px |
| A row of a tree, to expand or collapse it | 16px | Corners of `radius-xs` | 10px |
| The end of a filter field, to apply the filter | 32px wide, the field's height | Square corners where it meets the field | 14px |

The last of these is joined to the field it belongs to. Its corners on the side that meets the field are square, and its border overlaps the field's by 1px, so the sunken field and the raised button read as one control made of two parts.

Every one of these, whatever its size or shape, has the states this section sets out. In particular each is drawn pressed in while it is pressed, as every raised control is.

A glyph button MUST have an accessible name that says what pressing it does, such as "Remove the trip filter", and SHOULD show that name as a tooltip, as the section on tooltips specifies. The glyph is drawn, as chapter 2 requires. A character from a font, such as a multiplication sign standing in for the close glyph, MUST NOT take its place.

## Kinds

- A **plain** glyph button performs an ordinary action.
- A **danger** glyph button performs an action that destroys something or cannot be undone, such as removing a row or closing a window. Under the pointer its glyph turns to `danger`. The action SHOULD ask for confirmation or offer an undo, as for a danger button.

## States

| State | Appearance |
|---|---|
| At rest | Raised, with the glyph in `text-muted` |
| Under the pointer | The fill becomes `raise-grad-hover`, the border `raise-border-hover` and the glyph `text`; a danger glyph button's glyph becomes `danger` |
| Pressed, while the pointer or key is down | Pressed in: the fill becomes `raise-active-bg` and the shadow `raise-active-shadow` |
| Focused from the keyboard | A 3px ring in `focus-ring` outside its border, in addition to its other state |
| Confirming | For about two seconds after an action that leaves nothing else on screen to show it worked, such as a copy, the glyph MAY become the check glyph in `positive` |
| Disabled | Raised as at rest, and dimmed to 45% opacity; it takes no pointer or key presses |

A glyph button that confirms an action this way MUST also announce the outcome to assistive technology, in words, because the change of glyph and colour reaches only the eye.

## Interaction

A glyph button is one stop in the keyboard's tab order, and the platform's usual keys press it, as they press a button. A press with the pointer counts when the pointer is released over it.

A glyph button MUST NOT act on a pointer entering it or resting on it. Resting the pointer on it shows its tooltip after a moment, and focusing it from the keyboard shows the tooltip at once; neither does anything else.

A glyph button inside a control that may hold only certain children, such as the close button inside a document tab, MAY be left out of the tab order and hidden from assistive technology, provided the control around it offers the same action from the keyboard. The section on document tabs specifies the one case the web implementation has.

## Accessibility

A glyph button is exposed with the button role and its accessible name, and the glyph inside it is not exposed on its own, since the name already says what it shows. A disabled glyph button is exposed as disabled. In the platform's high-contrast mode a glyph button keeps a visible border, its glyph is drawn in the system's button text colour, and focus is drawn as a solid outline in the system's highlight colour.

## Questions this section must settle

- What size the glyph is in a standalone 28px glyph button. The web implementation leaves it to the size of the text the button inherits, and sets it only in the 26px form and in the glyph buttons other components carry.
- Whether a glyph button may latch, as a toggle button does. The web implementation gives it no latched state.
- Whether a danger glyph button must show its danger at rest. A danger button shows it before the reader touches it, but a danger glyph button shows it only under the pointer, which a touch screen never reaches.
- What shape a glyph button takes. The standalone one is a rounded square, the ones inside other components are mostly circles, and the tree's toggle has corners of `radius-xs`. The language should say whether the shape means something or whether there is one shape.
- How a reader on a touch screen learns what a glyph button does, when no pointer rests on it to show the tooltip.
- The minimum target size. The glyph buttons inside other components are 16px to 24px, below the sizes touch platforms recommend; chapter 6 holds the same question for the small button.
- Whether a glyph button can be the primary action of its context. The web implementation has no accent-filled glyph button.

## Conformance checklist

1. A glyph button is raised at rest and pressed in while pressed, in both themes, and so is every glyph button another component carries.
2. It shows one drawn glyph and no words, and never a character from a font in place of a glyph.
3. A standalone glyph button is 28px square with corners of `radius-sm`.
4. Its accessible name says what pressing it does, and its glyph is not exposed separately.
5. It is one tab stop, the platform's usual keys press it, and a pointer press counts only when released over it.
6. A pointer resting on it shows its tooltip and does nothing else.
7. Its glyph reaches 3:1 against its fill in every kind and state except disabled, in both themes.
8. A disabled glyph button is dimmed to 45%, keeps its elevation, takes no presses and is exposed as disabled.
9. Focus from the keyboard shows a ring at least 3:1 against its surroundings.
10. A glyph button that confirms an action by changing its glyph also announces the outcome in words.
11. In high-contrast mode it keeps a border, and its glyph and focus stay visible.
