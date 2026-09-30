# Tooltips

A tooltip is a short label that appears beside a control while the pointer rests on it or while it has keyboard focus. Its main use is naming a control that shows only a glyph, such as a glyph button, a window's buttons or the button that dismisses a notice, so that a sighted reader can learn what the glyph means without pressing it. A tooltip names a control or describes it in a few words. Anything the reader needs in order to use the application belongs in the view itself, where it shows without hovering.

## Anatomy

A tooltip is a small flat label, drawn in the reverse of the page's colours so that it stands apart from whatever it covers. It is filled with `text`, and its words are set in `bg`, in the interface face at `text-xs` and weight 600, with a line height of 1.4. It has 4px of padding above and below and 8px either side, corners of `radius-xs`, and no border. It casts a soft shadow of `shade`, 4px below it and blurred over 12px, at 1.4 times the strength `depth` sets. It grows no wider than 288px, and longer words wrap onto further lines.

The tooltip sits centred above its control, 6px from it. When there is no room above, it sits 6px below instead. It keeps 8px from the left and right edges of the window, shifting sideways as far as it must.

A control that shows only a glyph SHOULD have a tooltip, as the buttons section says, and the tooltip's text is then the control's accessible name. The glyph-only controls an implementation draws itself, such as a window's buttons and the button that dismisses a notice, MUST have one. Any other control MAY have a tooltip that names it or describes it briefly. A tooltip holds text only, and nothing in it can be pressed or focused.

## States

| State | Appearance |
|---|---|
| Hidden | Nothing is drawn |
| Shown | The tooltip is drawn beside its control, as above |

## Interaction

A tooltip appears when the pointer has rested on its control for 450ms. While one tooltip is showing, moving the pointer onto another control that has one shows the new tooltip at once, without the wait. A tooltip appears at once when its control receives focus from the keyboard, and does not appear when focus arrives from a pointer press.

The tooltip stays while the pointer is over its control or over the tooltip itself, so the reader can move the pointer onto it to read it or to magnify it. When the pointer leaves both, the tooltip hides 150ms later, and returning within that time keeps it. The tooltip also hides when its control loses focus, when the reader presses anywhere with the pointer, and when the view scrolls.

Escape hides a tooltip that is showing. That press of Escape hides only the tooltip, so a reader dismissing a tooltip inside a menu or a dialog does not also close the menu or the dialog.

Only one tooltip shows at a time. A control MUST NOT show a second tooltip beside PUDL's, such as one the platform draws for the same control.

A tooltip is momentary, and it is not part of the reader's restorable state.

## Accessibility

A tooltip is exposed with the tooltip role. When its text is the same as its control's accessible name, the control's name already says it, and nothing more is exposed. When its text differs, the control is exposed as described by the tooltip, so assistive technology reads the tooltip's words after the control's name.

A tooltip that hides after the pointer leaves, and stays while the pointer is on it, meets the requirements of WCAG 2.2 success criterion 1.4.13 for content shown on hover or focus: it can be dismissed without moving the pointer or focus, it can be hovered, and it persists until the reader dismisses it or moves away.

In the platform's high-contrast mode a tooltip gains a visible border, since its reversed colours are replaced by the system's.

## Questions this section must settle

- What takes the place of a tooltip on a device with no pointer that can rest, such as a touch screen. The web implementation shows nothing there, so a reader on a phone cannot learn a glyph's meaning without pressing it. A long press is one candidate, and chapter 6 asks the same question for every affordance that relies on hover.
- Whether the delays, 450ms to appear and 150ms to hide, are part of the language, or defaults a platform replaces with its own system setting for hover time.
- Whether a disabled control shows its tooltip, and whether that tooltip may say why the control is disabled, given that the buttons section asks for the reason to be given nearby.
## Conformance checklist

1. Every glyph-only control the implementation draws itself has a tooltip whose text is its accessible name.
2. A tooltip appears after the pointer rests on its control, and at once when the control receives focus from the keyboard.
3. A tooltip stays while the pointer moves from its control onto the tooltip.
4. Escape hides a showing tooltip, and the same press closes no menu or dialog around it.
5. A tooltip hides when its control loses focus, on a pointer press, and when the view scrolls.
6. A tooltip sits above its control, or below when there is no room above, and stays inside the window.
7. Only one tooltip shows at a time, and no platform tooltip shows beside it.
8. A tooltip is exposed with the tooltip role, and a tooltip whose text differs from its control's name is exposed as the control's description.
9. A tooltip's words reach 4.5:1 against its fill, in both themes.
10. A tooltip holds nothing that can be pressed or focused.
11. A tooltip's corners are `radius-xs`.
