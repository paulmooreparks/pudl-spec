# Buttons

A button performs an action when the reader presses it. It is the plainest raised control, and the model the other raised controls follow.

## Anatomy

A button is a raised surface holding a label, a glyph, or a glyph and a label. The label is short and says what pressing the button does, in the verb form where one fits, such as "Save" or "Add a receipt". A button with only a glyph MUST have an accessible name that says the same, and SHOULD show it as a tooltip.

The raised surface is drawn from the derived tokens. Its fill is `raise-grad`, its border a 1px hairline in `raise-border`, its shadow `raise-shadow`, and its corners are `radius-sm`. Its label is set in the interface face at `text-md` and weight 600, in `text`, on one line.

A button has two sizes. The default size has 7px of padding above and below the label and 14px either side. The small size, for toolbars and dense rows, has 4px and 10px and sets its label at `text-xs`.

## Kinds

- A **plain** button performs an ordinary action.
- A **primary** button performs the one primary action of its context, as chapter 2 requires. It is filled with the accent, lit toward its top, and its label is in `on-accent`. A visible context MUST NOT hold more than one.
- A **danger** button performs an action that destroys something or cannot be undone. It is a plain button whose label is in `danger` and whose border leans toward it, so the danger shows before the reader touches it; under the pointer it fills with `danger`. The danger colour is never its only signal: its label says what it destroys, and the action SHOULD ask for confirmation or offer an undo.

## States

| State | Appearance |
|---|---|
| At rest | Raised, as above |
| Under the pointer | The fill becomes `raise-grad-hover` and the border `raise-border-hover`, a touch darker, so it responds without changing elevation |
| Pressed, while the pointer or key is down | Pressed in: the fill becomes `raise-active-bg` and the shadow `raise-active-shadow`, cast inside the top edge |
| Focused from the keyboard | A 3px ring in `focus-ring` outside its border, in addition to its other state |
| Latched on, for a toggle button | Pressed in, as while pressed, until it is pressed again |
| Disabled | Raised as at rest, and dimmed to 45% opacity; it takes no pointer or key presses |

A toggle button is a button that stays on after it is pressed, and off after it is pressed again. Its on state MUST show through elevation, as a latched button pressed in, and MUST be exposed to assistive technology as pressed. Colour alone MUST NOT show it. A primary toggle button latched on keeps its accent fill and loses its light, since darkening it would swallow the dark text the dark theme's accent carries.

A disabled button stays visible and keeps its elevation, so the reader learns the action exists. Where the reason is not obvious, the application SHOULD say why it is disabled nearby.

## Interaction

A button is one stop in the keyboard's tab order. The platform's usual keys press it, which are Enter and Space on the web and on the desktop platforms. A press with the pointer counts when the pointer is released over the button, so a reader who presses by mistake can slide away and let go.

A button MUST NOT act on a pointer entering it or resting on it. A button MAY open a menu, and it is then a menu button, which chapter 8's section on menus specifies.

## Accessibility

A button is exposed with the button role and its accessible name. A toggle button is also exposed as pressed or not pressed. A disabled button is exposed as disabled, and remains perceivable. In the platform's high-contrast mode a button keeps a visible border, focus is drawn as a solid outline in the system's highlight colour, and a latched toggle takes the system's highlight colours, since its change of elevation would not show there.

## Conformance checklist

1. A button is raised at rest and pressed in while pressed, in both themes.
2. Its label is `text-md` at weight 600 in the default size, and `text-xs` in the small size.
3. It is one tab stop, and Enter and Space press it.
4. A pointer press counts only when released over it.
5. Its accessible name is its label, or for a glyph-only button, words that say what it does.
6. A toggle button latched on is pressed in, is exposed as pressed, and does not rely on colour.
7. A disabled button is dimmed, keeps its elevation, takes no presses and is exposed as disabled.
8. Focus from the keyboard shows a ring at least 3:1 against its surroundings.
9. Its label reaches 4.5:1 against its fill in every kind and state except disabled, in both themes.
10. In high-contrast mode it keeps a border, and focus and the latched state stay visible.
11. A view offers at most one primary button.
