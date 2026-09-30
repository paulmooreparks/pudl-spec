# 7. Restorable state

A reader who arranges an application to do their work has made something, and PUDL treats it as theirs. When they leave and come back, the application MUST be as they left it, and on a platform where a place can be handed to somebody else, such as by a link, the person they hand it to MUST see the same thing. This chapter says what that state is. How a platform keeps it is the platform's business: the web implementation keeps all of it in the page's address, and a desktop implementation might keep it in a session file, or in a link its application knows how to open.

## What must be restorable

- The record, document or place in view.
- A filter, search or sort in force on a list.
- The tab chosen among tabs within a page or among section tabs.
- The windows that are open, the order they were opened in, which is in front and which are minimised.
- Each window's placement (floating with its position and size, maximised, snapped to a zone, or docked at an edge with the size of its strip), and for a window that is not floating, the floating position and size it returns to.
- An applet's state, where its host chooses to keep it, as chapter 9 sets out.

State that belongs to the application rather than to what the reader is doing, such as the width they dragged a sidebar to, MAY be kept per reader instead, since it is a preference about the application and not part of any one piece of work.

## Fractions and sizes

Positions and sizes are kept as fractions of the space they sit in, so that a restored arrangement fits the space it is restored into, whether that is another window size, another screen or somebody else's machine. A window that would fall outside its space on restoring is brought back inside it, and keeps its size.

## Defaults

An application MAY open some windows by default, as standing furniture. An entry into the application that names no arrangement opens the defaults; an entry that names one, even an empty one, opens what it names and nothing else, so the reader who closed every window can come back to none.

## History

On a platform with a history of places, such as a browser, opening a window is a step the reader can go back from. Moving, resizing or minimising one replaces the current step, so that going back undoes the opening and does not replay every drag.

## Questions this chapter must settle

- Whether restorable state must be shareable on every platform, as it is on the web, or only restorable for the reader who made it.
- How a restored arrangement names a window whose content no longer exists, such as a deleted record.
