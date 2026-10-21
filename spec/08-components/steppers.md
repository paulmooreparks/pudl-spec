# Steppers

A stepper shows the steps of a task that takes several pages, such as setting up a configuration, which of them are done, which one the reader is on, and which are still to come. It answers the two complaints made most often about wizards: that there is no way back to fix an earlier step, and that there is no telling how much is left.

## Anatomy

A stepper is an ordered list of steps. Each step has a mark and a short name.

- A step that is **done** has a mark of a circle 24px across filled with `accent`, holding the `tick` glyph in `on-accent`, and its name in `text`. Its name is a link back to the step's page.
- The **current** step has its number in `accent`, in a ring 2px wide in `accent`, and its name in `text` at weight 700.
- A step **to come** has its number in `text-muted`, in a ring 1px wide in `border`, and its name in `text-muted`.

Each state is told by its mark's shape as well as its colour, as chapter 2 requires: a tick, a heavy ring and a light ring.

The steps run across the width, each joined to the next by a line 2px thick, in `accent` after a step that is done and in `border` otherwise. On a window 640px wide or less, only the current step keeps its name in sight, and the others show their marks, so the stepper never wraps.

A stepper MAY run down the side instead, each step a row with its mark and its name, the current row lit as the current row of a list is, with a bar of `accent` on its start edge. This form suits long names and many steps.

## Interaction

A done step's name is a link, which goes back to that step's page. The current step and the steps to come are not links, since the reader reaches a later step by completing the current one.

## Accessibility

A stepper is exposed as a list, with an accessible name that says what task it is, such as "Add a configuration". The current step is exposed as the current step. A done step's state is part of its accessible name, such as "Client (done)", since its tick is not read.

In the platform's high-contrast mode the marks keep their shapes in the system's text colour, and the current step's ring takes the system's highlight colour.

## Conformance checklist

1. Every step shows a mark and a name, and done, current and to come differ by the mark's shape as well as its colour.
2. A done step's name is a link back to its page.
3. Steps across are joined by lines that take the accent after a done step.
4. On a window 640px wide or less, only the current step's name stays in sight, and every mark stays.
5. The stepper down the side lights the current row as a list's current row.
6. The stepper is a named list, the current step is exposed as current, and a done step's state is part of its name.
