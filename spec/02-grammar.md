# 2. The grammar

The grammar is the small set of rules a reader learns once and then applies to every application built with PUDL. Everything else in this specification follows from it. An implementation MUST keep every rule in this chapter, and an application built with a conforming implementation keeps them by using its components as they are specified.

## Elevation says what a thing does

Every surface a reader sees has one of three elevations, and the elevation says what the reader can do with it.

- **Raised** means the thing can be pressed. A raised surface stands above what is behind it: it is lit along its top edge, it shades toward its foot, a hairline border bounds it, and it casts a small shadow. Buttons, tabs the reader can go to, a switch's thumb, the zones of a layout picker and the title bar's buttons are raised.
- **Sunken** means the thing takes input. A sunken surface sits below what is around it, with a shadow falling inside its top edge. Text fields, selects, text areas and a switch's track are sunken.
- **Flat** means the thing is there to be read. Text, tables of values, badges, a read-only field and the tab for where the reader already is are flat.

The three elevations MUST stay distinct from one another in every theme and in every state, so that a reader can tell them apart at a glance. A raised control that is pressed, or latched on, is drawn pressed in: it keeps its bounds and loses its light, and the shadow moves inside it. It does not become flat, because it can still be pressed again.

Nothing is raised that cannot be pressed, and nothing sunken that cannot take input. A disabled control keeps its elevation and is dimmed, so the reader learns that it exists and what it would do.

## Categories stay separate

Buttons, links, tabs, status badges, chips and filter chips each have an appearance of their own, and none of them borrows another's. A link that looks like a button, or a badge that looks like a chip, teaches the reader something false about what it does.

Links are underlined, so they can be told from the text around them without relying on colour. The application's name in its title bar is the one exception, because its position already says what it is.

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
