# Menu bars

A menu bar holds an application's commands in menus along its application bar, as a desktop application's menu bar does. There is one in the application however many windows are open, and it shows the menus of what the reader is in. It gives an applet's commands a place the reader can find, which a window menu's small button does not.

## Anatomy

The menu bar stands at the start of the application bar, in the brand's place. It holds at most two **menus**. The **host menu** is the application's own and is always there. The **front menu** belongs to whatever is in front, an applet or an article, and stands to the right of the host menu, so the host menu never moves or changes width as the reader moves between windows.

Each menu is one raised surface in the bar's own colours, filled with `tb-chip` and casting `tb-chip-shadow`, with corners of `radius-sm` and 2px of padding. The `menu` glyph stands at its start, 16px across in a 26px square, in `tb-chrome-fg`; pressing it opens the menu's first title. After it come the menu's **titles**, flat words at `text-sm` and weight 600 in `tb-chrome-fg`, padded 4px above and below and 10px at the sides, with corners of `radius-xs`. The titles take their press from the surface around them, as the positions of a segmented control do, so nothing flat is pressable on its own. Under the pointer a title takes a faint fill of `tb-fg` at 12%, and the open title is pressed into the surface, its fill darkened and shaded from above.

A menu's first title is its name. The host menu's first title is the application's mark and name, set in the display face, and its panel holds the application's places. The host's other titles are its standard ones, such as View, Window and Help, and a title MAY be shown only where it means something, such as Window on a page of windows. A front menu's first title is the name of the applet or article.

A title opens a **panel**, a menu panel as the section on menus describes, below it. A panel holds **commands**, separators, headings for the commands below them, and submenus. A command shows its shortcut at its end in `text-muted` at `text-xs`, and a submenu's row carries the `caret` glyph turned to point at where the submenu opens. A command that switches something on and off carries the `tick` glyph while it is on, and one of a group of which only one is on carries it on the one that is.

## Rules for a front menu

A front menu MUST NOT use a title the host menu has. It MAY add commands to one of the host's titles, which appear in that title's panel below a separator, under a heading with the front menu's name, and only while it is in front. It can add commands but never rename, remove or reorder the host's. Within one panel, every command's label is different. An implementation MUST leave out a title or a command that breaks either rule, and SHOULD say so in a way a developer sees, naming what broke it, so that a clash cannot ship unseen.

An applet that offers only a list of commands gets a front menu of one title, its own name, holding them, so every applet has a place in the bar without changing.

An article's menu is made of links, since every state of a PUDL application has an address. Its first title, the article's name, holds what every article offers: opening it as a page, copying its link, printing it, and in a window closing it. A link to a heading in the article moves to that heading, in its window if it has one, without changing the address; any other link is followed as a reader's press on it would be.

## Where commands live

Each command has one home. Where the application has a menu bar, an applet's commands live in its front menu, and the window menu holds only the window's own commands. Where there is no menu bar, the window menu holds the applet's commands, as the section on windows describes, since they would otherwise have no home.

## In a narrow space

When the bar does not fit, it becomes one menu button, the `menu` glyph alone, whose panel lists each menu as a section of its titles under the menu's name. Choosing a title shows its commands in the panel's place, with a Back row first, one level at a time; a submenu opens the same way. An implementation decides when the bar does not fit by measuring it.

## Shortcuts

A command MAY have a shortcut, written with `Mod` for the platform's command key, which is Ctrl on Windows and Linux and Command on a Mac, as `Mod+S`. A front menu's shortcut works while focus is in what the menu belongs to, and a host menu's works anywhere. A shortcut with no modifier does nothing while focus is in a field.

A command MUST NOT claim a key a page cannot have or that every field needs: `Mod` with N, T, W, Q or Tab, with or without Shift, which browsers keep for their windows and tabs, and `Mod` with A, C, X or V, the editing keys. A command that claims one keeps its place in the menu without the shortcut, and the implementation says so as it says so of a clash. These have one meaning everywhere, and a command that uses one MUST mean it: `Mod+S` save, `Mod+O` open, `Mod+Z` undo, `Mod+Y` and `Mod+Shift+Z` redo, `Mod+F` find, `Mod+P` print, F2 rename, and Delete.

## Interaction

Pressing a title opens its panel, and pressing it again closes it. With a panel open, moving the pointer to another title opens that title's panel instead. Choosing a command closes the panel, gives focus back to where it was before the reader came to the bar, and then carries the command out, so that a command acting on the focused thing finds it. A disabled command is shown and can be reached, and does nothing when chosen.

The whole bar is one stop in the keyboard's tab order.

| Key | On a title | In a panel |
|---|---|---|
| Left and Right | Move to the previous or next title, across both menus; with a panel open, its panel opens instead | Right opens a submenu, or moves to the next title and opens it; Left closes a submenu, or goes Back, or moves to the previous title and opens it |
| Down, Enter, Space | Open the panel, with focus on its first command | Down moves to the next command; Enter and Space choose |
| Up | Open the panel, with focus on its last command | Move to the previous command, and from the first, back to the title |
| Home, End | Move to the first or last title | Move to the first or last command |
| Escape | Close an open panel | Close the submenu or the panel, back on its row or title |
| Tab | Leave the bar | Close the panel and leave the bar |
| A letter | | Move to the next command that starts with it |

An implementation MAY also give the bar a key that moves focus to its first title, where the platform has one an application can use without taking it from the reader's other tools.

## Accessibility

The bar is exposed as a menu bar, each menu as a group named by its name, each title as a menu item that opens a menu and says whether it is open, and each panel as a menu named by its title. A command is exposed as a menu item, a command that switches as a checkable menu item, and one of a group as a radio menu item, each with its state. A disabled command is exposed as disabled, and a command with a shortcut announces it. In the platform's high-contrast mode each menu keeps a border, and the open title takes the system's highlight colours.

## Questions this section must settle

- Whether an applet may contribute a third menu, or a menu of its own beside its first title's, where two menus prove too few.
- How the host's standard titles are named in other languages, and whether a front menu's additions follow them by name or by an identifier.
- Whether a front menu's shortcuts should work while focus is in the host's own chrome, such as the bar itself, with the applet still in front.

## Conformance checklist

1. The bar holds the host menu and, when something in front has one, its front menu to the right.
2. Each menu is one raised surface with the `menu` glyph at its start and flat titles, the open title pressed in.
3. A front menu never shows a title the host has, adds to a host title only below a separator under its name, and never changes the host's commands; what breaks a rule is left out and reported.
4. An applet with only a list of commands gets one title, its name, holding them.
5. With a menu bar, the window menu holds only the window's own commands.
6. The bar is one tab stop, and every key in the table above does what it says.
7. A disabled command can be reached by the arrow keys and does nothing when chosen.
8. Choosing a command closes the panel and gives focus back before the command runs.
9. A shortcut uses `Mod` for the platform's command key, shows in the platform's own form, is announced, and works only where it belongs.
10. A command never takes a reserved key.
11. When the bar does not fit it becomes one menu button whose panel opens one level at a time, and the page does not widen.
12. The bar, its menus, titles, panels and commands are exposed with the roles and states above.
