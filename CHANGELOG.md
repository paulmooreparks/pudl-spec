# Changelog

## 0.31.0

From the maintainer's question of what PUDL lacks to be a complete UI library, and the controls he chose from mockups. Every control here is designed against the complaints made most often about it elsewhere, follows the reader's language and culture, and is built from the grammar.

- **The grammar.** A tick reports a state and a check box asks the reader to set one, so a component that sets state draws check boxes and one that reports it draws ticks. The wheel changes a field's value only while it has focus and the pointer is over it.
- **Context menus** (menus), opened by the secondary press, Shift with F10 or the Menu key, at the pointer or the focused element, with the menu bar's rows, glyphs in one column, and the platform's own menu where the application offers none or Shift is held.
- **Split buttons** (buttons), two joined keys whose menu lines up under the whole button.
- **Popovers**, a new section: a non-modal panel anchored to its control, with an optional pointer, head and actions, the head and actions pinned.
- **Progress bars and meters**, a new section: 16px flat bars always with words, a busy form that stands still for less motion, and meters banded by the application's thresholds in either direction, with the band's glyph, or with marks.
- **Images and avatars**, a new section: frames that keep their proportion, failures shown as words, neutral avatars with an optional tint by name, and status marks with shapes.
- **Steppers**, a new section: done, current and to come by shape and colour, done steps links back, the names but the current one hidden on a narrow window, and a form down the side.
- **Fields.** Sliders, number fields read and written in the reader's language, password fields with a Show key and a Caps Lock notice, list boxes whose rows carry check boxes or radio buttons and need no modifier keys, token fields with chips below the field and a separator of the application's choosing, and date and time fields: typed in any of the forms the reader is likely to use, echoed in words, shown in the page's language and calendar or in ISO 8601, with PUDL's calendar, a chooser of months and years, and a time list at any interval.
- **Dialogs** pin their head and actions by default, and an application may turn it off.
- **Segmented controls** are 30px tall, a menu bar's groups' height.
- **Glyphs:** `forward`, `eye` and `eye-off`.

## 0.30.1

- A combo box's text looks a suggestion up only when exactly one suggestion has it as its value or a key; text several suggestions share, such as a sign three currencies use, stays as typed.

## 0.30.0

From an application's need for a field that takes a typed value or a chosen one, and from the maintainer's review of the segmented control.

- **Combo boxes and searchable selects** (fields). A combo box is a sunken text field joined to a raised opener with a list of suggestions drawn as a menu; the reader may type any value or choose one. Typing filters the list and never completes the field unless the application asks. A suggestion may have keys it is found by that are not its value, and text left in the field that is exactly a key or a value becomes that suggestion's value, so a currency's code typed becomes its sign. A searchable select is a select drawn as a combo box, whose value is always one of its choices. Suggestions may come from the application as the reader types. Keys, exposure and conformance items are set out.
- **Segmented controls are keys** (grammar, segmented controls). Every choice that can be pressed is raised and the chosen one pressed in, joined in a row; the flat choices on a sunken track with a raised thumb are gone, since they drew the pressable choices as display.

## 0.29.0

From an agent that kept building tabbed dialogs that jumped as their tabs were chosen, and from the maintainer's review of the window menu.

- **Tabs in a dialog or a window keep one size** (tabs, dialogs, windows). Choosing a tab MUST NOT resize or move the dialog or the window. Tabs that are a window's whole content, or a dialog's content between its title and its actions, reach its sides, with the bar from edge to edge under the title and the panel taking the rest of the space. A dialog with more than a few tabs, or with settings the reader returns to, belongs in a window.
- **The window menu** (windows). Reset size and position ends the window's own commands. The layout picker and the Dock list follow, each under its heading, Snap or Dock, after a separator, where the menu has no submenus, so that snapping and docking are told apart; where it has submenus, both are submenus.

## 0.28.0

From the maintainer's decision that PUDL is AI-native, and from example.com's proposal that PUDL take in applet actions.

- **Agents** (chapter 1). PUDL is meant to be used by software agents as well as people. Where a part of the language gives a reader something to find out or to do, it SHOULD give an agent the same, by a documented, structured means that does not depend on reading the screen. A part about appearance alone has no such side, and none is invented for it.
- **Actions** (chapter 9). An applet may publish actions in a manifest: versioned references, input and output schemas in JSON Schema 2020-12, capabilities from a closed list the application may extend, and a replay rule, pure, once or human, now defined. A caller's grant decides what it may run; the reader holds everything, a script or an agent only what it is granted, and the application may ask the reader to allow more. Calls are checked at both ends and answer with a record. An action may be answered by the running applet. Request verbs are published as actions, and an action never navigates the page that called it. The five MCP tools an application and example.com share are the recommended binding for agents outside the page.

## 0.27.0

From the maintainer's request for splitters between windows side by side.

- The lines of the zones' grid can move. Where two snapped windows meet, a splitter on their shared line moves the whole line, by pointer and by keys, and every snapped window with an edge on it follows while the other dividing lines stay put. Lines never cross, keep each window at its least size, go back toward the grid when the inner area shrinks, and are forgotten once no two snapped windows meet across them. Enter or a double-click returns a line to the grid. Where two splitters cross, a handle moves both. The moved lines are part of the restorable arrangement.

## 0.26.0

From an application's proposals on danger controls and on starting applets.

- A danger button leads with the warning glyph, which the implementation draws unless the button already shows a picture of its own. A destructive menu action's glyph is drawn the same way, at 12px in the tick's space. The danger colour was the only mark on a danger button that did not carry the glyph in its markup.
- An applet may ask to start when its window is first seen, or when seen or once nothing else is starting, rather than when the window opens. Until it starts, its window shows the loading line and is busy, and stays busy until the instance says it is ready. A window closed before its applet started never starts it, and a host can ask whether a window's applet has started and start it at once.

## 0.25.0

From an application's proposals on a dialog's buttons.

- A dialog's title, with any head it shares with controls of its own, and its actions stay in view when its contents are taller than the window allows, and only the content between them scrolls. A 1px line in `border` separates the head or the actions from the content only while content is hidden beneath it, and a focused control is scrolled clear of both.
- A dialog's actions keep 24px (`space-5`) between them and whatever comes before them, a list or a table as well as the body.

## 0.24.3

- A menu bar's command may carry a picture of its own, such as an applet's icon, before its words, as a pin carries its item's icon. From Example's installed applet packages.

## 0.24.2

- **Restored.** The pills on a bar holding a menu bar take a plain button's surface in every theme, as 0.24.0 had it, so the bar's controls look uniform in both themes. 0.24.1's withdrawal is reversed at the maintainer's direction.

## 0.24.1

- **Correction.** 0.24.0 also gave the pills on a bar holding a menu bar a plain button's surface in the dark theme. The proposal asked that of the menus alone, and the pills keep `tb-chip` as before.

## 0.24.0

From Example's proposal.

- A menu bar's menu has the surface of a plain button in every theme, `raise-grad`, `raise-border` and `raise-shadow`, as though it were a button with the `menu` glyph at its start. It had the bar's chip colour, which matched a button in the light theme only.
- On a bar holding a menu bar, its pills and its status area take the same surface in the dark theme as in the light, so every pressable thing on the bar looks alike. (Withdrawn for the pills in 0.24.1.)
- The menu's glyph and titles are described in the colours the web implementation draws: `text` drawn toward `surface-alt`, `text` under the pointer, and the open title pressed in with `raise-active-bg`.

## 0.23.0

From an application's third batch of proposals.

- **Switching windows.** The order the windows were last in front is part of the state, and an application may offer a switcher on Ctrl+Tab that flips between the last two windows, walks the order while Ctrl is held with a list of the windows, and leaves docked windows out.
- A notice's and a toast's content stays inside the card: an unbroken word breaks at the edge, a code block scrolls, a long action ends in an ellipsis.
- A disabled action in a menu is faded to half as well as muted. A placeholder is not faded, as chapter 8's fields section already requires, since it would fall below 4.5:1.
- Two glyphs: `image` and `clip`.

## 0.22.0

From an application's second batch of proposals (PUDL's `docs/proposals/menu-bar-keys-and-toolbar.md`).

- **Letters in the menu bar.** Every title and command has a letter, declared or assigned by a rule, which opens the title from the bar and chooses the command in a panel on every platform, replacing type-ahead. A desktop host gains Alt alone and F10 to reach the bar and the platform's access-key modifier with a letter to open a title from anywhere, Ctrl+Option on a Mac. Letters are underlined while they can be typed.
- **A desktop host** may claim `Mod` with N, T and W. A function key works from a field. The bar lists its keys and reports one bound twice.
- **More of a command**: dangerous, a glyph, a detail line, and a reason while disabled, from markup as from an applet; a markup list of one-of-several commands.
- **Toolbars**, a section of their own: groups of raised controls, one tab stop with the arrow keys, latched controls pressed in, and a menu button disabled with its commands.
- **A window's detail**, a second part of its title that gives way before the title.
- **Sixteen glyphs**: `board`, `ticket`, `pencil-off`, `new-window`, and the editing glyphs `bold`, `italic`, `underline`, `strike`, `code`, `list`, `list-numbered`, `quote`, `table`, `panel`, `colour` and `paragraph`.

## 0.21.0

From an application's proposal on the controls its Flow window built for itself.

- **Disclosure cards.** A card that opens and closes by a raised toggle at the start of its head, drawn as a tree's toggle, with a summary shown only while closed and a foot of actions. The open question of whether a whole card may be pressable is settled: it may not.
- **Zoom**, a section of its own: a group of Zoom Out, the scale, Zoom In and Fit above a viewport that scrolls, keeping the middle in place, with Ctrl and the keys while the viewport has focus.
- **Row editors**, a section of its own: a table of fields with flat headings, a remove button at each row's end, an Add button beneath, and a stacked layout at a narrow width measured on the editor.
- A field's label line may end in a command, a small raised control with a name of its own.
- A master-detail list's rows take a tree's keys, and may stand on their own as a row list of links wherever a page lists things to open.
- A window's buttons and glyphs are sized from the title's text, and the window menu's caret stands as tall as the title's letters.
- Four glyphs: `plus`, `minus`, `arrow-up` and `arrow-down`.

## 0.20.1

- The conformance checklist gains the item for room to ask for, which 0.20.0 left out.

## 0.20.0

- **Room to ask for.** A window's content may ask for a width. While it is in front, automatic shared side docks that would leave it less give way to rails, the widest first, without changing the reader's arrangement. A dock the reader pinned open stays open. From the site's issue #16.

## 0.19.1

- **Correction.** 0.19.0 said that a docked window stays docked on a narrow screen that fills the workspace with windows. That reversed the responsive workspace rule, under which a window that takes part gives up its dock there. The rule stands. What is new is that an application may set the policy for all its windows at once, and that a window may keep its own placement, as a strip docked at the bottom does.

## 0.19.0

From the site's issues.

- **Five glyphs**: `reload`, `flag`, `inbox`, `shield` and `terminal`, the last told apart from `script` by a window's title bar above its prompt.
- **Where windows open.** A window's content may put its own placement first, may name the zone the windows it opens go to, and may name the zone it goes to when undocked. The application is told which link opened a window.
- **Open beside.** A link may open its target beside its window instead of in its place, in a zone it names or the other half. An application may let Ctrl or Cmd with a click do the same on a link that would replace its window.
- **Changing a window in place.** A form in a window may be sent without the application loading again, the window taking its new content from the answer, and an application may take a window's content again or give it new content.
- A docked window stays docked on a narrow screen that fills the workspace with windows. (Corrected in 0.19.1.)
- A shared dock's strip may be drawn without script, its tabs links, and without a strip a shared window leaves no empty band.

## 0.18.0

From an application's proposal.

- An application can share its top and bottom docks as well as its sides. Each shares its edge under a full-width tab strip on the side next to the central area, collapses to that strip when the workspace is short, and slides a window out from it.
- The reader can reorder the tabs of a shared dock by dragging them or with Alt, Shift and the arrow keys. Required windows keep the first places, and the order is restored with the arrangement.

## 0.17.0

- Rail buttons match Pin in size, omit dropdown buttons and stay depressed while their slideouts are visible.

- Host menu typography matches other menu titles, and splitters retain a 1px boundary rule at rest.

- Dock labels use compact badge typography. Collapse and Pin stay at the same outer top corner across dock modes, and rails place Pin above the tabs.
- Required windows omit Close from every menu. Empty front menus and separators without a preceding group are omitted.

- Shared side docks retain one width across their tabs. Tab menus replace close buttons, pinned docks omit title bars, and selected tabs connect to their content.
- Applications can keep permanent side panels docked, without window title bars, and omit docked windows from the taskbar.

## 0.16.0

- Shared side docks can show several windows through tabs and collapse to icon rails. Required windows remain available, and each dock restores its selected tab and open or rail preference. Window status marks appear in the tabs, rails and taskbar.

## 0.15.0

- **A `pencil` glyph**, for editing or renaming something in place, so that an icon button for either needs no glyph of its own.

## 0.14.0

- **Layout**, a section of its own: a stack, a row that wraps and may align its components or push its last to the end, and a grid of as many equal columns as fit at a least width. Each places its components in document order, with a gap from the spacing grid, never overlapping them, never at fixed positions and never making its space wider. It is the grammar's layout category, with no surface and nothing exposed. a development tool's canvas arranges components with these, and every application needed them.

## 0.13.0

From example.com's proposals, for it and the reader application.

- **The sidebar's side.** An application may put a master-detail sidebar at the end edge of the reading direction, mirrored as in a right-to-left layout, keeping its order for the keyboard and its width and collapsed state.
- **Collapsing, and a peek.** The section now says that a reader may collapse the sidebar to its handle, and that an application may let the reader peek at a collapsed sidebar by resting the pointer on its handle or focusing it: the sidebar is drawn over the detail pane without moving it, and closes when the pointer or focus leaves, never changing the collapsed state or the width.

## 0.12.0

From the reader application's proposal, for patterns it and example.com each built for themselves.

- **A filter menu**: checkbox rows in a menu that apply a filter at once, the panel staying open, or opening again with focus on the same box where the filter reloads what holds it.
- **A settings panel**: a column of cards, each a group of settings with its actions in a row at its foot.
- **A disclosure button**: a plain button that shows or hides content in place, with the new `chevron` glyph pointing down or up.
- **A window's default front menu**: a window whose content offers no menu has one title, the window's, with what every window offers.

## 0.11.0

- **The status area matches a menu bar's menus**, from the reader application's proposal. Where the application bar has a menu bar, the status area looks exactly like its menus, in surface, height and its items' colours and states, which are the titles'; only on a bar without a menu bar does it take the bar's own chip colours. It is 30px tall, as a menu is, with items 26px tall.
- A new glyph, `account`, for an account with no picture, drawn at a picture's size.

## 0.10.0

- **An article's Print is the application's to offer**, from example.com's proposal. An article's first title offers printing only where the application says the article's printed form is worth having, since printing a page of windows prints the windows and the frame around them, and an article has no File title unless the application gives it one.

## 0.9.0

- **A status area in the application bar**, from example.com's proposal. The last thing in the bar's chrome may be one raised group of flat items, each a glyph or a picture with an optional badge, for what runs in the background of the application, with the reader's account last. A badge with nothing to say is not shown, and an item's accessible name says what its badge means. A round picture needs no raised ring of its own, since the group is what is raised.
- **The window menu docks at every edge**, from example.com's proposal. Its Dock at the bottom becomes a Dock list of Top, Bottom, Left and Right, ticking the edge the window is docked at, with Undock at its end on a docked window.
- A new glyph, `comments`.

## 0.8.0

- **A select's opener is PUDL's.** A closed select's opener is the `caret` glyph, drawn by the implementation in the select's text colour, and a platform's own drawing of a select is not used. This settles a question the section on fields had left open. The web implementation found that WebKit draws a select raised and lit, which broke the rule that a field is sunken.

## 0.7.0

- **A pins group in the menu bar**, from example.com's proposal. Between the host menu and the front menu, an application may give the reader a group of the applets and articles they go to most: the `pin` glyph and a Pins title of pinning commands, then a link for each pinned item, with its icon and title. When the pins do not fit they give way together to an Items title, before the bar becomes one button, and the collapsed bar lists the Pins commands and then the pins. With nothing pinned the group keeps its Pins title.
- A new glyph, `pin`.

## 0.6.0

- **Menu bars**, from example.com's proposal. An application's menu bar stands in its application bar, holding the host's menu and the menu of whatever is in front, an applet or an article. Each menu is one raised surface with flat titles; a front menu may add to the host's titles but never take or change one. The bar is one tab stop and follows the WAI-ARIA menu bar pattern; it becomes one menu button when it does not fit. Shortcuts use `Mod` for the platform's command key and keep off the keys browsers and fields need. With a menu bar, an applet's commands live there and the window menu keeps the window's own.
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

- **Windows sized by their content.** A window is sized either by the reader or by its content, as a desktop window has a sizing border or is a dialog that sizes itself. A window sized by its content takes its content's size and follows it as it changes, larger and smaller, from a fixed top-left corner, stops at the edge of the workspace where its body scrolls, and cannot be resized, maximised, snapped or docked. An applet in it flows. From example.com's proposal on window sizing.
- **Limits on windows the reader sizes.** A window MAY carry a smallest and a largest size, which dragging, the keyboard and restoring an arrangement all respect.

## 0.2.1

- **Segmented controls return to a raised thumb.** 0.2.0 drew the chosen segment pressed in beside raised ones, and with two choices the state was hard to read. A segmented control is now defined as a switch with more than two positions, as macOS and iOS draw it: the trough is the track, the chosen segment is the raised thumb, and the other positions lie flat on the track. Chapter 2 states the rule for switches and segmented controls together.

## 0.2.0

Every chapter and every component section is drafted, and the grammar is settled where drafting them found it unclear. the maintainer made these decisions on 2026-10-01.

- **Where the reader is.** In a set of raised controls, the one for where the reader is, or the one chosen, is drawn pressed in and exposed as current or chosen. Tabs are the exception: the current tab stands flat, taller, open into the content below.
- **Segmented controls.** The chosen segment is pressed in and the others stand raised.
- **Lists of places and choices** are a category of their own, drawn flat: sidebar rows, tree nodes, menu rows and rows to choose from. They respond under the pointer and mark the current row by more than colour. Links in running text are underlined, and tabs and these rows are not.
- **Handles**, the things a reader drags, are flat and carry the new `grip` glyph at rest.
- **Every raised control** is pressed in while pressed, and dims to 45% when disabled.
- **Tokens.** New: `input-border`, which reaches 3:1 against every surface in both themes for the bounds of fields and switch tracks; `shadow-dialog` and `backdrop`; `radius-xs`, 4px, for small parts inside another control.
- **Glyphs.** New: `grip` and `theme`.
- **Chapter 2** names the badge shapes correctly: a warning badge carries a triangle and an error badge a square.

## 0.1.0

The specification separated from the web implementation, as `docs/proposals/spec-and-implementations.md` in paulmooreparks/pudl proposed and the maintainer decided on 2026-09-30.

- The introduction, the grammar, the tokens chapter and the button are written. The other chapters are outlines that list the questions each must settle.
- The palette and the scales are in the Design Tokens Community Group format, 2025.10. The derived tokens are formulas in `derived.json`, which chapter 3 defines.
- The 36 glyphs are SVG files on a 16-unit grid.
- Every value is the one the web implementation's 0.33.0 used, so its generated token block computes exactly as its hand-written one did.
