# The application bar

The application bar runs across the top of an application. It names the application, leads back to its home, and holds the few things that belong to the whole application rather than to any one page, such as links to its main places, the reader's account and the theme. It keeps colours of its own, so it can stay dark above a light page and the reader always knows where the application's frame ends and its content begins.

## Anatomy

The bar is a band the full width of the application. It is filled with `tb-grad`, which runs from a touch of `tb-fg` at its top edge down to `tb-bg`, has a 1px highlight of `tb-hi` along its top edge, and ends in a 1px line of `tb-border` along its foot. It is padded 10px above and below and 20px at each end. It holds two groups, 8px apart at the least: the brand at the start and the chrome at the end.

The **brand** is the application's name, a link to its home. It is set in the `font-display` face at `text-lg`, weight 700, with its letters drawn 0.01em closer than usual, in `tb-brand`. It MAY carry a mark before the name, 8px from it. The brand is not underlined, as chapter 2 allows, because its place in the bar already says what it is.

The **chrome** is a row of controls that belong to the whole application, 8px apart, pushed to the end of the bar. It holds any of these.

- A **pill** is a link or a button on the bar. It is raised, so it is never a label. It is filled with `tb-chip` and casts `tb-chip-shadow`, with corners of `radius-sm` and no border, padded 5px above and below and 12px at the sides, and its words are set at `text-sm`, weight 600, in `tb-chrome-fg`. A pill MAY carry a glyph before its words, 6px from them.
- A **menu button** opens a menu, as the section on menus specifies, and on the bar it takes the pill's colours.
- The **theme control** lets the reader choose the theme. On the web implementation it is a square pill, 28px on each side, holding the `theme` glyph and no words. The glyph is drawn, as chapter 2 requires of every glyph in PUDL's chrome.

A plain link in running text on the bar takes `tb-chrome-fg`, and stays underlined.

The bar MAY also hold a row of **tabs** between the brand and the chrome, for an application's main sections, as a web browser puts its tabs in its title bar. The row stands on the bar's foot. Each tab the reader can go to is raised in the bar's own colours, filled with `tb-chip` and casting `tb-chip-shadow`, with its top corners at `radius-sm`, its words at `text-sm` and weight 600 in `tb-chrome-fg`, padded 5px above and below and 14px at the sides, and it stands on the bar's bottom line. The tab for where the reader is follows the exception chapter 2 makes for tabs: it stands flat and 4px taller, bounded at its top and sides by a hairline in `tb-border`, and it covers the bar's bottom line and takes the colour of what lies directly below the bar, the page's `bg` unless the application says otherwise, so it opens into the page and its words are in `text`. On a narrow screen the tabs take the bar's last row, still standing on its foot, and scroll sideways when they do not fit.

## States

| Part | State | Appearance |
|---|---|---|
| Brand | Under the pointer | Its colour becomes `tb-link-hover` |
| Pill | At rest | Raised, as above |
| Pill | Under the pointer | Its words and glyph become `tb-chrome-hover-fg` |
| Pill | Current, the page the reader is on | Pressed in: its fill becomes black mixed at 24% into `tb-bg`, a shadow of black at 50% falls 1px inside its top edge with a 3px blur, and its words take `tb-fg` |
| Pill | Focused from the keyboard | A focus indicator that reaches 3:1 against the bar; see the questions below |
| Plain link | Under the pointer | Its colour becomes `tb-link-hover` |

The pills are a set of raised controls offering places, so the pill for the page the reader is on is drawn pressed in, as chapter 2 requires of where the reader is. It MUST be exposed as the current page, and it shows that by its elevation as well as its colour.

## Interaction

Each pill is one stop in the keyboard's tab order and acts as the link or button it is. The brand is a link and one stop.

The bar never makes the application wider than its window. On a screen too narrow for the brand and the chrome on one line, the chrome moves to a second line, at the end, and wraps within itself if it must.

When the application is 640px wide or less, the bar's padding becomes 8px above and below and 12px at each end. A pill that carries a glyph then shows its glyph alone, padded 8px at the sides, and its words are still spoken. A menu button on the bar cuts its words short with an ellipsis rather than widening the chrome.

## Accessibility

The bar is exposed as the application's banner. The brand is a link named by the application's name. A pill showing only its glyph keeps its words as its accessible name. The theme control has an accessible name that says what it does.

The bar's own colours are held to the same contrast as the page's: its text reaches 4.5:1 against its fill, and the bounds of a pill and a focus ring reach 3:1 against the bar.

In the platform's high-contrast mode the current pill takes the system's highlight colours, since its change of elevation would not show there.

A printed page leaves the bar out.

## Questions this section must settle

- How a pill shows its bounds in the platform's high-contrast mode. A pill has no border and is raised by its fill and shadow alone, both of which that mode removes, and the web implementation gives it no border there, unlike a button.
- How focus is drawn on the bar. The web implementation gives the brand, the pills and the theme control no focus ring of its own, so the browser's default outline shows, and the page's `focus-ring`, the accent at 26%, is not known to reach 3:1 against a dark `tb-bg`.
- What the theme control is. The reader's preference has three values, light, dark and following the system, and the web implementation's control is a single button that swaps light and dark, exposed as neither pressed nor checked. Whether the bar must carry a theme control at all is also open.

## Conformance checklist

1. The bar is filled with `tb-grad`, with a `tb-hi` highlight along its top and a `tb-border` line along its foot, in both themes.
2. The brand is at the start, set in `font-display` at `text-lg` and weight 700, links to the application's home, and is not underlined.
3. The chrome is at the end, and each pill in it is raised, set at `text-sm` and weight 600.
4. The pill for the current page is pressed in and exposed as current.
5. The theme control, where the bar has one, draws the `theme` glyph and has an accessible name that says what it does.
6. Text on the bar reaches 4.5:1 against the bar in both themes.
7. On a screen too narrow for one line, the chrome moves to a second line and the application does not grow wider than its window.
8. At 640px or less, a pill with a glyph shows its glyph alone and keeps its words as its accessible name.
9. The bar is exposed as the application's banner.
10. In high-contrast mode the current pill takes the system's highlight colours.
11. A printed page leaves the bar out.
12. Tabs on the bar stand on its foot; the current tab covers the bar's bottom line, takes the colour of what lies below the bar and is exposed as current, and the others stand raised on the line in the bar's colours.
13. On a narrow screen the tabs are the bar's last row and scroll sideways rather than widen the page.
