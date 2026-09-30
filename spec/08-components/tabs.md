# Tabs

A tab names one of several things that share a space, and pressing it brings that thing into the space. PUDL has three kinds of tab. Section tabs go to the sections of an application, tabs within a page switch between panels of one thing in place, and document tabs switch between the documents a reader has open. To the reader all three are tabs, so they are drawn alike, and they differ in what pressing one does and in how the keyboard moves among them.

## Anatomy

Tabs stand in a row on a tab bar. The bar is a recessed band, filled with `recess-bg`, shaded from above with `recess-shadow`, and ruled along its foot with a 1px line in `border`. It has 10px of padding above its tabs, 16px (`space-4`) at either end and none below, so the tabs stand on its foot. The tabs are 4px (`space-1`) apart. When they outrun the bar's width the bar scrolls sideways, and it never widens the view.

A tab the reader can press is raised. It is filled with `raise-grad` and bounded on its top and sides by a 1px hairline in `raise-border`, with no line at its foot, where it stands on the bar. Its top corners are `radius-sm` and its foot is square. It is lit along its top edge by a 1px line of `light` at the strength `lit` sets, and casts no shadow outside itself, because it rises from the band rather than floating over it. Its label is set in the interface face at `text-sm` and weight 600, in `text`, on one line, with 5px of padding above, 14px either side and 4px below.

The tab for where the reader is, the current section or the chosen panel or document, is the exception chapter 2 makes to drawing where the reader is as pressed in. It stands flat, because it is the edge of the content below rather than a control beside it. It has no light, a 1px border in `border`, and is filled with `section-current-bg`, which is the colour of the content below the bar, so the content visibly hangs from it. It stands 4px taller than the other tabs, with 7px of padding above and 6px below, and it is open at its foot into the content. The bar keeps the same height whether or not one of its tabs is current, so the content below does not move when a tab becomes current.

## Kinds

### Section tabs

Section tabs go to the sections of an application, each of which has an address of its own, so each section tab is a link. The current tab is the section the reader is in. On the section's own page it is the current page, and on a page inside the section, such as one article among many, it is still marked current, so every page shows which section it belongs to.

`section-current-bg` is `surface` by default, the colour of a master-detail toolbar. An application whose content sits directly on `bg` sets the current tab's fill to `bg`, so the tab still opens into what lies beneath it.

### Tabs within a page

Tabs within a page switch between panels of one thing, such as the details, the receipt and the history of one expense, without going anywhere. One panel shows at a time, below the bar. The panel is filled with `surface`, which is also the chosen tab's fill here, bounded by a 1px line in `border` on its sides and foot and open at its top into the chosen tab, and it has 16px (`space-4`) of padding.

Which panel is chosen is part of the reader's restorable state, as chapter 7 describes. Returning to the view, or opening a link to one of its panels, shows that panel. Choosing a panel SHOULD NOT count as a step for the platform's Back action, where the platform has one, so that switching panels does not fill the reader's history.

### Document tabs

Document tabs come and go, one for each document, record or view the reader has open, as in an editor. Which document is open belongs to the application, so pressing a tab asks the application to show its document, and the application decides what happens when a tab closes. A document tab is drawn as every other tab is.

A document tab holds its document's name and MAY hold two things after it, 6px apart. An unsaved mark is the circle glyph at 10px in `accent`, and it carries words for assistive technology, such as "unsaved", that the eye does not see. A close button is a small raised button 18px across, fully rounded, filled with `raise-grad`, bounded by `raise-border` and shadowed with `raise-shadow`, holding the close glyph at 9px in `text-muted`. A tab with a close button has 6px of padding at its end instead of 14px, so the button sits close to the tab's edge.

## States

| Part | State | Appearance |
|---|---|---|
| Tab | At rest | Raised, as above |
| Tab | Under the pointer | The fill becomes `raise-grad-hover` and the border `raise-border-hover` |
| Tab | Pressed, while the pointer or key is down | Pressed in: the fill becomes `raise-active-bg` and the shadow `raise-active-shadow` |
| Tab | Focused from the keyboard | A 3px ring in `focus-ring` outside its bounds, in addition to its other state |
| Tab | Current, or chosen | Flat, 4px taller, filled with `section-current-bg` and open into the content below |
| Document tab | Its document has unsaved changes | The unsaved mark shows after its name |
| Close button | Under the pointer | Its fill becomes `raise-grad-hover`, its border `raise-border-hover` and its glyph `danger` |
| Close button | Pressed, while the pointer or key is down | Pressed in: the fill becomes `raise-active-bg` and the shadow `raise-active-shadow` |

A focused tab that is also current keeps its focus ring. The current tab is marked by its elevation, its height and its opening into the content, so it never rests on colour.

## Interaction

### Section tabs

Each section tab is a link and a stop of its own in the tab order. Pressing it, with the pointer or the platform's usual key, goes to its section.

### Tabs within a page

The tab list is one stop in the tab order, on the chosen tab. Once it has focus, these keys choose among the tabs, and choosing a tab shows its panel at once.

- Right and Left choose the next and the previous tab, wrapping around from the last to the first and from the first to the last.
- Home and End choose the first and the last tab.

Right and Left are mirrored in a right-to-left layout. Pressing a tab with the pointer chooses it.

The chosen panel is itself the next stop in the tab order after the tab list, so a reader can reach and scroll a panel that holds nothing focusable.

### Document tabs

The tab list is one stop in the tab order, on the selected tab. Once it has focus, Right and Left move focus to the next and the previous tab, wrapping around, and Home and End move it to the first and the last. Moving focus does not choose a tab. Enter or Space chooses the focused tab, as a pointer press on it does. When focus leaves the list, its stop returns to the selected tab, so the reader who tabs back in lands on the document in view.

Pressing a tab's close button, or pressing Delete while the tab has focus, asks the application to close the tab, and does not choose the tab. The application MAY refuse or delay the close, for example to ask about unsaved changes in a dialog first, and removes the tab itself when it agrees.

## Accessibility

Section tabs are exposed as links inside a navigation region with an accessible name, such as "Sections". The current tab is exposed as the current page on the section's own page, and as current, without naming a page, on a page inside the section.

Tabs within a page are exposed with the tab list role and an accessible name, each tab with the tab role, and each panel with the tab panel role, named by its tab. The chosen tab is exposed as selected, and the others as not selected.

Document tabs are exposed in the same roles as tabs within a page, and the selected tab as selected. A tab's unsaved mark is exposed as part of its name, so a tab reads, for example, as "today.md unsaved". A tab's close button is not exposed, since a tab list may hold only tabs, and the keyboard reaches the same action through Delete.

In the platform's high-contrast mode, every tab and panel keeps a visible border, the current or chosen tab takes the system's highlight colours, and the unsaved mark and the close button's glyph are drawn in the system's text colours.

## Questions this section must settle

- Whether the three kinds should share one keyboard model. Section tabs are each a stop in the tab order, tabs within a page choose as focus moves, and document tabs move focus first and choose on Enter or Space. Each has a reason, and the language has not yet said whether those reasons are rules.
- What a tab bar does when its tabs outrun its width. Today it scrolls sideways, which leaves the reader no way to see which tabs are hidden, and document tabs in particular may need a menu of every open tab.
- Which tab becomes selected when the selected document tab closes, and whether the language or the application decides.
- How a reader who uses assistive technology learns that Delete closes a document tab, given that the close button is not exposed.
- Whether a tab may be disabled, and how a disabled tab is drawn.

## Conformance checklist

1. A tab bar is recessed, and its tabs stand on its foot, raised, with square feet and `radius-sm` top corners.
2. The current or chosen tab, of every kind, is flat, 4px taller than the others, and open at its foot into the content below.
3. The tab bar keeps the same height whether or not one of its tabs is current.
4. A tab's label is `text-sm` at weight 600, on one line.
5. A tab is drawn pressed in while it is pressed, and so is a document tab's close button.
6. When the tabs outrun the bar, the bar scrolls sideways and the view does not widen.
7. A section tab is a link, and the current one is exposed as the current page on the section's own page and as current on a page inside it.
8. Tabs within a page are one stop in the tab order, on the chosen tab, and Right, Left, Home and End choose a tab and show its panel at once, with Right and Left wrapping and mirrored in a right-to-left layout.
9. The chosen panel of tabs within a page is restored when the reader returns to the view, and a link can name it.
10. Document tabs are one stop in the tab order, on the selected tab; Right, Left, Home and End move focus without choosing, and Enter or Space chooses.
11. Pressing a document tab's close button, or Delete on a focused document tab, asks the application to close it, and neither chooses the tab.
12. A document tab's unsaved mark is a drawn glyph whose words are part of the tab's accessible name.
13. Tabs within a page and document tabs are exposed as a tab list of tabs, with the chosen one exposed as selected.
14. Focus from the keyboard shows a ring at least 3:1 against its surroundings, on the current tab as on the others.
15. In high-contrast mode every tab keeps a border and the current or chosen tab stays distinguishable.
