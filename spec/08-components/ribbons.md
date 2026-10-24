# Ribbons

A ribbon holds a long set of tools, such as an editor's, as several folding toolbars of which one shows at a time, each under a tab. It suits an application with more tools than one row can show in a useful way. An application whose commands live mostly in menus uses a command bar instead, as the section on toolbars sets out. A ribbon is an application's choice; nothing becomes a ribbon by itself.

## Anatomy

A ribbon is a tab bar along its top, drawn as tabs within a page are, and under it the folding toolbar of the chosen tab, one row tall, filled with `section-current-bg` so the chosen tab opens into it. Each tab's toolbar folds on its own as the section on toolbars sets out, so a long tab of tools still keeps to one row.

**Show as ribbon** stands at the end of the tab bar. It is a toggle button with the `ribbon` glyph and those words, latched on while the ribbon shows. Releasing it **folds the ribbon into a menu bar**: the tab bar and the row are replaced by a menu bar, drawn as the section on menu bars sets out, with a title for each tab, and Show as ribbon stands, released, at the end of that bar. Each title's menu holds the tab's groups in order, each under a heading with the group's name, separated from the next by a rule, in the rows a fold menu holds. Pressing Show as ribbon again brings the tabs and the row back. The tab bar and the menu bar are one height, 44px, and Show as ribbon stands in the same place on both, so folding the ribbon takes away only the row and nothing on the bar moves.

A tab is never left standing without its row, since tabs over nothing read as tabs for the page beneath them.

An application's own menu bar MAY unfold into a ribbon the other way round, its titles becoming tabs and each menu's rows a row of tools, as the section on menu bars sets out. That ribbon is the application's, under its application bar, where this section's ribbon belongs to one part of the page, such as an editor.

## States

The chosen tab is momentary, as an open menu is, so it is not part of the page's address. Whether the ribbon shows or is folded into menus is the reader's preference, and an implementation SHOULD remember it for the application.

## Interaction

Every ribbon tab exposes its full title on hover and on keyboard focus, including when its words have folded away. A labeled **Ribbon tabs** menu offers the available tabs by their full titles and marks the current tab. It is a separate stop in the tab order and opens with Enter, Space or Down Arrow. Choosing a title selects that tab; Escape returns focus to the chooser. The chooser is available to touch users without a long-press gesture.

The tab bar is one stop in the tab order, and the arrow keys, Home and End move among its tabs and choose them, as among tabs within a page. In a standalone ribbon, Tab moves from the tab bar to Ribbon tabs, then Show as ribbon and then into the chosen row, which is a toolbar with the keys the section on toolbars sets out. In an application's unfolded menu bar, the chooser stands beside the chosen row. When the ribbon is folded into menus, its menu bar has the keys of a command bar's menus.

## Accessibility

The tab bar is exposed as a tab list holding only its tabs, each tab controlling its row, and the row is a toolbar named for its tab. Show as ribbon stands beside the tab list rather than in it, and is exposed as a toggle button with its pressed state. Ribbon tabs is a menu button outside the tab list, and its entries expose their selected state. Folded into menus, the menu bar's titles are menu buttons and their menus are menus.

## Conformance checklist

1. A ribbon is a tab bar with the chosen tab's folding toolbar under it, one row tall, the chosen tab open into it.
2. Show as ribbon stands at the end of the tab bar with the `ribbon` glyph, latched while the ribbon shows.
3. Releasing it replaces the tabs and the row with a menu bar of the same names, each menu holding its tab's groups under headings in fold-menu rows, with Show as ribbon released at its end; pressing it brings the ribbon back.
4. No tab stands without its row, and the tab bar and the folded menu bar are one height, with Show as ribbon in the same place on both.
5. The chosen tab is not in the address; whether the ribbon is folded is remembered.
6. The tabs, the row, the toggle and the folded menu bar have the keys and roles this section sets out.
7. Full-title tips remain available after folding, and the labeled Ribbon tabs chooser supports keyboard and touch selection with the current tab identified.
