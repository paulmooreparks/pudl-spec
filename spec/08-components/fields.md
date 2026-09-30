# Fields and form states

A field is where the reader enters a value. PUDL has three kinds of field, and each is sunken, because each takes input. This section also covers what surrounds a field in a form: the label that names it, the hint that helps with it, the mark of a field that must be filled in, the message that says its value was refused, the read-only and disabled forms of a field, and the group that holds a set of related choices.

## Anatomy

A field is a sunken surface. Its fill is `input-bg`, its border a 1px hairline in `input-border`, its shadow `entry-shadow`, which falls inside its top edge, and its corners are `radius-sm`. Its value is set in the interface face at `text-md`, in `text`, with 8px of padding above and below and 11px either side. A field takes the full width of the space it is given, and the application narrows that space where a value is short, as a date or an amount is.

`input-border` is `text` mixed 55% into `surface`, and it reaches 3:1 against every surface a field sits on, in both themes, so the border alone meets chapter 3's contrast for the bounds of a control.

The figures in a field are tabular, since what a field holds is data.

A field that is empty MAY show a placeholder, a short example of what it takes, in `text-muted` at full opacity, which reaches about 5.5:1 against `input-bg`. A placeholder never stands in for the label, because it disappears as soon as the reader types.

A field sits in a group with the words that belong to it, stacked in this order with 6px between them:

1. The **label** comes first, set at `text-sm` and weight 600 in `text`. It says what the field holds, and it is the field's accessible name.
2. The field comes next.
3. The **hint**, if the field has one, is set at `text-sm` in `text-muted`. It says something the reader needs in order to fill the field in, such as "As printed on the receipt".
4. The **error message** shows while the field's value is refused. It is set at `text-sm` in `danger` and led by the `warning` glyph at the size of its text, 6px from the words, and it says what is wrong and, where it can, what would be right, such as "The amount must be a number greater than zero".

Groups follow one another `space-4` apart.

The label of a field that must be filled in carries a mark after it, 3px from the label's words, in `danger`. The web implementation draws an asterisk.

A set of related choices, such as radio buttons, sits in a group with a border and a title. The group's border is a 1px hairline in `border` with corners of `radius-sm`, and its padding is 12px at the top and 16px at the sides and the foot. Its title is set at `text-sm` and weight 600, and sits in the top border with `space-1` either side. The choices inside it stack `space-2` apart, or run along a line, wrapping, `space-2` apart between lines and `space-5` apart along them. Each choice is a checkbox or a radio button 16px square, tinted with the accent, with its words `space-2` after it at `text-md`, and the words are part of what the reader presses.

A field for choosing a file is a raised button, with 6px of padding above and below and 12px either side and its label at `text-sm` and weight 600. It has the states of a button, so it is drawn pressed in while it is pressed. The button is followed `space-3` later by the chosen file's name as flat text at `text-sm` in `text-muted`.

## Kinds

- A **text field** takes one line of text, and is 36px tall whatever kind of value it takes, so that fields side by side in a form line up. A field for a date, a number or a search is a text field.
- A **select** takes one choice from a list. It is 36px tall like a text field. A select that shows several rows of its list at once in the page, rather than opening a list, keeps the height of those rows.
- A **text area** takes several lines of text. It is at least five times its text size tall, 70px at `text-md`, with lines 1.5 times its text size apart. Where the platform lets a reader resize it, it grows in height only.

## States

| State | Appearance |
|---|---|
| At rest | Sunken, as above |
| Focused | The border becomes `accent`, and a 3px ring in `focus-ring` shows outside it, however the field was reached |
| Invalid | The border becomes `danger`, and while focused the ring is `focus-ring-danger`; the error message shows below it |
| Required | The label carries its mark |
| Read-only | Flat: no fill, no border and no shadow, with no padding at the sides, so the value lines up with the text around it |
| Disabled | Sunken as at rest, and dimmed to 55% opacity; it takes no input |

A read-only field is flat because the reader can read its value and cannot change it. It MUST NOT be drawn sunken, which would promise input it does not take. Read-only is the one state in which a field is flat.

A disabled field of any kind, a select included, keeps its sunken look and is dimmed, as chapter 2 requires, so the reader learns that the field exists and would take input. Where the reason is not obvious, the application SHOULD say why nearby.

An invalid field MUST NOT rely on the colour of its border. The error message, with its glyph and its words, is the second signal chapter 2 requires, and it MUST be shown whenever the field is marked invalid.

## Interaction

A field is one stop in the keyboard's tab order. Pressing its label moves focus into it, and pressing the words of a checkbox or a radio button changes it. Focus shows whether it arrived from the keyboard or the pointer, because the ring tells the reader where the next key they type will go.

A form the application refuses SHOULD come back holding every value the reader entered, with each wrong field marked invalid and its message beneath it, and a notice at the top of the form saying what went wrong, as the section on notices specifies.

## Accessibility

A field is exposed with the role the platform gives its kind, with its label as its accessible name, and with its hint and its error message as its description. A field that must be filled in is exposed as required, and the mark after its label is hidden from assistive technology, which hears "required" from the field itself. An invalid field is exposed as invalid, a read-only field as read-only, and a disabled field as disabled. A group of related choices is exposed as a group named by its title.

In the platform's high-contrast mode a field keeps a visible border, and focus is drawn as a solid outline in the system's highlight colour.

## Questions this section must settle

- Whether a checkbox and a radio button are drawn by PUDL, sunken as chapter 2 would have them, or left to the platform and tinted with the accent, as the web implementation leaves them.
- Whether the mark on a required field's label may be a character from a font, which chapter 2's rule on glyphs forbids in chrome, or must be a drawn glyph. The same question applies to the opener of a select, which the web implementation leaves to the platform.
- Whether a disabled field and a disabled button share one dimming. A field dims to 55% and a button to 45%.
- When a field is checked: as the reader leaves it, as they type, or only when the form is sent. The web implementation shows only what the server returns.
- Where focus goes when a refused form comes back.
- Whether a text area's figures are tabular. What a text area holds is often prose, where chapter 2 keeps proportional figures.
- Whether fields have a small size, as buttons do. The web implementation's filter field in a toolbar is 30px tall with its text at `text-sm`, and no other field is.
- Whether a read-only field is a stop in the tab order, so that somebody using a screen reader can reach it, and whether it shows the focus ring when it is.

## Conformance checklist

1. A text field, a select and a text area are sunken at rest in both themes, and a read-only field is flat.
2. A field's border is `input-border`, and it reaches 3:1 against the surface the field sits on, in both themes.
3. A placeholder is `text-muted` at full opacity, and reaches 4.5:1 against `input-bg` in both themes.
4. A field's value is set at `text-md`, its label at `text-sm` and weight 600 above it, and its hint at `text-sm` in `text-muted` below it.
5. A text field and a closed select are 36px tall whatever kind of value they take.
6. A field is one tab stop, and pressing its label focuses it.
7. A focused field shows an accent border and a 3px ring, however it was reached.
8. A field's accessible name is its label, and its hint and error message are its description.
9. A field that must be filled in is exposed as required, and the mark on its label is not exposed.
10. An invalid field is exposed as invalid, has a danger border, and shows its error message, led by the `warning` glyph, below it.
11. A disabled field, a select included, is dimmed, stays sunken, takes no input and is exposed as disabled.
12. A read-only field is flat, shows its value, takes no input and is exposed as read-only.
13. The button of a field for choosing a file is raised, and is drawn pressed in while it is pressed.
14. A group of related choices is exposed as a group named by its title.
15. A field's value reaches 4.5:1 against `input-bg`, and an error message 4.5:1 against its background, in both themes.
16. In high-contrast mode a field keeps a border, and focus stays visible.
