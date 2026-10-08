# Changelog

## 0.16.0

- Shared side docks can show several windows through tabs and collapse to icon rails. Required windows remain available, and each dock restores its selected tab and open or rail preference. Window status marks appear in the tabs, rails and taskbar.

## 0.15.0

- **A `pencil` glyph**, for editing or renaming something in place, so that an icon button for either needs no glyph of its own.

## 0.14.0

- **Layout**, a section of its own: a stack, a row that wraps and may align its components or push its last to the end, and a grid of as many equal columns as fit at a least width. Each places its components in document order, with a gap from the spacing grid, never overlapping them, never at fixed positions and never making its space wider. It is the grammar's layout category, with no surface and nothing exposed. PUDL Studio's canvas arranges components with these, and every application needed them.

## 0.13.0

From parkscomputing.com's proposals, for it and YAVCHN.

- **The sidebar's side.** An application may put a master-detail sidebar at the end edge of the reading direction, mirrored as in a right-to-left layout, keeping its order for the keyboard and its width and collapsed state.
- **Collapsing, and a peek.** The section now says that a reader may collapse the sidebar to its handle, and that an application may let the reader peek at a collapsed sidebar by resting the pointer on its handle or focusing it: the sidebar is drawn over the detail pane without moving it, and closes when the pointer or focus leaves, never changing the collapsed state or the width.

## 0.12.0

From YAVCHN's proposal, for patterns it and parkscomputing.com each built for themselves.

- **A filter menu**: checkbox rows in a menu that apply a filter at once, the panel staying open, or opening again with focus on the same box where the filter reloads what holds it.
- **A settings panel**: a column of cards, each a group of settings with its actions in a row at its foot.
- **A disclosure button**: a plain button that shows or hides content in place, with the new `chevron` glyph pointing down or up.
- **A window's default front menu**: a window whose content offers no menu has one title, the window's, with what every window offers.

## 0.11.0

- **The status area matches a menu bar's menus**, from YAVCHN's proposal. Where the application bar has a menu bar, the status area looks exactly like its menus, in surface, height and its items' colours and states, which are the titles'; only on a bar without a menu bar does it take the bar's own chip colours. It is 30px tall, as a menu is, with items 26px tall.
- A new glyph, `account`, for an account with no picture, drawn at a picture's size.

## 0.10.0

- **An article's Print is the application's to offer**, from parkscomputing.com's proposal. An article's first title offers printing only where the application says the article's printed form is worth having, since printing a page of windows prints the windows and the frame around them, and an article has no File title unless the application gives it one.

## 0.9.0

- **A status area in the application bar**, from parkscomputing.com's proposal. The last thing in the bar's chrome may be one raised group of flat items, each a glyph or a picture with an optional badge, for what runs in the background of the application, with the reader's account last. A badge with nothing to say is not shown, and an item's accessible name says what its badge means. A round picture needs no raised ring of its own, since the group is what is raised.
- **The window menu docks at every edge**, from parkscomputing.com's proposal. Its Dock at the bottom becomes a Dock list of Top, Bottom, Left and Right, ticking the edge the window is docked at, with Undock at its end on a docked window.
- A new glyph, `comments`.

## 0.8.0

- **A select's opener is PUDL's.** A closed select's opener is the `caret` glyph, drawn by the implementation in the select's text colour, and a platform's own drawing of a select is not used. This settles a question the section on fields had left open. The web implementation found that WebKit draws a select raised and lit, which broke the rule that a field is sunken.

## 0.7.0

- **A pins group in the menu bar**, from parkscomputing.com's proposal. Between the host menu and the front menu, an application may give the reader a group of the applets and articles they go to most: the `pin` glyph and a Pins title of pinning commands, then a link for each pinned item, with its icon and title. When the pins do not fit they give way together to an Items title, before the bar becomes one button, and the collapsed bar lists the Pins commands and then the pins. With nothing pinned the group keeps its Pins title.
- A new glyph, `pin`.

## 0.6.0

- **Menu bars**, from parkscomputing.com's proposal. An application's menu bar stands in its application bar, holding the host's menu and the menu of whatever is in front, an applet or an article. Each menu is one raised surface with flat titles; a front menu may add to the host's titles but never take or change one. The bar is one tab stop and follows the WAI-ARIA menu bar pattern; it becomes one menu button when it does not fit. Shortcuts use `Mod` for the platform's command key and keep off the keys browsers and fields need. With a menu bar, an applet's commands live there and the window menu keeps the window's own.
- **Applets** may offer a front menu in full, as titles and additions to the host's titles.
- A new glyph, `menu`.

## 0.5.1

- A window the reader brings forward takes the keyboard, on the element that last had focus in it, or the first time on an element the content marks, or else on its title bar.

## 0.5.0

- **Tabs in the application bar.** The bar may hold an application's main sections as tabs, as a browser puts its tabs in its title bar. The current tab covers the bar's bottom line and takes the colour of what lies below, so it opens into the page; on a narrow screen the tabs take the bar's last row.

## 0.4.0

- **A segmented control in a narrow space** may become a pop-up button labelled with the current choice, whose menu lists every choice with the current one ticked, as a desktop view switcher does in a narrow window. The application says which controls may collapse, and a control never collapses on a wide screen.

## 0.3.2

- A docked window's free edge carries the `grip` glyph at rest, as every handle does, so it can be seen to resize.

## 0.3.1

- A window sized by its content has a frame of a single hairline, with no frame band, so it does not look as if its edges could be dragged.

## 0.3.0

- **Windows sized by their content.** A window is sized either by the reader or by its content, as a desktop window has a sizing border or is a dialog that sizes itself. A window sized by its content takes its content's size and follows it as it changes, larger and smaller, from a fixed top-left corner, stops at the edge of the workspace where its body scrolls, and cannot be resized, maximised, snapped or docked. An applet in it flows. From parkscomputing.com's proposal on window sizing.
- **Limits on windows the reader sizes.** A window MAY carry a smallest and a largest size, which dragging, the keyboard and restoring an arrangement all respect.

## 0.2.1

- **Segmented controls return to a raised thumb.** 0.2.0 drew the chosen segment pressed in beside raised ones, and with two choices the state was hard to read. A segmented control is now defined as a switch with more than two positions, as macOS and iOS draw it: the trough is the track, the chosen segment is the raised thumb, and the other positions lie flat on the track. Chapter 2 states the rule for switches and segmented controls together.

## 0.2.0

Every chapter and every component section is drafted, and the grammar is settled where drafting them found it unclear. Paul Parks made these decisions on 2026-10-01.

- **Where the reader is.** In a set of raised controls, the one for where the reader is, or the one chosen, is drawn pressed in and exposed as current or chosen. Tabs are the exception: the current tab stands flat, taller, open into the content below.
- **Segmented controls.** The chosen segment is pressed in and the others stand raised.
- **Lists of places and choices** are a category of their own, drawn flat: sidebar rows, tree nodes, menu rows and rows to choose from. They respond under the pointer and mark the current row by more than colour. Links in running text are underlined, and tabs and these rows are not.
- **Handles**, the things a reader drags, are flat and carry the new `grip` glyph at rest.
- **Every raised control** is pressed in while pressed, and dims to 45% when disabled.
- **Tokens.** New: `input-border`, which reaches 3:1 against every surface in both themes for the bounds of fields and switch tracks; `shadow-dialog` and `backdrop`; `radius-xs`, 4px, for small parts inside another control.
- **Glyphs.** New: `grip` and `theme`.
- **Chapter 2** names the badge shapes correctly: a warning badge carries a triangle and an error badge a square.

## 0.1.0

The specification separated from the web implementation, as `docs/proposals/spec-and-implementations.md` in paulmooreparks/pudl proposed and Paul Parks decided on 2026-09-30.

- The introduction, the grammar, the tokens chapter and the button are written. The other chapters are outlines that list the questions each must settle.
- The palette and the scales are in the Design Tokens Community Group format, 2025.10. The derived tokens are formulas in `derived.json`, which chapter 3 defines.
- The 36 glyphs are SVG files on a 16-unit grid.
- Every value is the one the web implementation's 0.33.0 used, so its generated token block computes exactly as its hand-written one did.
