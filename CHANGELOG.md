# Changelog

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
