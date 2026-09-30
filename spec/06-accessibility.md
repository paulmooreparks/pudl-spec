# 6. Accessibility

Status: not yet written.

This chapter will list the roles and states every component uses, and map each to the accessibility interface of the common platforms: ARIA on the web, UI Automation on Windows, NSAccessibility on macOS and AT-SPI on Linux. It will also set the requirements for focus, contrast, target sizes, high-contrast modes, reduced motion, right-to-left languages and print.

The states PUDL marks, with the ARIA attribute the web implementation uses for each:

| State | ARIA |
|---|---|
| The current place | `aria-current` |
| Pressed, for a toggle button | `aria-pressed` |
| Checked, for a switch or a checkbox | `aria-checked` |
| Selected, for a tab of a tab panel or a row among choices | `aria-selected` |
| Disabled | `disabled`, or `aria-disabled` where the element cannot be disabled |

Questions this chapter must settle:

- What replaces each affordance that relies on a pointer resting over something, on a platform or device with no hover. The web implementation's layout picker on the maximise button is one; its window menu already carries the same picker.
- The minimum target size, and whether the small button size meets it on touch screens.
