# 2. The grammar

The grammar is the small set of rules a reader learns once and then applies to every application built with PUDL. Everything else in this specification follows from it. An implementation MUST keep every rule in this chapter, and an application built with a conforming implementation keeps them by using its components as they are specified.

## Elevation says what a thing does

Every surface a reader sees has one of three elevations, and the elevation says what the reader can do with it.

- **Raised** means the thing can be pressed. A raised surface stands above what is behind it: it is lit along its top edge, it shades toward its foot, a hairline border bounds it, and it casts a small shadow. Buttons, tabs the reader can go to, a switch's thumb, the zones of a layout picker and the title bar's buttons are raised.
- **Sunken** means the thing takes input. A sunken surface sits below what is around it, with a shadow falling inside its top edge. Text fields, selects, text areas and a switch's track are sunken.
- **Flat** means the thing is there to be read. Text, tables of values, badges and a read-only field are flat.

The three elevations MUST stay distinct from one another in every theme and in every state, so that a reader can tell them apart at a glance. A raised control that is pressed, or latched on, is drawn pressed in: it keeps its bounds and loses its light, and the shadow moves inside it. It does not become flat, because it can still be pressed again.

Nothing is raised that cannot be pressed, and nothing sunken that cannot take input. A disabled control keeps its elevation and is dimmed, so the reader learns that it exists and what it would do.

### Where the reader is

Where a set of raised controls offers places or choices, such as the pages of a list, the pages of an application bar or the windows in a dock, the one for where the reader is, or the one chosen, is drawn pressed in, like a latched toggle, and exposed as current or chosen. A segmented control follows the same rule: the chosen segment is pressed in and the others stand raised, ready to be pressed.

A tab is the one exception, whether it is a section tab, the tab of a panel within a page or the tab of an open document. The tab for where the reader is stands flat and a little taller, open at its foot into the content below it, because it is the edge of that content rather than a control beside it. The other tabs stand raised.

### Lists of places and choices

A list of places or choices is a category of its own, drawn flat. Its rows are the rows of a sidebar list, the nodes of a tree, the rows of a menu and the rows of a table the reader chooses from. A row can be pressed, and it says so in three ways: it sits in a list whose form says it holds places or choices, it responds under the pointer, and the current or chosen row is marked by its weight, its edge or its fill as well as its colour. Each row is flat because a list of fifty raised buttons would bury what they name.

### Handles

Something the reader drags, such as the handle between two panes, the divider beside a sidebar or the edge of a window, is a handle. A handle that stands on its own is flat, and carries the `grip` glyph so that it can be found without a pointer resting on it. A window's title bar is raised, because besides being dragged it holds buttons and answers a double press.

## Categories stay separate

Buttons, links, tabs, lists of places, status badges, chips and filter chips each have an appearance of their own, and none of them borrows another's. A link that looks like a button, or a badge that looks like a chip, teaches the reader something false about what it does.

A link in running text is underlined, so it can be told from the text around it without relying on colour. Tabs, and the rows of a list of places, are not underlined, since their form already says what they are. The application's name in its title bar is not underlined either, because its position already says what it is.

## Colour is never the only signal

Every state that means something carries a second signal besides its colour: a glyph, a position, an elevation or words. Each status has a shape of its own, which chapter 5 lists, so a warning badge carries a triangle and an error badge a square. A selected row is marked by its position and edge, and a toggle that is on by its elevation. An application MUST still read correctly for a reader who cannot tell red from green, and for one who sees no colour at all.

## State is exposed as well as shown

A state is exposed to assistive technology in the same terms the eye receives it. When a component shows that it is the current place, that it is pressed or checked, or that it is selected, it MUST also expose that state through the platform's accessibility interface. The visual treatment SHOULD follow from the exposed state, so that the two come from one source and cannot drift apart.

Chapter 6 lists the states and how each maps to the accessibility interfaces of the common platforms.

## One primary action

A visible context has at most one primary action, drawn in the accent. A dialog, a form or a toolbar that seems to need two has a secondary or a destructive action hiding in one of them.

## Numbers that are data line up

Where numbers are data, as identifiers, counts, money and times are, their figures are tabular, so the digits line up down a column and a changing value does not shift the text around it. Numbers in running prose keep the face's proportional figures.

## Glyphs are drawn

Every glyph in PUDL's own chrome is drawn from the shapes in chapter 5, filled with the colour of the text around it. None is a character from a font, because a character can fall back to another face, or become a colour emoji, and then no longer mean what it did.

## The reader can return

What the reader has arranged, such as the windows they have open, the record they are viewing or a filter in force, is part of the state they can come back to and hand to somebody else. Chapter 7 says what must be restorable. How a platform restores it is the platform's business.
