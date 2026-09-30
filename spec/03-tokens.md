# 3. Tokens

A token is a named value that PUDL draws with. The tokens fall into three kinds. The palette is what a theme sets. The scales belong to the language and stay the same everywhere. The derived tokens are computed from the palette by formulas, so a theme that sets the palette gets them without setting them.

The files in `tokens/` are the normative source for every value in this chapter. An implementation SHOULD generate its own form of the tokens from those files rather than copying values by hand, and it MUST give each token the name used there, adapted only as far as the platform's naming rules require. Every implementation then means the same thing by `surface-alt`, and a theme can be written once for all of them.

## The palette

The palette has a light form and a dark form, in `palette.light.tokens.json` and `palette.dark.tokens.json`, and every application offers both. Each form has the same tokens.

| Token | Role |
|---|---|
| `bg` | The page behind everything |
| `surface` | Cards, panels and the content area |
| `surface-alt` | The body of a raised control, and bands set off from a surface |
| `text` | Text |
| `text-muted` | Secondary text |
| `border` | Hairlines between flat regions |
| `accent` | The primary action, where the reader is, and focus |
| `accent-hover` | The accent under the pointer |
| `on-accent` | Text and glyphs drawn on the accent |
| `warn`, `danger`, `positive` | The status colours: needs attention, failed or destructive, done |
| `danger-hover` | The danger colour under the pointer |
| `light`, `shade` | The colour of the light that falls on a raised control, and of its shadow |
| `lit`, `depth` | How strongly the light shows and how strongly the shadow does, each a number from 0 to 1 |
| `tb-bg`, `tb-fg` | The application bar's background and foreground, which may stay dark on a light page |
| `syntax-keyword` to `syntax-error` | The ten colours of highlighted code |

`lit` and `depth` are how a theme tunes elevation. A light theme wants a strong highlight and a soft shadow, and a dark theme wants the reverse, which is why the light palette sets `lit` to 0.9 and `depth` to 0.18 and the dark one sets them to 0.07 and 0.48.

### What a theme may change

A theme sets any palette token, in both forms. The result MUST keep these rules.

- The three elevations of chapter 2 stay distinct. A theme tunes them through `light`, `shade`, `lit` and `depth`, and never by setting a derived token.
- Text reaches a contrast of 4.5:1 against its background, and the bounds of a control and a focus indicator reach 3:1 against what surrounds them, as WCAG 2.2 requires at level AA.
- `warn`, `danger`, `positive` and `accent` stay distinguishable from one another.
- Each syntax colour reaches 4.5:1 on `surface`, `surface-alt` and `input-bg`.

## The scales

The scales are in `scales.tokens.json`. The type scale runs from `text-2xs`, 11px, to `text-3xl`, 30px, and every size PUDL sets is one of its nine steps. The spacing grid has six steps on a 4px base, `space-1` to `space-6`, and spacing between and around components comes from it; a control's own padding belongs to the control. The radii are `radius`, 12px, for cards, panels and windows, `radius-sm`, 7px, for buttons, fields and tabs, and `radius-pill` for fully rounded ends.

A theme MUST NOT change the scales. It MAY change the three faces, `font`, `font-display` and `mono`, within the roles chapter 4 sets out.

## The derived tokens

The derived tokens are in `derived.json`, where each is a formula over the palette. An implementation MUST compute each one from the palette in force, so that a theme's palette reaches every derived value. A derived token with separate `light` and `dark` members has a formula for each theme.

### Colours

A colour in a formula is one of these.

- A token's name, such as `"surface-alt"`, which stands for that token's value in the theme in force. It may name a palette token or another derived token.
- A hexadecimal colour, such as `"#000"`, which stands for that colour in sRGB.
- `{ "srgb": [r, g, b], "alpha": a }`, a colour with its sRGB components and its alpha, each from 0 to 1.
- `{ "mix": [a, b], "by": p }`, colour `a` mixed into colour `b` in the proportion `p`. Each channel of the result is `a × p + b × (1 − p)`, computed in sRGB with the channels premultiplied by alpha, as [CSS Color 5's `color-mix()`](https://www.w3.org/TR/css-color-5/#color-mix) does. When both colours are opaque this is a plain weighted average of each channel.
- `{ "fade": a, "by": p }`, colour `a` with its alpha multiplied by `p`, which is the same as mixing it into a fully transparent colour.

### Amounts

The proportion `p` is one of these.

- A number from 0 to 1.
- A token's name, such as `"lit"`, which stands for that number token's value.
- `{ "token": t, "times": k }`, the value of number token `t` multiplied by `k`.

An amount that comes out below 0 or above 1 is an error in the theme. An implementation SHOULD report it, and MUST NOT silently clamp it into range.

### Paints

A token's value is a colour, or one of these.

- `{ "gradient": [top, bottom] }`, a linear gradient from the first colour at the top edge to the second at the bottom, interpolated in sRGB with premultiplied alpha.
- `{ "shadow": [layer, …] }`, one or more shadows. Each layer has an offset `x` and `y` and optionally a `blur` radius and a `spread`, all in px, a `color`, and `inset`, which is true for a shadow cast inside the shape rather than outside it. The first layer is drawn on top. A platform that cannot draw a blurred shadow SHOULD draw the nearest it can, and MUST keep the three elevations distinct without it, as chapter 2 requires.

### An example

The top of a raised control is the light mixed into `surface-alt`, as strongly as `lit` says:

```json
"raise-top": { "mix": ["light", "surface-alt"], "by": "lit" }
```

With the light palette that is `#ffffff` at 0.9 into `#e4e7eb`, which comes to about `#fcfdfd`. With the dark palette it is `#e8eef6` at 0.07 into `#23272d`, about `#31353b`. A theme that changes `lit` changes both results, and changes nothing else.

## Glyphs

The glyphs are in `glyphs/`, one SVG file each, drawn on a 16-unit grid and filled or stroked in black. Chapter 5 sets out their meanings and how they are drawn.
