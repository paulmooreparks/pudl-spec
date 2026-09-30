# The PUDL specification

PUDL is the Pleasantly Usable Design Language. It gives every affordance one visual representation, so that somebody who has learned it in one application can use any other application built with it on sight. This repository holds the language itself: the rules, the tokens, the glyphs and what each component must be and do, written so that any platform can implement them.

An implementation carries the language to a platform. The web implementation, a stylesheet and a set of optional scripts, lives at [paulmooreparks/pudl](https://github.com/paulmooreparks/pudl), and it is where PUDL began. An implementation for Avalonia, which reaches Windows, macOS and Linux from one codebase, is the next one planned. Each implementation is a repository and a package of its own, and each release of one says which version of this specification it implements.

## What is here

- [`spec/`](spec/) holds the specification, one chapter per file, starting at [the introduction](spec/01-introduction.md).
- [`tokens/`](tokens/) holds the palette and the scales in the [Design Tokens Community Group format](https://www.designtokens.org/tr/2025.10/format/), and the derived tokens as formulas in `derived.json`, which [chapter 3](spec/03-tokens.md) defines.
- [`glyphs/`](glyphs/) holds every glyph as an SVG file on a 16-unit grid.
- `VERSION` holds the version of the specification these files make up.

An implementation generates its own form of the tokens and glyphs from these files, so a theme written once reaches every platform, and nobody copies a colour by hand.

## Status

This is version 0.1.0. The grammar, the tokens and the button are written; the other chapters are outlines. The specification reaches 1.0 when every chapter is written and the web implementation passes every conformance checklist, and the web implementation's own 1.0 waits for it.

## Changing the language

A change to the language is a change here, reviewed as such, and each implementation follows it in a release of its own. A bug fix in one implementation, or a change to how it carries out a rule, belongs in that implementation's repository and leaves this one alone.

## Licence

The specification, the tokens and the glyphs are released under the Apache License 2.0. See `LICENSE`.
