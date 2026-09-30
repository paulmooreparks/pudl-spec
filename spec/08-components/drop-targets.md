# Drop targets

A drop target is a place where something the reader is dragging may land, such as a list that takes files dropped on it or a folder's row that takes a file moved into it. What may be dropped where is the application's rule, so the application decides when a place is a target and what a drop there does. PUDL supplies how a target looks while something is over it, so every application shows the same thing.

## Anatomy

A drop target takes one of two forms.

- A **drop zone** is a region, such as a list or an empty panel, that takes a drop anywhere inside it. A zone MAY hold a hint, a short line saying what dropping there will do, such as "Drop text files here to upload them".
- A **target item** is one thing within a larger view, such as a folder's row in a file list, that takes a drop on itself.

Neither form changes the appearance of the place at rest. While something the place would take is dragged over it, the place is ringed and tinted. The ring is 2px of `accent` drawn inside the place's edge, following its corners, and the tint is `accent` at 7% laid over the place's own fill, so the content inside stays readable.

A zone's hint shows only while something is over the zone. It sits centred along the zone's foot, 12px above its lower edge, on one line. It is filled with `accent` with its words in `on-accent`, at `text-sm` and weight 600, padded 4px above and below and 12px at the sides, with fully rounded ends (`radius-pill`). The hint does not take the pointer, so it never becomes the target itself.

## States

| State | Appearance |
|---|---|
| At rest, or while something it would not take is dragged over it | Unchanged |
| Something it would take is dragged over it | A 2px `accent` ring inside its edge, a 7% `accent` tint, and a zone's hint shown |

A place that would not take what is being dragged does not change at all, so a ring always means that a drop there will be accepted. The ring gives the state a shape as well as a colour, which the tint alone would not.

## Interaction

The application marks a place as the target while something it would take is over it, and clears the mark when the dragged thing leaves or is dropped.

Dropping on a marked place does what its hint says, or what the target item stands for. Dropping anywhere unmarked does nothing.

Dragging is never the only way to do what a drop does. The application MUST offer another route to the same outcome that needs no dragging, such as a button that chooses files or a command that moves an item, as WCAG 2.2 requires of every action done by dragging.

## Accessibility

A zone's hint, when it has one, is in the application's words and says what a drop will do. The route that needs no dragging is the one a reader using a keyboard or assistive technology takes, so it is labelled with the same outcome.

In the platform's high-contrast mode the ring is drawn as a 2px dashed outline in the system's highlight colour, since the ring and the tint are both drawn in colours the mode replaces, and the hint takes the system's highlight colours.

In a right-to-left interface the hint stays centred along the zone's foot.

## Questions this section must settle

- Whether the state of being over a target is exposed to assistive technology. Chapter 2 requires a state that is shown to be exposed as well, and the web implementation shows this one and exposes nothing, relying on the route that needs no dragging.
- Whether the hint, a pill filled with the accent, borrows the appearance of another category. Chapter 2 keeps badges and chips apart from everything else, and the hint is a fully rounded label in a status-like fill.
- Whether a zone and a target item inside it may be marked at once. The web implementation's file browser sample rings the list and the folder's row under the pointer together, although the drop lands in only one of them.
- Whether a target that would refuse what is dragged over it should say so, rather than staying unchanged.

## Conformance checklist

1. A drop zone and a target item look the same at rest as they would without being targets.
2. While something the application would accept is over it, a target shows a 2px `accent` ring inside its edge and a 7% `accent` tint.
3. A place that would not accept what is dragged over it does not change.
4. A zone's hint shows only while something is over the zone, centred along its foot, in `on-accent` on `accent` at `text-sm` and weight 600.
5. The hint does not take the pointer.
6. Every action a drop performs can also be done without dragging.
7. In high-contrast mode the target shows a dashed outline in the system's highlight colour.
