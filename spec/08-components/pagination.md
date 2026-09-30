# Pagination

Pagination divides a long list into pages and lets the reader move between them. It sits with the list it pages, usually below it, and says which part of the list is in view. Each page is restorable state, as chapter 7 describes, so a reader can leave page 3 of a list, come back to it, or hand it to somebody else.

## Anatomy

Pagination is a row of parts, `space-1` apart, which wraps onto a second line when it runs out of width.

- A **summary** MAY come first, saying in words which records are in view, such as "Showing 21 to 40 of 132". It is set at `text-sm` in `text-muted`, with `space-3` after it.
- A **previous** control goes to the page before.
- The **page controls** each go to one page and are labelled with its number.
- A **gap** stands for a run of pages left out between two page controls. It is an ellipsis in `text-muted`, with `space-1` either side.
- A **next** control goes to the page after.

Every control is drawn raised, like a small button: fill `raise-grad`, a 1px border in `raise-border`, shadow `raise-shadow` and corners of `radius-sm`. Each is 32px high and at least 32px wide, with 10px of padding either side, and its words are set at `text-sm` and weight 600 in `text`, with tabular figures. The previous control leads with the `back` glyph at 12px, 4px (`space-1`) before its words, and the next control ends with the same glyph turned to point the other way. In a right-to-left language the two glyphs are mirrored, so each still points the way it goes.

The application chooses which page controls to show, and marks each run it leaves out with a gap. A list with few pages usually shows them all.

## States

| State | Appearance |
|---|---|
| At rest | Raised, as above |
| Under the pointer | The fill becomes `raise-grad-hover` and the border `raise-border-hover` |
| Pressed, while the pointer or key is down | Pressed in: the fill becomes `raise-active-bg` and the shadow `raise-active-shadow` |
| The current page | Pressed in: the fill becomes `raise-active-bg`, the shadow `raise-active-shadow` and the border `raise-border-hover`, because the reader is already there |
| Focused from the keyboard | A 3px ring in `focus-ring` outside its border, in addition to its other state |
| Unavailable, for previous on the first page or next on the last | Raised as at rest and dimmed to 45% opacity; it takes no presses |

The page controls are a set of raised controls offering places, so the one for where the reader is, the current page, is drawn pressed in, as chapter 2 requires, and exposed as current. Being on the current page is shown by elevation, so it does not rely on colour.

## Interaction

Each control that is available is one stop in the keyboard's tab order, and the platform's usual keys press it. Pressing a control shows its page of the list and changes nothing else in the view. An unavailable previous or next control takes no pointer or key presses.

On a screen 560px wide or less, the summary takes a line of its own above the controls, so the controls stay together on one line.

## Accessibility

Pagination is exposed as a navigation region with a name that says what it pages, such as "Pages of expenses", so a page with more than one list can tell them apart. Each control is exposed with its words as its name. The current page's control is exposed as the current page, and an unavailable control is exposed as disabled. The gap is hidden from assistive technology, since the page numbers either side of it already say what is missing.

In the platform's high-contrast mode each control keeps a visible border, the current page takes the system's highlight colours, since its change of elevation would not show there, and the glyphs are drawn in the system's button text colour. Pagination is left out of print.

## Questions this section must settle

- What pagination becomes on a narrow screen with many pages, beyond moving the summary to its own line. The web implementation leaves the choice of which pages to show to the application.
- Whether the language offers an alternative to pages for long lists, such as loading more rows as the reader reaches the end, and how that would stay restorable.

## Conformance checklist

1. Each available control is raised, 32px high and at least 32px wide, with its words at `text-sm` and weight 600 and tabular figures.
2. The current page's control is pressed in, and is exposed as the current page.
3. Every available control is drawn pressed in while it is pressed.
4. The previous and next controls carry the `back` glyph, pointing the way each goes, and mirror in a right-to-left language.
5. On the first page the previous control, and on the last page the next control, are dimmed to 45%, take no presses and are exposed as disabled.
6. Each available control is one tab stop and is pressed with the platform's usual keys.
7. Pressing a control shows that page, and the page in view is restored when the reader returns.
8. Pagination is exposed as a named navigation region.
9. A gap between page numbers is hidden from assistive technology.
10. Focus from the keyboard shows a ring at least 3:1 against its surroundings.
11. In high-contrast mode each control keeps a border, and the current page stays distinguishable.
