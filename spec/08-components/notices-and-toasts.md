# Notices and toasts

Notices and toasts tell the reader something the application has to say, such as that a save failed, that a record is over a limit, or that a report was sent. A notice stays in the view until the reader deals with it or the view changes. A toast is a passing confirmation that appears over the view and leaves by itself after a few seconds. An error the reader must act on is always a notice, because a toast goes away before some readers have seen it.

## Anatomy

### Kinds

Notices and toasts come in the same four kinds, and each kind leads with a glyph of its own and carries an edge in a colour of its own, so the kind never rests on colour alone.

| Kind | Glyph | Colour |
|---|---|---|
| Information, the default | info | `accent` |
| Positive, something done | check | `positive` |
| Warning, something that needs attention | warning | `warn` |
| Danger, something that failed | stop | `danger` |

The kind's colour is called the notice colour below.

### Notices

A notice is a flat panel, set in the flow of the view where its message applies, such as at the top of a form the application refused. It is tinted with the notice colour mixed 9% into `surface`, bounded by a 1px line of the notice colour mixed 45% into `border`, and edged on its start side with a 4px bar of the notice colour. Its corners are `radius-sm`, and it has 12px (`space-3`) of padding above and below and 16px (`space-4`) either side. Its text is set at `text-md` in `text`.

Inside the panel, 12px (`space-3`) apart, are these parts.

- **The kind's glyph**, at 18px in the notice colour, level with the first line of text.
- **The content**, which is an optional title, set at `text-md` and weight 700 with 2px below it, then the message, then optionally a row of actions 8px (`space-2`) below the message. The actions are buttons, usually in the small size, 8px (`space-2`) apart and wrapping onto further lines when they must. An action leads to what the reader needs to do, such as "Edit the amount".
- **A dismiss button**, optionally, at the end.

### Toasts

A toast is a small panel lifted above the view. It is filled with `dialog-bg`, bounded by a 1px line in `border`, edged on its start side with a 4px bar of the notice colour, and has `radius-sm` corners. It casts `shadow-card` together with a soft shadow of `shade`, 10px below it and blurred over 28px, at 1.4 times the strength `depth` sets. It has 12px (`space-3`) of padding above, below and at its end, and 16px (`space-4`) at its start. Inside it, 12px (`space-3`) apart, are the kind's glyph at 18px in the notice colour, the message set at `text-md` in `text`, and a dismiss button at the end.

Toasts gather in a stack at the foot of the window, in its end corner, 16px (`space-4`) from the foot and from the end side. The stack is as wide as 384px or the window less 32px, whichever is smaller, and each toast fills its width. The toasts are 8px (`space-2`) apart, and a new toast joins the stack at the foot. The space between and around the toasts does not catch presses, so the reader can still press what lies beneath it.

### The dismiss button

The dismiss button of a notice or a toast is a small raised button, 24px across and fully rounded, filled with `raise-grad`, bounded by `raise-border` and shadowed with `raise-shadow`. It holds the close glyph at 12px in `text-muted`. Its accessible name says what it does, such as "Dismiss", and it shows that name as a tooltip.

## States

| State | Appearance |
|---|---|
| A notice shown | In the flow of the view, as above |
| A notice dismissed | Gone from the view, and the space it held closes |
| A toast arriving | It joins the foot of the stack |
| A toast leaving | It fades and drops 8px over 200ms, then is removed; with reduced motion it is removed at once |
| A dismiss button under the pointer | The fill becomes `raise-grad-hover` and the glyph `text` |
| A dismiss button focused from the keyboard | A 3px ring in `focus-ring` outside its border |

## Interaction

A notice stays until the reader presses its dismiss button, where it has one, or until the application removes it, such as when the reader corrects what it reported.

A toast leaves by itself 5 seconds after it appears, unless the application gives it a different time. Its time stops running while the pointer is over it or focus is inside it, and runs on for the time that was left once both have gone, so a reader who is reading it or about to press its dismiss button does not lose it. The application MAY make a toast stay until the reader dismisses it. Pressing a toast's dismiss button starts it leaving at once.

A toast that is present when a view first appears, such as one confirming a save after the application has moved the reader to a new view, MUST be announced as a toast raised afterwards is.

## Accessibility

The stack of toasts is exposed as a status region whose changes are announced politely, so assistive technology reads each toast as it arrives, after whatever it is already saying. A notice that appears after the view has loaded SHOULD be exposed so that it is announced: as an alert when it reports a failure, and as a status otherwise.

The kind's glyph is drawn and not exposed. Where the message alone does not make the kind plain, its words SHOULD say it, as "The expense could not be saved" does.

In the platform's high-contrast mode, a notice and a toast keep a visible border and their 4px edge, their glyphs are drawn in the system's text colour, and the dismiss button keeps a visible border.

## Questions this section must settle

- What happens to a toast raised while a modal dialog is open. The web implementation draws the stack beneath the dialog's backdrop, where the toast is dimmed and its dismiss button cannot be reached.
- Whether a toast may carry an action, such as Undo, which the buttons section suggests a destructive action should offer. An action that leaves after five seconds is hard to reach for a reader who is slow, uses a keyboard or uses a screen reader, and WCAG 2.2 success criterion 2.2.1 bears on it.
- What a danger toast is for, given that an error the reader must act on is always a notice, and whether it is announced more urgently than the other kinds.
- Whether the kind of a notice or a toast must be exposed to assistive technology in its own right, since chapter 2 requires every shown state to be exposed and today the kind is carried only by the glyph, the colour and whatever the words say.
- Whether the five seconds a toast stays is part of the language or a default each platform may change, and whether a reader may lengthen it.
- How many toasts may stand in the stack at once, and what happens to the oldest when more arrive.

## Conformance checklist

1. Each kind of notice and toast leads with its own glyph and carries a 4px edge in its own colour on its start side.
2. A notice is flat and sits in the flow of the view; a toast is lifted above the view in a stack at the foot of the window's end corner.
3. A notice stays until it is dismissed or the application removes it.
4. A toast leaves by itself after 5 seconds by default, its time stops while the pointer or focus is on it, and a toast made to stay remains until it is dismissed.
5. The dismiss button is a raised button with the close glyph, an accessible name, and a tooltip showing that name.
6. The stack of toasts is announced politely by assistive technology as each toast arrives, including a toast present when the view first appears.
7. A toast's leaving motion is removed when the reader has asked for reduced motion.
8. Every message reaches 4.5:1 against its panel in every kind, in both themes.
9. In high-contrast mode a notice and a toast keep a border, their start edge and a visible glyph.
