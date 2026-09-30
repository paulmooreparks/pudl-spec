# 4. Typography

PUDL sets text in three faces, each with a role, and at the nine sizes of the type scale in chapter 3. An implementation MUST use the scale for every size it sets, and MUST give each kind of text the face its role calls for.

## The faces

The token `font` names the interface face, in which body text, labels and controls are set. It MUST be a legible sans-serif face. PUDL ships Inter for it, so that an application looks the same whatever the reader has installed, and an implementation SHOULD ship Inter as well. The rest of the list in the token stands in until Inter has loaded, or where it cannot load.

The token `font-display` names the face for headings and the application's name. By default it is the interface face. A theme MAY give it a face of its own, and that face may be any legible face, serif included.

The token `mono` names the monospace face. It MUST be used for code and for values that are read character by character, such as identifiers, versions, hashes and file names shown as machine values.

Weights stay between 400 and 700, and PUDL uses three of them. Text is set at 400. Labels, controls and table headers are set at 600. Headings, titles and the current item of a list are set at 700.

## Sizes and line heights

Body text is `text-base`, 15px, with a line height of 1.6. A control's own text is `text-md`, 14px, and a small control's is `text-xs`, 12px. Labels, list rows and secondary text are `text-sm`, 13px. Section labels, meta lines and badges are `text-2xs`, 11px, and a section label is set in capitals with its letters spaced a little apart.

Each component section in chapter 8 names the size of every text it holds, and an implementation follows it.

## Headings

There are four heading levels, set in the display face at weight 700, with a line height of 1.25 and their letters drawn slightly together.

| Level | Size |
|---|---|
| First | `text-3xl`, 30px |
| Second | `text-2xl`, 24px |
| Third | `text-xl`, 20px |
| Fourth | `text-lg`, 17px |

A heading is followed by `space-3` before the text under it. A heading level MUST be chosen for its place in the document's outline and never for its size, since assistive technology reads the outline from the levels. A component that needs a title at another size, such as a card, sets its own and does not borrow a heading level to get it.

## Figures

Where numbers are data, their figures are tabular, so that every digit takes the same width and a column of numbers lines up. Tables, fields, badges, chips, list rows, dates and times, and any value marked as data use tabular figures. Numbers in running prose keep the face's proportional figures, which read better in a sentence; an implementation MUST still let an application mark a number inside prose as data, so that it can be tabular there too.

## Links

A link is set in the accent and underlined with a 1px line 2px below the text, so that it can be told from the text around it without relying on colour. Under the pointer it takes `accent-hover` and its underline thickens to 2px. A quieter link, for secondary places such as a footer, MAY be set in `text-muted`, and it keeps its underline. The application's name in the application bar is the only link that is not underlined, because its place already says what it is.

A link takes the reader somewhere, and a button performs an action. An action SHOULD be a button. A short action inside running text, such as "undo" at the end of a sentence, MAY be drawn as a link, and it is then exposed to assistive technology as a button, since that is what it does.

## Language and direction

Text follows the language and direction of its content. In a right-to-left language, the layout of every component mirrors, as chapter 6 sets out, and the faces are chosen by the platform where Inter lacks the script.
