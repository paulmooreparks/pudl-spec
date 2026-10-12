# Zoom

A zoom group scales a picture that is larger than the place it is shown in, such as a chart of a flow or a diagram in a document, so the reader can take in the whole of it or look closely at a part. It belongs to a **viewport**, the scrolling box the picture sits in, and it stands above or beside that box.

## Anatomy

The group is a row of controls, `space-1` apart, in this order:

- **Zoom Out**, a glyph button carrying `minus`.
- The **scale**, the picture's size as a percentage of its own, flat text at `text-sm` in `text`, in tabular figures, at least four characters wide so that the row does not shift as the number changes.
- **Zoom In**, a glyph button carrying `plus`.
- **Fit**, a small button with that word, which sets the scale at which the picture's width fills the viewport, and no larger than its own size.

The two glyph buttons are raised, as everything pressable is, and the scale is flat, since it shows a value. The viewport is a sunken box, as a text area is, whose content scrolls in both directions, and the picture inside it is drawn at its own size times the scale.

## States

| Part | State | Appearance |
|---|---|---|
| Zoom Out | At the smallest scale | Disabled, as a glyph button is |
| Zoom In | At the largest scale | Disabled |
| Fit | While the scale is the fitted one | As at rest; it does not latch, since the scale says what it is |
| The viewport | Focused from the keyboard | A 3px ring in `focus-ring` drawn inside its edge, as a window's body shows focus |

## Interaction

Zoom Out and Zoom In divide and multiply the scale by a step, 1.25 by default, between a least and a greatest scale, 5% and 800% by default; the application MAY set all three. A change of scale keeps the point at the middle of the viewport where it was, so the reader does not lose the part they were looking at. Fit sets the scale to fill the viewport's width and scrolls to the picture's start. While the viewport has focus, Ctrl with Plus, Minus and 0 zoom in, zoom out and fit, and Ctrl with the wheel zooms about the pointer, so that the browser's own zoom, which the same keys reach elsewhere, is not taken from the reader anywhere but there. The viewport is a stop in the tab order, since it scrolls.

Each change tells the application the new scale and whether it is the fitted one, and the application MAY remember them for the reader, as chapter 7 allows for a preference; a page restores a scale by giving it to the viewport before the script runs.

## Accessibility

The group is exposed as a group named for what it zooms, such as "Chart zoom". Each glyph button has its name, Zoom Out and Zoom In, and the scale is a live region that announces each new value politely. The viewport has an accessible name saying what it holds. In the platform's high-contrast mode the buttons keep their borders and the glyphs are drawn in the system's text colour.

## Questions this section must settle

- Whether pinch on a touch screen zooms the picture, and whether a double-tap fits it. The web implementation answers neither gesture.
- Whether the scale may be typed, as a field, rather than only stepped.

## Conformance checklist

1. The group is Zoom Out, the scale, Zoom In and Fit in that order, the buttons raised and the scale flat, with the `minus` and `plus` glyphs drawn and never characters.
2. Zoom Out and Zoom In are disabled at the least and greatest scale, and the scale stays between them.
3. A change of scale keeps the viewport's middle where it was; Fit fills the viewport's width and goes to the picture's start.
4. Ctrl with Plus, Minus and 0 zoom while the viewport has focus and nowhere else; Ctrl with the wheel zooms about the pointer.
5. The scale is announced as a live region, the group and viewport are named, and the viewport is a tab stop that shows focus inside its edge.
6. The application is told each change, and a scale it gives the viewport is restored.
