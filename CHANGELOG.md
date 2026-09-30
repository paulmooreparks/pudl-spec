# Changelog

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
