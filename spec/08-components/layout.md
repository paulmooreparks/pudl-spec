# Layout

Layout arranges components in a page, a pane or a window: a column of them, a row of them, or a grid. Master-detail layouts, splitters, tabs and windows divide an application's space; layout is what arranges the components inside one of those spaces, such as the fields of a form or the cards of a settings panel. It has no surface of its own, so it is the grammar's layout category: nothing about it is raised, sunken or flat, and nothing in it can be pressed. Every application needs it, and an application that writes its own arranges the same things differently from the next, so PUDL has three.

## Anatomy

- A **stack** places its components one above another, in reading order, each as wide as the stack unless it says otherwise.
- A **row** places its components side by side in reading order, and wraps them onto further lines when there is not room for them on one, so it never makes its space wider. Its components keep their own widths. A row MAY align its components along their starts, centres, ends or first lines of text, the last being the way to line up fields of different heights by their labels, and MAY push its last component to the end, as a toolbar's commands are pushed away from its title.
- A **grid** places its components in equal columns, as many as fit at a least width, 224px unless the application says otherwise, and starts a new line when a line is full. On a space narrower than the least width it is one column, a stack. Each component takes one cell, or MAY span every column of its line.

The gap between a layout's components is one step of the spacing grid, `space-3` unless the application chooses another, from `space-1` to `space-6`, or none. The same gap separates lines of a row or a grid. A layout adds nothing around its components: the space around it belongs to whatever holds it.

Layouts nest: a stack of rows, a grid of stacks, a row inside a card inside a grid.

## Rules

The order of a layout's components on the screen MUST be their order in the document, which is the order the keyboard and assistive technology meet them. A layout never moves a component out of its order to fit, and never overlaps components or places them at fixed positions; a component that needs to stand over others is a dialog, a menu or a window.

A layout MUST fit its space without making it wider, at any width down to 320px: a row wraps, a grid drops to fewer columns, and a component wider than its space, such as a wide table, scrolls inside itself rather than widening the layout.

## States

A layout has no states of its own.

## Accessibility

A layout is not exposed: assistive technology meets its components as if the layout were not there, in their order. A group of related controls inside a layout is exposed as a group by its own means, such as a fieldset, not by the layout.

## Questions this section must settle

- Whether a grid's components may span more than one column but not all of them.
- Whether a row may hold back its wrapping until a width the application names, so that a pair of fields stays side by side on a tablet.

## Conformance checklist

1. A stack, a row and a grid place their components in document order, with a gap from the spacing grid and nothing around them.
2. A row wraps rather than widening its space, and may align its components along their starts, centres, ends or first lines of text, or push its last component to the end.
3. A grid fits as many columns as its least width allows, 224px unless the application says otherwise, and is one column below it.
4. No layout overlaps its components, places them at fixed positions or changes their order.
5. At 320px wide no layout makes the page wider.
6. A layout is not exposed to assistive technology.
