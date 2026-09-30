# 6. Accessibility

An application built with PUDL is usable by a reader who cannot see it, a reader who cannot use a pointer, a reader who cannot tell colours apart, and a reader who has asked their system for high contrast or for less motion. The requirements in this chapter apply to every component, and each component's section adds its own. They are set to meet the Web Content Accessibility Guidelines 2.2 at level AA, which the platforms' own guidance broadly follows.

## Roles and states

Every component is exposed to the platform's accessibility interface with a role that says what it is, a name that says which one it is, and the states chapter 2 requires it to expose. The table maps each state to the four common interfaces. An implementation for another platform maps them to that platform's equivalents.

| State | ARIA (web) | UI Automation (Windows) | NSAccessibility (macOS) | AT-SPI (Linux) |
|---|---|---|---|---|
| Pressed, for a toggle button | `aria-pressed` | `Toggle.ToggleState` | `AXValue` of a toggle | `STATE_PRESSED` |
| Checked | `aria-checked` | `Toggle.ToggleState` | `AXValue` | `STATE_CHECKED` |
| Selected | `aria-selected` | `SelectionItem.IsSelected` | `AXSelected` | `STATE_SELECTED` |
| Expanded or collapsed | `aria-expanded` | `ExpandCollapse.ExpandCollapseState` | `AXExpanded` | `STATE_EXPANDED` |
| Disabled | `disabled`, or `aria-disabled` | `IsEnabled` false | `AXEnabled` false | `STATE_SENSITIVE` absent |
| The current place | `aria-current` | To be settled | To be settled | To be settled |
| Busy, while a region loads | `aria-busy` | To be settled | To be settled | `STATE_BUSY` |

The desktop columns are this specification's reading of each platform's documentation. The web's current and busy states have no plain counterpart in some of the desktop interfaces, and those cells are left open until an implementation for that platform settles them against its own accessibility guidance. An implementation MUST NOT fill one by guessing.

## The keyboard

Every action a pointer can take MUST also be reachable from the keyboard. A component that holds several items the reader moves between, such as a tab list, a menu, a tree or a grid, is one stop in the tab order, and the arrow keys move within it. The platform's usual keys activate: Enter and Space for buttons, Enter for links, Space for checkboxes and switches, Escape to close what was opened.

## Focus

The focused element MUST always be visible. PUDL draws focus as a 3px ring in `focus-ring` outside the element's border, or in `focus-ring-danger` on a destructive control. A ring MUST reach 3:1 against what surrounds it, as WCAG 2.2 requires for focus indicators. Focus is shown for the keyboard and SHOULD NOT be shown for a pointer press, since a ring that appears on every click teaches the reader nothing.

When a component closes, such as a menu, a dialog or a window, focus returns to the element that opened it, or, where that element has gone, to the nearest sensible place.

## Contrast

Text reaches 4.5:1 against its background, and text at `text-lg` and above in bold reaches 3:1. The bounds of a control, and anything that says what state a control is in, reach 3:1 against what surrounds them. These hold in both themes and in every state except disabled. A theme that changes the palette MUST keep them, as chapter 3 says.

## High contrast

When the reader has asked their system for high contrast, the system replaces the application's colours with a few of its own and, on most platforms, removes shadows. Much of PUDL's elevation is drawn with shadows, so in that mode an implementation MUST keep every control's border, draw focus as a solid 2px outline in the system's highlight colour, and draw every selected, pressed, checked or current state in the system's highlight colours, since the change of elevation that marks it would not show. Glyphs MUST still paint, in the system's text colour.

## Less motion

When the reader has asked their system for less motion, every transition and animation completes at once. An implementation MUST NOT move content the reader did not move.

## Right to left

In a right-to-left language, the layout of every component mirrors. A sidebar sits on the right, a selected row marks the edge facing its detail, a menu lines up with its button's right edge, a switch that is on slides to the left, and the arrow keys follow what the reader sees. Glyphs that point, such as back and the branch of a child row, turn round. Coordinates that are positions rather than reading order, such as a window's place in its workspace, stay measured from the left.

## The application's own words

Every word an implementation writes into an application on its own account, such as the name of a window's minimise button or the words for "unsaved", MUST be replaceable by the application, so that an application can be written in the reader's language. English is the default.

## Print

A printed page carries the content without the chrome: no application bar, tab bars, toolbars or dividers, and dark text on a white page even from the dark theme. A layout showing a record prints the record alone, and with windows open, the window in front prints as the page's content.

## Questions this chapter must settle

- What replaces each affordance that relies on a pointer resting over something, on a device with no hover. Tooltips are one, and the layout picker on a window's maximise button another, though the window menu already carries the same picker.
- The minimum size of a target. In the web implementation the small button is 25px tall and the default button 33px, which meet WCAG 2.2's minimum of 24px at level AA and fall short of the 44px that touch guidance on the mobile platforms asks for.
- Whether printing belongs to the language at all, since many platforms have no notion of printing an application's view.
