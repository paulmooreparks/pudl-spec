# Switches

A switch turns one setting on or off, such as "Show hidden files" or "Send me a daily summary". It is made of a raised thumb that runs in a sunken track, with the setting's name beside it, and it shows whether the setting is on by where the thumb sits as well as by colour.

## Anatomy

The track is sunken, since it is the slot the thumb runs in. It is 40px wide and 22px tall with fully rounded ends (`radius-pill`), filled with `recess-bg`, bounded by a 1px hairline in `input-border`, which reaches 3:1 against the surface around it as the bounds of a control must, and shaded inside its top edge by `entry-shadow`.

The thumb is raised, since it is the part the reader presses. It is a circle 16px across, 2px inside the track's border at the top and at the end it rests against, and it is drawn as a button is: its fill is `raise-grad`, its border a 1px hairline in `raise-border`, and its shadow `raise-shadow`.

The label follows the track, 10px after it in reading order, in `text` at the size of the text around the switch. It names the setting in words that stay true whether the switch is on or off, such as "Show hidden files". The track, the thumb and the label make up one control, and pressing any part of it changes the switch.

When the switch is on, the track fills with `accent` and its border becomes `accent-hover`, and the thumb sits at the far end of the track, 18px from where it rests when off. On a right-to-left page the far end is the left. The thumb MAY slide between the ends over about 150 milliseconds, and it MUST move at once for a reader whose system asks for reduced motion.

## States

| State | Appearance |
|---|---|
| Off | The track in `recess-bg`, with the thumb at the start |
| On | The track in `accent` with its border in `accent-hover`, and the thumb at the far end |
| Under the pointer | The thumb's border becomes `raise-border-hover` |
| Pressed, while the pointer or key is down | The thumb is pressed in: its fill becomes `raise-active-bg` and its shadow `raise-active-shadow` |
| Focused from the keyboard | A 3px ring in `focus-ring` outside the track's border |
| Disabled | Drawn as off or on, and dimmed to 45% opacity; it takes no pointer or key presses |

A switch's state MUST show through the thumb's position as well as the track's colour, so a reader who sees no colour can still tell on from off. It MUST be exposed to assistive technology as checked or not checked.

A disabled switch keeps its track sunken and its thumb raised, as chapter 2 requires, so the reader can still see which way the setting stands.

## Interaction

A switch is one stop in the keyboard's tab order. The platform's usual keys change it, which are Space and Enter on the web. A press with the pointer counts when the pointer is released over the switch. Each press turns the switch to the other state.

A switch MUST NOT change on a pointer entering it or resting on it.

## Accessibility

A switch is exposed with the switch role, its label as its accessible name, and its state as checked or not checked. A disabled switch is exposed as disabled. In the platform's high-contrast mode the track and the thumb keep visible borders, the track of a switch that is on takes the system's highlight colour, the thumb is filled with the system's background colour so it stands out against either track, and focus is drawn as a solid outline in the system's highlight colour.

## Questions this section must settle

- When a switch is the right control, and when a checkbox or a toggle button is. The web implementation offers a switch for a preference, a checkbox for a choice inside a form and a toggle button for a mode, but the language has not written these down as rules.
- Whether a switch takes effect the moment it is pressed, or waits, like a field, for the form around it to be sent. The web implementation's switch is a button whose state the application's own script changes, so it sends no value with a form on its own.
- Whether a reader on a touch screen may drag the thumb from one end to the other, as the switches of the phone platforms allow.
- Where the label goes in a list of settings on a phone, where the platforms' own switches put the label first and the switch at the far end of the row.
- Whether a switch has a small size for dense lists of settings.

## Conformance checklist

1. A switch's track is sunken and its thumb raised, in both themes and in both states.
2. The track is 40px by 22px with fully rounded ends and a border of `input-border` that reaches 3:1 against its surroundings in both themes, and the thumb is a circle 16px across.
3. When the switch is on, the track is filled with the accent and the thumb sits at the far end, which is the left on a right-to-left page.
4. Its state shows through the thumb's position as well as colour, and is exposed as checked or not checked.
5. It is one tab stop, the platform's usual keys change it, and a pointer press counts only when released over it.
6. Pressing its label changes it, and its accessible name is its label.
7. The thumb is pressed in while the switch is pressed.
8. A disabled switch is dimmed to 45%, keeps both elevations and its position, takes no presses and is exposed as disabled.
9. Focus from the keyboard shows a ring at least 3:1 against its surroundings.
10. With reduced motion the thumb moves without animating.
11. In high-contrast mode the track and thumb keep borders, and the on state and focus stay visible.
