# Code blocks and editor surfaces

Code appears in two roles. A code block shows code for the reader to read, as a listing in an article or a snippet in a help page, and an editor surface is where the reader writes code. PUDL gives the two the elevations their roles call for, so a reader can tell at a glance whether the code in front of them can be changed, and it colours highlighted code in both from the same ten tokens.

## Anatomy

### Code block

A code block is flat, because it is for reading. It is a panel of `surface-alt` with corners of `radius-sm` and no border or shadow, padded 12px above and below and 16px at the sides, with 16px of space below it. Its text is set in the `mono` face at `text-sm`, with a line height of 1.55, in `text`. Tab stops are four characters apart. Lines keep their breaks and their spacing, and a line too long for the block runs past its edge, and the block scrolls sideways rather than wrapping it.

### Editor surface

An editor surface is sunken, because it takes input. It is filled with `input-bg`, bounded by a 1px hairline in `border`, with corners of `radius-sm` and the shadow `entry-shadow` falling inside its top edge, as a field has. Its text is set in the `mono` face at `text-sm`, in `text`. The editor that draws into the surface is the application's; PUDL specifies the surface and the colours of the code in it.

### Syntax colours

Highlighted code, in a block or on a surface, takes its colours from ten palette tokens, one for each role a piece of code can play.

| Token | Role | Also |
|---|---|---|
| `syntax-keyword` | Keywords and built-in names | |
| `syntax-string` | Strings and regular expressions, and lines added in a comparison | |
| `syntax-number` | Numbers, literal values such as true and null, and constants | |
| `syntax-comment` | Comments | Italic |
| `syntax-name` | Names being defined or called, such as functions, classes and parameters | |
| `syntax-tag` | Tags, element names and selectors in markup | |
| `syntax-attr` | Attributes and properties | |
| `syntax-heading` | Headings in a markup language | Weight 700 |
| `syntax-link` | Links and addresses | Underlined |
| `syntax-error` | Invalid code, and lines removed in a comparison | |

Code that plays none of these roles is in `text`. An implementation maps its highlighter's categories onto these roles as its highlighter requires, and the roles and their colours stay the same on every platform. The italic comment, the bold heading and the underlined link SHOULD be kept, because they carry their roles to a reader who cannot tell the colours apart. Each syntax colour reaches 4.5:1 on `surface`, `surface-alt` and `input-bg`, as chapter 3 requires of any theme that sets them, and a change of theme reaches highlighted code at once, with nothing highlighted again.

### Copy and download

A code block MAY offer the reader two actions, to copy its code and to download it as a file. When it does, a strip above the code holds them. The strip is flat, as the code is, and it sits outside the code itself, so that selecting or copying the code by hand never takes the strip's words with it. The block and its strip then share one panel of `surface-alt` with corners of `radius-sm`, and a 1px hairline in `border` divides the strip from the code.

The strip is padded 4px above and below, 16px at its start and 6px at its end. At its start it names the code's language, such as "C++" or "Python", at `text-xs` and weight 600 in `text-muted`, on one line, ending in an ellipsis if the strip is too narrow; a block whose language is unknown shows no name. At its end it holds two glyph buttons, 26px square, 4px apart, carrying the `copy` and `download` glyphs at 14px. They are raised, because they are pressed, and follow [the button's](buttons.md) states.

## States

| Part | State | Appearance |
|---|---|---|
| Code block | At rest | Flat on `surface-alt` |
| Code block | Focused from the keyboard | A 3px ring in `focus-ring` drawn inside its edge |
| Editor surface | At rest | Sunken, with a hairline in `border` |
| Editor surface | Focus within it | The hairline takes `accent`, and a 3px ring in `focus-ring` surrounds it |
| Copy button | For two seconds after a copy | Its glyph becomes the `check` glyph, drawn in `positive` |

The copy button's confirmation carries the change of glyph as well as the change of colour, and it is announced in words as well, as Interaction describes.

## Interaction

A code block that can scroll is one stop in the keyboard's tab order, so a reader who scrolls by keyboard can reach its hidden end. An editor surface takes focus as the editor inside it decides.

Copy puts the code's text on the clipboard, never its highlighting or the strip's words. The button then shows its confirmation for two seconds after the last copy, however many there were, and the word "Copied" is announced. Where the platform refuses the clipboard, or has none, the block selects its code instead and announces how the reader can copy it by hand, with the platform's own keys.

Download saves the code's text as a file. The file takes the name the application gives the block, such as `exercise-0-0.cpp`, and without one it is named `code` with the usual extension for the block's language, or `code.txt` when the language is unknown.

The application is told after each copy, and whether it succeeded, and after each download, with the file's name. The strip's words and the language names and extensions an implementation knows are the application's to extend and to translate.

## Accessibility

A code block is exposed as preformatted text, and its content reads as the code it holds. The copy and download buttons have accessible names that say what they do, such as "Copy code" and "Download code", and SHOULD show them as tooltips. The confirmation of a copy, and the instructions when a copy falls back to selecting the code, are announced through a live region that belongs to the strip. An editor surface is exposed as the editor inside it chooses, named for the document it edits.

In the platform's high-contrast mode a code block and an editor surface each keep a 1px border in the system's text colour, the highlight colours give way to the system's text colour, and links in code take the system's link colour; the italic comments, bold headings and underlined links still carry their roles.

A printed code block keeps its highlighting, in colours that read on white, and leaves out the strip's buttons.

## Questions this section must settle

- Which role a type name plays. The web implementation's two mappings disagree: its mapping for highlight.js colours types as keywords, and the mapping its README gives for CodeMirror colours them as tags.
- Whether a code block may wrap long lines, as a reader on a phone might prefer, or always scrolls sideways as it does today.

## Conformance checklist

1. A code block is flat on `surface-alt`, with `radius-sm` corners and no border or shadow, in the `mono` face at `text-sm`.
2. An editor surface is sunken on `input-bg`, with a hairline in `border` and `entry-shadow`, and its hairline takes `accent` with a 3px `focus-ring` while focus is within it.
3. A code block whose content can scroll is a tab stop, and its focus ring is drawn inside it.
4. Highlighted code takes each of its colours from the ten syntax tokens, and a change of theme recolours it at once.
5. Comments are italic, headings in markup are bold and links are underlined.
6. Each syntax colour reaches 4.5:1 on `surface`, `surface-alt` and `input-bg` in both themes.
7. A block offering copy and download shows a flat strip above the code naming its language, with two raised glyph buttons.
8. Copy puts the code's plain text on the clipboard, shows the `check` glyph for two seconds, and announces that it copied.
9. Where the clipboard is refused or missing, Copy selects the code and announces how to copy it by hand.
10. Download saves the code under the application's file name, else `code` with the language's extension, else `code.txt`.
11. In high-contrast mode code blocks and editor surfaces keep a visible border, and highlighted code reads in the system's colours.
