# Empty and loading states

An empty state takes the place of content that is not there yet. It tells the reader that a list, a folder or a view has nothing in it, and what they can do about that. A loading state takes the place of content that is on its way, and says in words what is being fetched. A view never shows a blank frame for either, because a reader cannot tell a blank frame that is empty from one that is still loading, or from one that has failed.

## Anatomy

### Empty state

An empty state is centred in the space the content would fill, with `space-6` of padding above and below and `space-4` either side, and its parts are `space-2` apart.

- A **glyph**, the `empty` glyph at 36px, in `text-muted` at 70% opacity, with `space-1` more below it.
- A **title**, which says what is missing, such as "No expenses on this trip yet", set at `text-lg` and weight 700 in `text`.
- A **body**, a sentence or two on what the reader can do, set at `text-md` in `text-muted` and no wider than about 42 characters to a line.
- **Actions**, which MAY follow, as a row of buttons centred and `space-2` apart, with `space-2` more above them. One of them may be the context's primary action, such as "Add an expense".

The body and the actions are optional. A data table with no rows uses its own empty row, which the data tables section specifies, in place of an empty state.

### Loading state

A loading state is a **spinner** followed by **words**, such as "Loading expenses…", centred in the space the content will fill. The two are `space-2` apart, the words are set at `text-sm` in `text-muted`, and the whole has `space-5` of padding above and below and `space-4` either side.

The spinner is a ring 1.2 times the size of the words, drawn with a 2px stroke. Most of the ring is the colour of the words at 22% opacity, and a quarter of it is the colour of the words at full strength; that quarter goes round once every 0.8 seconds at a steady speed. The spinner is never shown without words.

### A region being refreshed

When a part of a view is being replaced with fresh content and its old content is still worth reading, the part MAY stay in place and dim to 60% opacity until the new content arrives, instead of giving way to a loading state. The dimming begins after a short delay, 0.12 seconds on the web, so a quick refresh does not flicker.

## States

An empty state has no states of its own; its actions keep the states of buttons. A loading state has two.

| State | Appearance |
|---|---|
| Loading | The spinner turns, and the words say what is loading |
| Loading, for a reader who has asked for reduced motion | The spinner stands still, and the words say what is loading |

## Interaction

Neither an empty state nor a loading state takes focus or responds to the pointer, apart from the actions an empty state holds. When the content arrives, it takes the loading state's place.

## Accessibility

A loading state is exposed as a status, so its words are announced without taking the reader's focus, and the spinner is hidden from assistive technology, since the words already say what it shows. A region being refreshed is exposed as busy until its new content arrives. An empty state's glyph is hidden from assistive technology; its title and body are read as text.

In the platform's high-contrast mode the empty state's glyph is drawn in the system's text colour, and the spinner's ring in the system's text and disabled-text colours, so both stay visible.

## Questions this section must settle

- Whether an empty state's title is exposed as a heading. The web implementation sets it as ordinary text.
- Whether an application may use a glyph other than `empty` in an empty state, such as a folder for an empty folder, or whether the language fixes one.
- Whether the language offers a measured progress indicator, for work whose share done is known, and placeholder shapes that stand in for content while it loads. The web implementation offers neither.
- How long a load must take before a loading state appears, so that a fast load shows nothing rather than a flash of spinner. The web implementation sets a delay only for a region being refreshed.
- How an error in loading is shown in the space a loading state held. The notices section may be the answer, but neither section says so yet.

## Conformance checklist

1. An empty state shows the `empty` glyph at 36px and a title at `text-lg` and weight 700, centred.
2. An empty state's body, when present, is `text-md` in `text-muted`, and its actions, when present, are buttons.
3. A loading state shows a spinner together with words, and never the spinner alone.
4. A loading state is exposed as a status, and its words are announced when it appears.
5. The spinner is hidden from assistive technology.
6. With reduced motion requested, the spinner does not turn.
7. A region being refreshed in place is exposed as busy until its content arrives.
8. Neither state takes focus, apart from an empty state's actions.
9. In high-contrast mode the empty state's glyph and the spinner stay visible.
