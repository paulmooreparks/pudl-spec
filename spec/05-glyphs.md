# 5. Glyphs

Status: not yet written.

This chapter will give each glyph in `glyphs/` its meaning and where PUDL uses it, and say how a glyph is drawn: as a mask filled with the colour of the text around it, at the size the component sets, never as a character from a font.

Every glyph is an SVG file on a 16-unit grid, drawn in black with fills and strokes only, so that any platform can draw it from its path data. The web implementation draws them as CSS masks. A platform without vector drawing, such as a terminal, will need a character or a small cell pattern for each.

Questions this chapter must settle:

- What a terminal implementation draws for each glyph. Chapter 2 says glyphs are drawn and never font characters, and a terminal can only show characters, so the rule needs a stated exception with its own safeguards, such as a fixed character set known to render in the common terminals.
- Whether the glyph set is closed, or an application may add glyphs of its own in the same style, and how it names them.
