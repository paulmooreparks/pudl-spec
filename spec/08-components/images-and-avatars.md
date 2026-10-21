# Images and avatars

## Images and figures

A figure is a picture with its caption. The picture stands in a frame with a 1px line in `border` and `radius-sm` corners, on a fill of `surface-alt` that shows while it loads. The frame takes the picture's proportion before the picture arrives, so the page never moves when it does, which is one of the complaints made most often about pictures on the web. The picture covers its frame, or MAY fit inside it on the fill. The caption stands under the frame at `text-sm` in `text-muted`.

A figure MAY lay its caption over the foot of the picture, on a shade dark enough for white words to read on any picture, where room is short, as in a gallery; or MAY drop its frame and fill, for a picture with edges of its own, such as a diagram.

A picture that fails to load is never shown as the platform's broken picture. Its frame keeps its proportion, and shows the picture's alternative text centred on the fill under the `image` glyph, and it is still exposed as a picture with those words.

Every picture that carries meaning has alternative text, and one that is only decoration has empty alternative text.

## Avatars

An avatar stands for a person or an agent: their picture, or their initials, in a circle. It is neutral by default, filled with `surface-alt`, bounded by `border`, with the initials in `text` at weight 700, so it is never mistaken for a status. It comes in four sizes: 24px, 32px, 40px and 64px. A picture that fails to load gives way to the initials.

An application MAY tint avatars by name: each takes a soft tint whose hue is worked out from the name, so the same person has the same colour everywhere. The tint means nothing else, and the initials keep at least 4.5:1 against it at every hue, in both themes. Since a reader may not see the tint, the initials are always there.

An avatar MAY carry a status mark at the foot of its circle, ringed in the colour of the surface around it, with a shape as well as a colour: online is a filled circle in `positive`, away a half-filled circle in `warn`, busy a minus in `danger`, and offline a ring in `text-muted`.

## Accessibility

An avatar is exposed as a picture named by the person's name. Its status mark is exposed with its status in words, such as "Online".

In the platform's high-contrast mode a frame and an avatar keep a border, and glyphs are drawn in the system's text colour.

## Conformance checklist

1. A figure's frame takes the picture's proportion before it loads, on a quiet fill, and its caption stands below in muted words, or over the picture on a shade, or the frame is dropped where the application asks.
2. A picture that fails shows its alternative text under the image glyph in a frame of the same proportion, never the platform's broken picture.
3. An avatar is a circle in one of four sizes, neutral unless tinted, showing the picture or the initials, and the initials when the picture fails.
4. A tinted avatar's hue comes from the name, and its initials reach 4.5:1 at every hue in both themes.
5. A status mark has a shape as well as a colour and is exposed in words.
