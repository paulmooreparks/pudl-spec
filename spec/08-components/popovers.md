# Popovers

A popover is a panel of any content anchored to the control that opened it, such as a small form that sets a filter, a help text, or the details of an item. It is not a menu, whose rows are places and actions, and it is not a dialog, which is modal: the rest of the view stays usable while a popover is open, and a press outside it closes it.

## Anatomy

A popover is drawn as a menu's panel is: filled with `dialog-bg`, bounded by a 1px line in `border`, with `radius` corners and the panel's shadow, lifted above every other surface with no backdrop. It has 16px (`space-4`) of padding, is at least 16rem wide and at most 24rem or the window's width less 16px, and scrolls when its content is taller than the room it has.

It MAY have a head: a band across its top holding a title, set at `text-sm` and weight 700, and a close key at the end, a glyph button with the `close` glyph, separated from the content by a 1px line in `border`. It MAY have actions, a row of buttons at its foot, at the end, as a dialog's are. The head and the actions stay in view while the content between them scrolls, as a dialog's do.

A popover MAY have a pointer: a small square turned to a point, in the panel's fill and border, on the edge that faces its control and aimed at the control's middle, for controls that sit close together, where the reader could otherwise not tell which control the popover belongs to. A popover with a pointer stands 7px further from its control than one without.

## Placement

A popover opens against its control as a menu's panel does: below it, or above it on the terms the section on menus sets out, lined up with the control's start edge and kept 8px from the window's edges. On a narrow window it opens as a sheet across the full width, without its pointer.

## Interaction

The control that opens a popover is a button. Pressing it opens or closes the popover. Opening moves focus into the popover: to an element marked to take focus, or to its first field, or to its first control other than the close key. Escape, a press outside the popover, and the close key each close it, and focus returns to the control that opened it. A popover never closes because the pointer leaves it.

## Accessibility

A popover is exposed as a non-modal dialog, named by its title where it has a head, or by an accessible name otherwise. The control that opens it is exposed as controlling it, and as expanded while it is open.

In the platform's high-contrast mode the panel keeps a visible border.

## Conformance checklist

1. A popover is drawn as a menu's panel, with 16px padding, and is lifted above every surface with no backdrop.
2. It opens against its control as a menu's panel does, below or above, lined up with the control's start edge, inside the window, and as a sheet on a narrow window.
3. Opening moves focus into it, to its first field or first control other than its close key.
4. Escape, a press outside and its close key close it, and focus returns to its control.
5. A head and actions stay in view while the content between them scrolls.
6. A pointer, where there is one, is on the edge facing the control and aimed at its middle.
7. It is exposed as a non-modal dialog with a name, and its control as expanded while it is open.
