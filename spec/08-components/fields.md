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

The label's line MAY carry, at its end, a command that acts on the field, such as a menu that inserts a reference into the text, or a button that fills the field from elsewhere. The line is then a row with the label at its start and the command at its end, aligned on the label's baseline, and the command is a small raised control, a small button, a glyph button or a menu button, never a field, since it holds no value. When the line is too narrow for both, the command wraps under the label at the line's start rather than squeezing the label. The command has a name of its own; the label still names the field and nothing else.

The label of a field that must be filled in carries a mark after it, 3px from the label's words, in `danger`. The web implementation draws an asterisk.

A set of related choices, such as radio buttons, sits in a group with a border and a title. The group's border is a 1px hairline in `border` with corners of `radius-sm`, and its padding is 12px at the top and 16px at the sides and the foot. Its title is set at `text-sm` and weight 600, and sits in the top border with `space-1` either side. The choices inside it stack `space-2` apart, or run along a line, wrapping, `space-2` apart between lines and `space-5` apart along them. Each choice is a checkbox or a radio button 16px square, tinted with the accent, with its words `space-2` after it at `text-md`, and the words are part of what the reader presses.

A field for choosing a file is a raised button, with 6px of padding above and below and 12px either side and its label at `text-sm` and weight 600. It has the states of a button, so it is drawn pressed in while it is pressed. The button is followed `space-3` later by the chosen file's name as flat text at `text-sm` in `text-muted`.

## Kinds

- A **text field** takes one line of text, and is 36px tall whatever kind of value it takes, so that fields side by side in a form line up. A field for a date, a number or a search is a text field.
- A **select** takes one choice from a list. It is 36px tall like a text field. Its opener is the `caret` glyph, 12px across, standing 11px in from its end edge and centred on its height, in the colour of its text, and the text stops short of it. The implementation draws the opener, so that the select is sunken and looks the same on every platform; a platform's own drawing of a select is not used, since it may be raised or lit. A select that shows several rows of its list at once in the page, rather than opening a list, keeps the height of those rows and has no opener.
- A **combo box** is a text field with a list of suggestions. The reader may type any value or choose one from the list, and the value is whatever the field holds. At its end edge stands its opener, a raised strip 34px wide holding the `caret` glyph, set inside the field's border behind a 1px hairline in `raise-border`. The field is sunken because it is typed in, and the opener is raised because it is pressed. The field's border, focus ring, danger border and dimming go round the whole control, opener included, and the opener shows its own keyboard focus as a 2px ring in `focus-ring` inside its strip. Every field with a key in it is drawn this way: the number field, the password field, the date and time fields, the year in a calendar's chooser and a toolbar's filter with its apply button. That is what tells a combo box from a select, whose whole surface opens it and whose caret stands inside it. The list is drawn as a menu is, below the field, or above it where there is no room below, at least as wide as the field. Each row shows a suggestion, with a line of description under it in `text-muted` at `text-xs` where it has one, the row whose value equals the field's carries the `tick` glyph, and the row the keyboard is on is drawn as a focused menu row. A suggestion MAY have keys, words the reader can find it by that are not its value, such as a currency's code for a suggestion whose value is its sign.
- A **searchable select** is a select drawn as a combo box: the reader types to find a choice in a long list, and its value is still always one of its choices.
- A **slider** takes a value in a range. Its track is sunken, since it takes input, 16px tall with fully rounded ends, filled with `accent` from its start to the value. Its thumb is raised, since it is dragged, a disc 24px across that takes the focus ring. The value stands beside it in words, in the page's language. A slider sets a value roughly, so where the exact value matters a number field stands beside it and the two keep step.
- A **number field** takes a number, typed or stepped. It is a text field whose digits sit at its end, as numbers in a column do, with two raised keys, minus and plus, inside its border at its end as a combo box's opener is, full height so they are easy to hit, each dimmed at the end of the range it moves toward. The field reads and writes numbers in the page's language, its decimal and group separators and its digits, and gives the application a plain number, so a reader in Germany types 1.234,5. It refuses letters, snaps a typed value to its step and keeps it within its range. Up and Down step it, Page Up and Page Down by ten steps, the keys repeat while held, and the wheel steps it as chapter 2 allows.
- A **password field** is a text field with a raised key inside its border at its end that shows the password, reading Show, and pressed in while the password shows, when its word reads Hide; an application MAY use the `eye` glyph instead of the word, struck out while the password shows. Its accessible name stays "Show the password" while its pressed state says whether it is on. While the field has focus and Caps Lock is on, a line under it says so, led by the `warning` glyph; it takes no room otherwise. Pasting into it is never blocked, since blocking it pushes readers to weaker passwords.
- A **list box** shows several rows of a list in a form and takes one choice or several from them, where a select is too small to show the list and check boxes would be too many. It is sunken, as every field is, as many rows tall as the application asks and scrolling beyond that. Each row is drawn as a menu's row and carries a check box where several may be chosen, or a radio button where one may, since a list box sets state and those are the controls that invite a press to set it; a list that only reports state would carry ticks instead. A heading over a group of rows is drawn as a menu's section label.
- A **token field** takes several values, each shown as a chip with its own remove key, gathered below a plain field the reader types in, so the field's width never moves as values come and go. It offers suggestions as a combo box does, with keys that look a value up. The values reach the application as one text joined by a separator the application chooses, a comma unless it says otherwise.
- A **date field** takes a date, and a **time field** a time. Each is a text field the reader types in, with a raised opener inside its border at its end, as a combo box has: a date field's opener shows a calendar, and a time field's a list of times. Under the field stands its echo line, at `text-xs` in `text-muted`, which says back in words what the field understood as the reader types, such as "Thursday, 1 February 2026" or "9:00 in the morning", an example of what it takes while it is empty, and that the text is not a date yet, or is outside the dates allowed, when it is. The echo line keeps its height whether it has words or not, so the form never moves. The value the application receives is always ISO 8601 in the Gregorian calendar, whatever the reader typed or saw. The field shows its value in the page's language and that language's calendar, numeric unless the application asks for the month by name, and in ISO 8601, with a 24-hour clock, where the page gives no language.
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

A combo box keeps focus in its field while its list is open, and follows the editable combobox with list autocomplete of the ARIA Authoring Practices.

- Typing filters the list to the suggestions whose value, description or keys contain what is typed, ignoring case, and opens it where any match; a list with no match closes. Typing MUST NOT complete the field by itself unless the application asks for it, since in a field that accepts new values a completed match is a value the reader did not type.
- Down opens the list and moves to the next row, and Up to the previous, wrapping around. Alt with Down opens the list without moving to a row, and Alt with Up closes it.
- Enter chooses the row the keyboard is on, putting its value in the field and closing the list. Pressing a row does the same.
- Escape closes the list. Escape with the list closed clears the field, unless the field must have a value.
- Tab leaves with the field as typed, and closes the list; leaving never chooses the row the keyboard is on.
- Text left in the field, by Tab, by Enter with no row lit or by moving away, that is exactly the value or one of the keys of one suggestion, and of no other, becomes that suggestion's value, so a reader who types a currency's code gets its sign. Text that several suggestions share stays as typed.
- Pressing the opener shows every suggestion, with the field's own value ticked, and pressing it again closes the list. The opener is not a stop in the tab order.

Choosing a suggestion tells the application that the field's value has changed, as typing does. A searchable select behaves the same, except that its value is always one of its choices: leaving it with text that names no choice puts back the choice it had. Its suggestions MAY come from the application as the reader types, after a pause, where the list is too long to hold in full.

A list box answers the complaint made most often about multiple selection elsewhere, that choosing several takes Ctrl with a press, which few people know, and that a press without it loses every choice made so far. In a list box where several may be chosen, a press or Space switches one row and leaves the others as they were; Shift with a press, or with Up, Down, Home, End, Page Up or Page Down, sets every row from the last one switched to the one reached as that row was set; and Ctrl with A, or Command on a Mac, chooses every row, or none when every row is already chosen. In a list box where one may be chosen, the choice follows Up, Down, Home, End, Page Up and Page Down. In both, the list is one stop in the tab order, the row the keyboard is on is lit as a focused menu row while the list has focus, typing letters goes to the next row that begins with them, and a disabled row can be reached but not chosen.

A token field answers the complaints that a chip must be deleted to fix a typo, that a pasted list stays one value, and that nothing says what ends a value. Enter, the separator, Tab or leaving the field adds what is typed, and a value already there is not added again, its chip shown instead. Pasting splits the text at the separator and at new lines, or at commas and new lines where the separator does not occur in it. Backspace in the empty field takes the last chip back into the field to be edited, as pressing a chip's words takes that chip; Escape puts an edited chip back as it was. Left in the empty field moves to the chips, where Left and Right move along them, Home and End go to the ends, Delete and Backspace remove one, and F2 takes one back to edit. An application MAY limit the number of values, and the field then says so beside the chips and takes no more.

An application MAY check each value before it is added, however it comes: typed, pasted, chosen from the suggestions or given by the application itself. The check may refuse a value with a message, or replace it with another, such as a pasted link with its domain; a repeat is found after the replacement. A value the reader gave that is refused stays in the field to be mended, the field is marked invalid and the message stands under it as a field's error does, until the reader changes what is typed. The application MAY also read, replace, add and remove the values itself, as when the same list changes elsewhere; each such change is checked as the reader's would be, redraws the chips, and is not reported to the application as a change the reader made.

A date field and a time field answer the complaints made most often about them elsewhere: the date read the wrong way round, the expected format not said, the long paging to a birthdate, the picker that will not let the reader type, the field that fights the caret, the week that starts on the wrong day, and the picker that looks different in every browser.

- **Typing.** A date field takes ISO 8601 in every language, the numbers in the language's own order with any separator, a four-digit year first, month names in the language and, where its calendar's months are the Gregorian ones, in English, the language's word for today, tomorrow or yesterday, a plus or minus sign and a number of days from today, digits of any script, a two-digit year as the year nearest today, and, in a calendar with eras, an era's name or initial before its year. A time field takes an hour alone, hours and minutes with or without a separator, the 24-hour clock, and a 12-hour time with its marker in any case, with or without points or a space, or in the language's own words; a bare hour in a 12-hour language is the morning, and the echo line says so. Text that does not parse, or a time not on the field's step, leaves the value as it was and marks the field invalid, and the echo line says why. The reader's text is never changed while it is being typed; leaving the field, or Enter, puts the value in the field's own form.
- **The calendar.** The opener, or Down or Alt with Down in the field, opens a month of the field's calendar below the field or above it, in a panel drawn as a menu's panel is. Its head holds raised keys for the previous and the next month and, between them and of their height, a raised key with the month and year that opens a chooser of the year's months, with the year as a field holding minus and plus keys, so that a distant month is a few presses away. Its foot holds a raised Today key and, where the field may be empty, a Clear key. The week begins on the language's first day. Each day is a cell at least 32px square, 36px on a touch screen; today is ringed in `accent`; the chosen day is pressed in and its number bold; a day outside the dates allowed is dimmed and struck through, and can be reached but not chosen. In the grid, Left and Right move a day, mirrored in a right-to-left language, Up and Down a week, Home and End to the week's ends, Page Up and Page Down a month, with Shift a year, Enter and Space choose and close, and Escape closes without choosing; focus returns to the field. A calendar other than the Gregorian shows its own months, with their own lengths, its own year and era, and its own digits where the language uses them.
- **The time list.** The opener, or Down, opens a list of times drawn as a combo box's list, at an interval the application may set to any whole number of minutes, such as 5, 6, 15 or 30, and otherwise at the field's step where that is 5 minutes or more, or every 30 minutes. The time nearest the field's value is lit and in view as it opens.
- **The wheel.** As chapter 2 allows, the wheel steps a focused time field to the next time on its step, or by a minute where it has none, and the year in the chooser by one, only while the pointer is over the field.

A form the application refuses SHOULD come back holding every value the reader entered, with each wrong field marked invalid and its message beneath it, and a notice at the top of the form saying what went wrong, as the section on notices specifies.

## Accessibility

A field is exposed with the role the platform gives its kind, with its label as its accessible name, and with its hint and its error message as its description. A field that must be filled in is exposed as required, and the mark after its label is hidden from assistive technology, which hears "required" from the field itself. An invalid field is exposed as invalid, a read-only field as read-only, and a disabled field as disabled. A group of related choices is exposed as a group named by its title.

A combo box and a searchable select are exposed as a combo box, with their list as a list box of options, the field as expanded while the list is open, and the row the keyboard is on as the field's active descendant. A row whose value is the field's is exposed as selected.

In the platform's high-contrast mode a field keeps a visible border, and focus is drawn as a solid outline in the system's highlight colour.

## Questions this section must settle

- Whether a checkbox and a radio button are drawn by PUDL, sunken as chapter 2 would have them, or left to the platform and tinted with the accent, as the web implementation leaves them.
- Whether the mark on a required field's label may be a character from a font, which chapter 2's rule on glyphs forbids in chrome, or must be a drawn glyph.
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
17. A closed select's opener is the `caret` glyph drawn by the implementation, in its text colour, and no platform drawing of the select shows.
18. A command at the end of a label's line is a small raised control with a name of its own, aligned on the label's baseline, and wraps under the label when the line is too narrow; the label still names only the field.
19. A combo box is a sunken field with a raised opener holding the `caret` glyph inside its border at its end, the border and focus ring going round both, and its list is drawn as a menu, the field's own value ticked and the keyboard's row lit.
20. Typing in a combo box filters its list by value, description and keys, never completes the field unless the application asked for it, and closes the list when nothing matches.
21. Down, Up, Alt with Down, Alt with Up, Enter, Escape and Tab behave as this section sets out, and focus stays in the field while the list is open.
22. Text left in a combo box that is exactly the value or a key of one suggestion alone becomes that suggestion's value, and text several share stays as typed.
23. A searchable select's value is always one of its choices, and leaving it with text that names none puts its choice back.
24. A combo box and a searchable select are exposed as a combo box with a list box, expanded while open, the keyboard's row as the active descendant.
25. A date or time field is a text field with a raised opener inside its border, with an echo line under it that keeps its height and says back in words what was understood, an example while empty, and why when the text is refused.
26. The value a date or time field gives the application is ISO 8601 in the Gregorian calendar, and the field shows it in the page's language and calendar, or in ISO 8601 where there is no language.
27. A date field takes every form of typing this section lists, in every language, and refuses without changing the value what it cannot read.
28. The calendar's head keys are one height, its month and year key opens a chooser of months with a year field and its keys, and its foot has Today, and Clear where the field may be empty.
29. The calendar follows the language's first day of the week and its calendar's months, rings today, presses in the chosen day, dims and strikes through the days not allowed, and moves and chooses by the keys this section lists.
30. The time list's interval is the application's, or the field's step where it is 5 minutes or more, or 30 minutes.
31. The wheel changes a date or time field only while it has focus and the pointer is over it.
32. A list box is sunken, its rows carry check boxes where several may be chosen and radio buttons where one may, and it is one stop in the tab order with the keyboard's row lit while it has focus.
33. In a list box where several may be chosen, a press or Space switches one row and keeps the rest, Shift sets a range, and Ctrl or Command with A chooses all or none; in one where one may be chosen, the choice follows the keys.
34. A token field gathers its values as chips below a plain field, adds a value on Enter, the separator, Tab or leaving, adds none twice, splits a paste, takes a chip back to edit on Backspace in the empty field or a press on its words, and gives the application the values joined by its separator.
35. A list box and a token field are exposed as a list box with its options and their selected state, and as a field with a list of its values, each value's remove key named for the value.
36. A slider's track is sunken and 16px tall with the accent to its value, its thumb raised and 24px, and its value shown in words.
37. A number field's digits sit at its end, its minus and plus keys are raised, inside its border and dimmed at the range's ends, it reads and writes the page's language, refuses letters, snaps and clamps, and steps by its keys, the arrow keys and the wheel as this section sets out.
38. A password field's Show key is pressed in while the password shows, keeps its accessible name, and the field says when Caps Lock is on and never blocks pasting.