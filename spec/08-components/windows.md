# Windows

A window shows a record, a document or a tool in a movable frame of its own above the rest of the application, so the reader can keep several open at once, set them side by side and come back to each. Windows are never modal. Each window's content keeps a place of its own in the application, which the window is one way of seeing, so a window never stands in for a page.

This section covers the window itself, the windows a window opens for its own content, the dock of open windows, windows docked at an edge of the workspace, the zones a window snaps to with the layout picker that chooses them, and the window menu.

## Anatomy

### The workspace

Windows float over a workspace, the region of the application they may occupy, which is usually the main area below the application bar. The workspace does not scroll; the content inside it and inside each window does. The workspace holds the application's own content, beneath the windows, and that content stays usable wherever no window covers it.

Windows docked at the workspace's edges take strips of it, as Docked windows below describes. The rest is the inner area, and every window that is not docked is laid out in it. With nothing docked, the inner area is the whole workspace.

### A window

A window is a frame holding a title bar above a body.

The **frame** is `surface-alt`, bounded by a 1px hairline in `raise-border`, with corners of `radius`. A band 5px wide runs between that hairline and the hairlines of the title bar and body, so the frame reads as a band of the raised tint between two hairlines, and the whole band is where the window is resized from. The window casts a soft shadow in `shade`, in two layers: 2px down with a 6px blur at 0.8 times `depth`, and 10px down with a 28px blur at 0.9 times `depth`. A window is never smaller than 320px wide and 200px tall, or the whole inner area where that is smaller.

The **title bar** is raised, because the reader presses it to drag the window. It is filled with `raise-grad` and bounded by a 1px hairline in `raise-border`, with the light of `light` at `lit` along its top edge, and its top corners follow the frame's, at 7px. It is at least 38px tall, padded 5px above and below, 12px at its start and 7px at its end, with 10px between the things it holds. Its title is set at `text-md` and weight 700, on one line, ending in an ellipsis when the bar is too narrow for it.

The **window buttons** sit at the end of the title bar, 5px apart, with Close last. Each is a small raised circle, 24px across, filled with `raise-grad`, bounded by `raise-border` and casting `raise-shadow`, with its glyph drawn 12px across in `text-muted`. The buttons a window MAY carry are these.

| Button | Glyph | Does |
|---|---|---|
| Open as a page | `open` | Opens the window's content in its own place in the application, where it has one |
| Dock | `dock`, or `undock` while docked | Docks the window at the bottom edge, or undocks it |
| Minimise | `minimize` | Hides the window, which stays open in the dock of open windows; on a docked window, collapses or expands it |
| Maximise | `maximize`, or `restore` while not floating | Fills the inner area with the window, or returns it to floating |
| Close | `close` | Closes the window |

A window MAY also carry a menu button at the start of its title bar, with the `caret` glyph and 4px of extra space after it, which opens the window menu. An application MAY give every window one.

The **body** is `surface`, bounded by a 1px hairline in `border` at its sides and foot, with its bottom corners following the frame's. It is padded 16px above and below and 18px at the sides, and it scrolls on its own.

### The dock of open windows

The dock of open windows has one tab for each open top-level window, in the order the windows were opened, and it MAY sit anywhere in the application, usually in a toolbar above the workspace. An empty dock draws nothing and takes no height.

A tab is raised, with corners of `radius-sm`, filled with `raise-grad`, bounded by `raise-border` and casting `raise-shadow`, padded 3px above and below and 10px at the sides. Its words are the window's title at `text-xs` and weight 600, on one line, at most 220px wide and ending in an ellipsis. The tabs are 6px apart and wrap onto further lines when they need to.

Each tab starts with a glyph 9px across that says whether its window shows: `circle`, filled, in `accent` while it shows, and `ring` in `text-muted` while it is minimised, when the tab's words are in `text-muted` too. The glyph's shape carries the state without its colour.

An application MAY also offer two controls that act on every window at once: one that minimises them all, which shows what lies beneath, and one that restores them all, with the window that was in front back in front. Each is disabled while it would change nothing.

### The window menu

The window menu reaches every command a window has from one place, including the ones its title bar has no room for, and it is the keyboard's route to them. It is a menu, as the section on menus specifies, built afresh each time it opens so that every label is true at that moment. It holds three groups, divided by separators.

1. The window's own commands: Open as a page, where the content has a place of its own; Minimise, or Collapse or Expand on a docked window; Maximise or Restore, and the layout picker, on a window that is not docked; a Dock list; and Reset size and position, which returns the window to the placement its content gave it when it opened. The Dock list names the four edges, Top, Bottom, Left and Right, in that order, the edge the window is docked at carrying the `tick` glyph, and choosing an edge docks the window there; on a docked window it ends, after a separator, with Undock, which returns the window to where it floated. The list names all four edges on a narrow screen too, where a side dock shows at the bottom, since the window docks at its side again when there is room. Where the menu has submenus, as a menu bar's does, the Dock list is a submenu; in a window's own menu it MAY stand in the menu under a heading, as the layout picker does.
2. The commands of what the window holds, such as an editor's word wrap, in the content's own words. A command that switches something on and off shows the `tick` glyph while it is on, and a disabled command stays in the menu, dimmed.
3. Close, last and on its own, drawn as a destructive command, so that it is never chosen by a slip from the command above it.

The window's content can add its commands to the second group, but it cannot change or remove the window's own commands.

### Snap zones and the layout picker

A zone is a rectangle of the inner area on a grid of sixths, which holds the halves, the quarters, the thirds, and two thirds beside one third. A window snapped to a zone fills it, and follows it as the inner area changes size. The left half, the right half and the whole inner area are zones too, and a window in one of them is snapped to that half, or maximised.

The **layout picker** offers five layouts, each drawn as a thumbnail 48px wide and 32px tall: halves, quarters, thirds, two thirds beside one third, and one third beside two thirds. The thumbnails sit in a row 6px apart, padded 6px above and below and 14px at the sides. Each zone in a thumbnail is a small raised button, inset 1px from its neighbours, filled with `raise-grad` and bounded by `raise-border`, with corners of `radius-xs`, and pressing it snaps the window to that zone. The zone the window fills now is drawn pressed in and filled with `accent`, so it is marked by its elevation as well as its colour.

The picker sits in the window menu, after Maximise or Restore. On a platform with a mouse, resting the pointer on the maximise button for half a second also opens the picker in a panel of its own under the button, which closes once the pointer has left both the button and the panel for a moment. The picker is not offered on a docked window.

### Windows sized by the reader or by their content

A window is sized either by the reader or by its content, as a desktop window either has a sizing border or is a dialog that sizes itself to what it holds. A window is sized by the reader unless its content says otherwise. The content decides, because only the content knows whether it has a size of its own: a terminal or an editor fills whatever it is given, and a form or a tool with a fixed layout does not.

A window **sized by its content** takes its content's width and height, and follows them as they change, larger and smaller. When the reader changes something that changes how much the content holds, such as a setting that shows more fields, the window follows at once, and nothing asks the reader to accept it. Its top-left corner stays where it is while its size changes, so a control above the part that changed stays under the pointer. At the right and bottom of the inner area it stops, and its body scrolls.

Such a window has nothing to fill and no size of its own to change, so it cannot be resized, maximised, snapped or docked. Its frame is a single 1px hairline in `raise-border`, with no frame band, since the band is the border a reader drags to resize and this window has none; its title bar and body sit flush inside the hairline. It has no resize edges and no maximise or dock button, its window menu leaves out Maximise, the layout picker and Dock, and it offers Reset position in place of Reset size and position. A drag that ends at an edge moves it there without snapping it. Minimise, close, opening as a page and moving it by its title bar all work as they do for any window. Content that holds an applet tells the applet to flow, as chapter 9 sets out.

A window **sized by the reader** MAY carry limits, a smallest and a largest width and height in px. Every way the window's size is reached respects them: dragging, the keyboard, and restoring an arrangement, so that a terminal keeps a usable grid however small it is dragged, and an old arrangement cannot restore it below that.

### Docked windows

A window MAY be docked at an edge of the workspace, the top, the bottom, the left or the right. A docked window belongs to the workspace's frame. It takes a strip along its edge away from every other window, and nothing covers it: a maximised window ends where the dock begins, a snapped half is half of what is left, and a floating window cannot be moved into the strip. Top and bottom docks span the workspace's whole width, and side docks span the height between them.

The strip is the size of the docked window, a share of the workspace's height for the top and bottom and of its width for the sides. It is a quarter until the reader or the application sets another, and it is never more than 80% of the workspace, nor less than the docked window's title bar and a little of its body.

A docked window is flush with its edge. It has no shadow, no rounded corners and no frame band, and a 1px hairline in `border` separates it from the inner area along its free edge, the one facing the workspace. The free edge is a handle, as chapter 2 describes, so it carries the `grip` glyph at rest, at its middle and just outside the window, on the workspace, where it reads whatever colour the title bar is. Its title bar is thin, 30px tall, with a hairline at its foot, padded 10px at its start and 4px at its end, with 8px between the things it holds. Its title is set at `text-sm`, and its buttons are 20px across with glyphs 10px across. It has no maximise button.

An edge holds any number of docked windows and shows one at a time, the one most recently in front; the others wait behind it and come forward from the dock of open windows.

A docked window is **collapsed** rather than minimised. Collapsing it leaves its title bar in place along its edge and hides its body, and the strip shrinks to the title bar. A collapsed side dock is a strip as wide as a title bar is tall, with its title running down it.

### Child windows

A window MAY open children for content that belongs to it, such as a source listing, an image or a receipt. The relation belongs to the content, so the content says which window is a child's parent. A child is otherwise a window like any other, except in these ways.

- A child stacks directly above its parent, and bringing the parent forward brings its children with it.
- Minimising the parent hides its children, and closing the parent closes them.
- A child has no tab in the dock of open windows, and so has no minimise button. A parent's tab brings forward its topmost child, since that child covers it.
- Children nest one level. A child of a child stands on its own, as a top-level window.

### Windows and a list

A list whose rows open windows, such as the sidebar of a [master-detail layout](master-detail.md), follows the windows. The row whose window is in front is marked current, as the row of the record in view is. Beneath the row of a window with open children, a row for each child is added, titled with the child's title, which brings that child forward when chosen and goes when the child closes. A child's row is indented 32px, with its title at `text-xs`, and it starts with the `branch` glyph at 12px in `text-muted`, so the relation does not rest on the indent alone. A list inside a menu marks the current row and gains no child rows.

## States

A window has one placement at a time, and a placement has a mode.

| State | Appearance |
|---|---|
| Floating | Framed and shadowed, as under Anatomy, at its own position and size in the inner area |
| Maximised | Fills the inner area, flush: no frame band, border, corners or shadow, and a hairline at the title bar's foot |
| Snapped to a half or a zone | Fills its zone, flush as a maximised window is, with a 1px hairline in `raise-border` where it meets another zone rather than the edge of the inner area |
| Docked | Flush along its edge, as under Docked windows |
| Docked and collapsed | Its title bar alone, along its edge |
| Minimised | Not shown; its tab in the dock of open windows shows the `ring` glyph and muted words |
| In front, the active window | As below |
| Being dragged | Follows the pointer; an outline shows where it will land when released over a zone or the dock edge |

At most one window is in front, and none is when every window is minimised. The window in front has a frame whose hairline is `accent` mixed at 45% into `raise-border`, and a stronger shadow, 3px down with an 8px blur at 1.1 times `depth` and 18px down with a 48px blur at 1.4 times `depth`. Its title bar takes the accent. In the light theme the bar is filled with the accent, lit toward its top by white mixed in at 10%, bounded by `accent-hover`, with its title in `on-accent`. In the dark theme, whose accent is too bright to fill a bar, the bar is the raised gradient tinted toward the accent, `accent` mixed at 32% into `raise-top` at its top and at 20% into `surface-alt` at its foot, bounded by `accent` mixed at 55% into `raise-border`, with its title in `text`. A docked window in front keeps its flush look, and its hairline takes `accent` mixed at 45% into `border`. Besides these colours, the window in front shows by its place above the others and by the pressed-in tab of its family in the dock of open windows.

The outline that shows where a dragged window will land is filled with `accent` at 12%, bounded by a 2px dashed line of `accent` at 60%, with corners of `radius`.

The window buttons follow [the button's](buttons.md) states, drawn on a circle: under the pointer the glyph takes `text` and the fill and border their hover tokens, while pressed they are pressed in, and focus adds a 3px ring in `focus-ring`. The close button's glyph turns `danger` under the pointer. The menu button stays pressed in while its menu is open. The maximise button's glyph and name become Restore whenever the window is not floating, and the minimise button of a docked window is named Collapse or Expand.

A tab in the dock of open windows follows the button's states. The tabs are a set of raised controls offering places, so the tab of the family in front is drawn pressed in, as chapter 2 requires of where the reader is, and is exposed as current.

A zone in the layout picker is filled with `accent` mixed at 35% into `surface`, bounded by `accent` and without its shadow, while under the pointer or focused, and focus adds a 2px outline in `accent`. While it is pressed, a zone is drawn pressed in: its fill becomes `raise-active-bg` and its shadow `raise-active-shadow`. The zone the window fills is drawn pressed in, with the shadow `raise-active-shadow`, filled and bounded with `accent`, and is exposed as current.

The title bar and the body are each a stop in the tab order. Focus on the title bar shows a 3px ring in `focus-ring` outside it, and focus on the body shows the same ring drawn inside its edge, since the body is a large area.

## Interaction

### Bringing a window forward

A press anywhere in a window, or focus moving into it, brings it in front at once, before any drag. A collapsed docked window brought forward stays collapsed; its own button, or its tab in the dock of open windows, expands it.

Pressing a tab in the dock of open windows brings its window forward, or its topmost child, and restores it if it was minimised. Pressing the tab of the window already in front minimises it, as a taskbar does.

Minimising the window in front passes the front to the highest window still showing, if there is one.

A window the reader brings forward takes the keyboard, as an activated window does on the desktop, however they bring it forward: by its title bar or frame, its tab, a row in a list, or its window menu. Focus goes back to the element that last had it in that window, if it is still there and can take focus. The first time, it goes to an element the content marks to take focus first, and otherwise to the title bar, where the keys that move and resize the window work. A window that already holds focus keeps it where it is. A press inside a window's body focuses what it lands on, as usual. A window that arrives some time after the reader asked for it, such as one fetched from a server, takes focus only if the reader has not moved it elsewhere in the meantime.

### Moving and resizing

Dragging the title bar moves the window, from anywhere on the bar except its buttons. A press that moves less than 4px is not a drag. Dragging a maximised, snapped or docked window lifts it back to its floating size under the pointer, at the same point along its title bar, and undocks a docked one. A floating window is always kept inside the inner area.

A floating window resizes from any edge or corner of its frame. Each edge takes the pointer across a strip 10px wide, straddling the frame so that the band and a hair beyond it can be grabbed, and each corner across a square 15px on a side. A window never goes below its least size. A maximised, snapped or docked window does not resize from its frame, except that a docked window resizes along its free edge.

A double-click on the title bar maximises a floating window, restores a maximised or snapped one, and undocks a docked one.

### Snapping and docking by dragging

When a drag ends, where the pointer is decides where the window lands, and while the drag is under way the outline shows it.

- Within 16px of the inner area's left or right side, the window snaps to that half, or to the quarter at that corner when the pointer is also within 64px of the top or the bottom.
- Within 16px of the inner area's top, the window maximises, or snaps to a top quarter when the pointer is also within 64px of a side.
- Within 16px of the workspace's foot, and not within 16px of a side, the window docks at the bottom.
- Anywhere else, the window floats where it was dropped.

Dragging a docked window's title bar away from its edge undocks it, back to where it floated before.

### The layout picker and the window menu

Pressing a zone in the layout picker snaps the window to it. A zone window restores as a half does: the maximise button, named Restore, floats it again, and dragging it lifts it back to its floating size.

The window menu opens from its button, or from the platform's context-menu keys while the title bar has focus, with focus on its first command. The arrow keys and Enter move through it and choose, as in any menu. The picker's zones are rows of the menu, so the keyboard reaches every zone.

### Docking

The reader docks a window at the bottom by dragging it there or with its dock button or the Dock command, and the same button or command undocks it. An application MAY dock a window at any of the four edges, and MAY open a window already docked, which is how an application gives the workspace standing furniture, such as a panel of links at its foot, that the reader can still move and close.

A docked window keeps the floating placement it had, and returns to it when undocked. It keeps its strip's size while undocked too, so docking it again brings it back as it was.

### Opening a window

A window opens in front. It takes focus if focus is where it was when the reader asked for the window, or has fallen back to the application as a whole, so a window that takes a moment to arrive never pulls the reader away from something they chose in the meantime.

A window opening with no placement of its own takes the first of these that gives one.

1. A placement the application supplies for it, such as one it remembered.
2. The state of the window whose content opened it, so that following a link never overturns the reader's arrangement. From a maximised window it opens maximised, from a snapped one in the same zone, and from a floating one it floats 3% of the inner area down and to the right of its opener, starting again 3% from the top left when that step would run past the edge. A window opened from a docked window takes nothing from it.
3. The position its content gives it.
4. The mode its content gives it, with a position cascading from the top left to restore to. A reading application opens its articles maximised this way.

A floating window with no position cascades from 6% of the inner area from its left and 5% from its top, each new window a further 4% down and to the right, for six steps before starting again; it is 55% of the inner area wide and 75% tall.

A link inside a window MAY open its target in place of that window, as a link does in a browser tab. The new window takes the old one's placement and its place in the dock of open windows, the old one closes, and the change is one step in the reader's history, so going back returns to the old window.

When a window's content cannot be loaded, the application SHOULD take the reader to the content's own place instead, where it has one.

### Closing a window

Closing a window closes its children with it. Before a close the reader or the application asked for, the window's content, and each child's, MAY refuse it, as an editor with unsaved changes does while it asks what to do with them. A close that follows from the reader moving to another arrangement, such as stepping back through their history, cannot be refused, because the reader has already left.

After a close, focus returns to what opened the window if that is still there, and otherwise to the window now in front.

Escape closes a child window that is in front, as a lightbox closes, unless focus is in a text field. Escape never closes a top-level window, so that a stray key cannot lose the reader's place.

### Keys

With a window's title bar focused:

| Keys | On a window that is not docked | On a docked window |
|---|---|---|
| An arrow key | Floats the window and moves it 2% of the inner area | Nothing |
| Shift with an arrow key | Floats the window and resizes it by 2% of the inner area, Right and Down growing it | Moves the free edge by 2% of the workspace, the arrow pointing into the workspace growing the strip |
| Enter | Maximises or restores the window | Undocks the window |
| The context-menu key, or Shift with F10 | Opens the window menu | Opens the window menu |

Each window button is its own stop in the tab order and responds as a button does. Tab moves into and between windows in their order in the application, and focus moving into a window brings it forward.

### Default windows

An application MAY name default windows, standing furniture such as a panel of site links or a help strip. When the reader arrives with no arrangement of windows to restore, the default windows open where their content places them. Once the reader has an arrangement, even one with no windows open, the defaults do not come back of themselves. Default windows move, minimise and close like any other.

### Narrow screens

When the workspace is 640px wide or less, a window docked at a side shows at the bottom instead, since there is no room beside the content, and returns to its side when the workspace widens again. It keeps its own edge in the reader's arrangement.

When the workspace sits inside a [master-detail layout](master-detail.md), the windows are the detail pane. A layout narrow enough to show one pane at a time shows the windows while any window the reader opened shows, and the list otherwise; a default window does not turn the pane over by itself. The back control above the windows minimises every window, which returns to the list with the windows kept. An application whose detail pane holds content of its own, with windows floating over it, decides which pane shows itself.

### Shared side docks

An application MAY opt into shared side docks. Each side then has a tab strip for its docked windows, with one window shown below it. Choosing a tab raises that window without replacing its content. The strip spans the full width of its dock. Tabs follow the component's normal selected and unselected treatments.

All windows in a shared dock MUST use the same width. Resizing any member changes the dock's width, and changing tabs MUST preserve that width. A window moved into an existing dock adopts its width. The dock retains this preference when empty.

Shared dock tab labels use the compact badge font, `text-2xs` at weight 700 with line height 1.55. Collapse and Pin occupy the same outer top corner across dock modes, top-left for a left dock and top-right for a right dock. Tabs shift inward to make room in a pinned dock and follow Pin vertically in a rail.

A pinned shared dock omits window title bars. Each tab has a window-menu button in place of a close button. The selected tab connects visually to its content with no intervening border. Ordinary rail slideouts MAY retain their title bars. The menu remains accessible by pointer and keyboard, and closing through it uses the normal unsaved-change handling.

An application MAY identify required windows. A required window opens even when a restored arrangement omits it, cannot be closed or replaced, and has no close affordance. Required windows appear first in their dock, in the order the application supplies. They may still float or move to another edge.

Required windows MUST omit Close from every menu. A front menu with no applicable commands is omitted. Separators only appear between groups of commands, including when Close is the sole command.

An application MAY restrict a permanent side panel to the left and right docks. Such a panel cannot float, snap, maximise or dock at another edge, and has no title bar even in a rail slideout. Its pinned tab menu or keyboard context menu provides the applicable dock commands. Requiring the panel to stay open is a separate choice.

A shared side dock has an automatic mode, an open mode and a rail mode. Automatic mode uses a rail when the workspace is at or below a threshold set by the application, 960px by default. An explicit choice of open or rail persists across width changes. Shared side docks keep their side on narrow screens rather than moving to the bottom.

A rail is a narrow strip of the dock's tab glyphs. Activating a tab opens its window over the central area without moving the other windows. Working outside that window and rail retracts it. Escape retracts it and returns focus to the tab, except when a menu or dialog needs Escape first. Pinning the dock changes its mode to open; collapsing it changes the mode to rail. A temporary slideout changes neither the saved mode nor the window's canonical placement.

Rail buttons MUST use the same square icon control and dimensions as Pin. They omit dropdown buttons, including for permanent side panels. A button uses the depressed treatment while its slideout is visible and returns to the raised treatment when the slideout retracts.

Arrow keys move focus between tabs without selecting them, horizontally in an open dock and vertically in a rail. Home and End move focus to the first and last tabs. Enter or Space activates the focused tab. Delete requests closing it, using the same unsaved-change handling as the window's Close command. Closing a tab moves focus to a remaining tab when one exists.

An application MAY supply a glyph, an attention count, a running mark and percentage progress for a window. The dock tabs, rails and taskbar show those marks consistently. A rail may omit the visible percentage while including it in the accessible name and tooltip. Updates MUST preserve mounted content and keyboard focus. An attention count and running mark are distinguishable by shape as well as color.

An application MAY omit docked windows from the taskbar, including while their dock is collapsed to a rail. Their dock tabs remain available.

The shared tab strip is exposed as a tab list and its window as the selected tab's panel. A floating window retains the normal non-modal dialog semantics. Tabs in a rail have full accessible names and tooltips even when their visible names are hidden.

## Restorable state

The arrangement of windows is state the reader can return to, as chapter 2 requires and chapter 7 describes. An implementation MUST be able to restore all of it.

- Which windows are open, and the order they were opened in, which is the dock of open windows' order.
- Which window is in front, including the window that comes back in front after every window was minimised.
- Which windows are minimised, and which docked windows are collapsed.
- Each window's mode: floating, maximised, snapped to a half or a zone, or docked at an edge.
- Each window's floating position and size, kept while it is maximised, snapped or docked, since that is where it returns.
- The zone of a snapped window, and the strip size of a docked one.
- The selected window, shared width and automatic, open or rail preference of each shared side dock.

A window sized by its content restores its position only, since its size comes from its content each time.

Positions, sizes and zones are held as shares of the inner area, and strip sizes as shares of the workspace, so an arrangement restores sensibly in a workspace of another size. A parent's relation to its children belongs to the content, and is not part of the arrangement.

Whether a window menu, layout picker or rail slideout is open, and any drag under way, are momentary and are not restored.

## Accessibility

A window is exposed as a dialog that is not modal, named by its title, except while it is a tab panel in a shared side dock. Its title bar has an accessible name that carries the title and then says what the keys do: that the arrow keys move the window, that Shift with them resizes it, and that Enter maximises or restores it. Each window button has a name that says what pressing it will do now, such as Maximise or Restore, and SHOULD show it as a tooltip. The dock of open windows is exposed as navigation named "Open windows", each tab is named by its window's title, a minimised window's tab says in its tooltip that it is minimised, and the current tab is exposed as current. Each zone of the layout picker is named in words, such as "Top left quarter", each layout is a group named for it, and the zone the window fills is exposed as current. A content command that switches something on and off is exposed as pressed or not pressed.

Every word the implementation writes, the buttons' names, the title bar's name, the commands and the zones, SHOULD come from the application where it gives them, so they reach the reader in the reader's language.

In the platform's high-contrast mode the frame, the title bar, the body, the window buttons and the dock's tabs each keep a 1px border in the system's text colour, and the zones of the picker a border in the system's button text colour. The window in front takes a 2px border in the system's highlight colour, and its title bar, the current tab of the dock and the picker's current zone take the system's highlight colours. The outline of where a window will land is bounded in the highlight colour.

A printed page with windows open carries the window in front as its content, its title and body without the frame or buttons, and leaves out the other windows, the dock of open windows and whatever lies under the windows.

## Questions this section must settle

- What a window becomes on a phone. The web implementation shows one pane at a time, with the windows as the detail, but that answer is not yet written down as a rule.
- Whether the layout picker's opener on the maximise button, which a mouse resting there for half a second summons, is part of the language, or a pointer convenience a platform may leave out, given that the window menu already carries the picker.
- Whether the reader must be able to dock a window at every edge. The reader can dock only at the bottom today, by dragging or by the dock button; the other three edges are reached only by the application.
- Whether minimising every window collapses docked windows too, as the web implementation does today, or leaves the workspace's frame as it is.
- How focus is drawn on a zone of the layout picker. It is a 2px outline in `accent`, where every other control takes the 3px `focus-ring`.
- Whether the active window's title bar, the window shadows and the drag outline become tokens of chapter 3. The web implementation lets a theme set the active title bar's four colours directly, while chapter 3 says a theme tunes elevation only through the palette.
- Whether a window's position mirrors in a right-to-left interface. The web implementation measures positions from the left of the inner area whatever the direction, because they are coordinates in its address, which is a reason of the web's rather than of the language's.

## Conformance checklist

1. A floating window has a `surface-alt` frame with a `raise-border` hairline, a 5px band, corners of `radius` and a soft shadow, and is never smaller than 320px by 200px unless the inner area is.
2. Its title bar is raised, at least 38px tall, with its title at `text-md` and weight 700 on one line.
3. Its buttons are raised circles 24px across, with Close last, and their names follow the window's state.
4. At most one window is in front, and it is marked by its frame, its shadow, its title bar and its tab in the dock of open windows.
5. A press in a window, or focus moving into it, brings it in front, and a window brought forward takes the keyboard, on the element that last had focus in it, or else on an element marked to take focus first, or else on its title bar.
6. Dragging the title bar moves the window, and a floating window stays inside the inner area.
7. A floating window resizes from every edge and corner, and a maximised, snapped or docked window does not resize from its frame.
8. A drag ending at a side snaps to that half, at a corner to that quarter, at the top maximises, and at the foot of the workspace docks at the bottom, with an outline showing where it will land.
9. A double-click on the title bar maximises or restores the window, or undocks a docked one.
10. With the title bar focused, the arrow keys move the window, Shift with them resizes it, Enter maximises or restores it, and the context-menu keys open the window menu.
11. The window menu holds the window's own commands, then the content's, then Close, and reaches every command the title bar has.
12. The layout picker offers halves, quarters, thirds and the two arrangements of two thirds with one third, each zone named in words and reachable by keyboard, with the zone the window fills drawn pressed in, filled with `accent` and exposed as current.
13. A zone of the layout picker has corners of `radius-xs`, and is drawn pressed in while it is pressed.
14. A snapped window fills its zone, follows it as the inner area resizes, and restores to floating.
15. A docked window takes its strip from every other window, is flush with a hairline on its free edge, has a 30px title bar and no maximise button, and nothing covers it.
16. A docked window resizes along its free edge only, between its title bar and 80% of the workspace, and its free edge carries the `grip` glyph at rest.
17. Minimising a docked window collapses it to its title bar in place.
18. An edge with several docked windows shows the one most recently in front.
19. On a workspace 640px wide or less, a side dock shows at the bottom.
20. The dock of open windows has a tab for each top-level window, in opening order, with the `circle` glyph for a window that shows and the `ring` glyph for one that is minimised.
21. The tab of the family in front is drawn pressed in and exposed as current.
22. Pressing a tab brings its window forward, or minimises it when it is already in front.
23. A child stacks above its parent, moves forward and is hidden with it, closes with it, has no tab of its own, and closes on Escape when in front and focus is not in a text field.
24. Escape never closes a top-level window.
25. A window opened from a link inside another window opens in that window's state.
26. Closing a window returns focus to what opened it, or to the window now in front.
27. Every item listed under Restorable state is restored.
28. The window is exposed as a non-modal dialog named by its title, or as a tab panel while in a shared side dock, and the dock of open windows as navigation with its current tab exposed.
29. In high-contrast mode window frames and buttons keep their borders, and the window in front and the current tab take the system's highlight colours.
30. A window sized by its content takes its content's width and height and follows them as they change, larger and smaller, with its top-left corner fixed.
31. A window sized by its content stops at the right and bottom of the inner area, where its body scrolls.
32. A window sized by its content cannot be resized, maximised, snapped or docked by any route, and its window menu offers Reset position.
33. A window sized by the reader with limits cannot be made smaller or larger than them by dragging, by the keyboard or by restoring an arrangement.
34. The window menu's Dock list names Top, Bottom, Left and Right, ticks the edge the window is docked at, docks the window at the edge chosen, and on a docked window ends with Undock.
35. Shared side docks show one mounted window per side, selected through a full-width tab strip.
36. Required windows remain available through closing, replacement and arrangement restoration, have no close affordance, and precede other dock tabs.
37. Automatic shared docks become icon rails at the configured threshold, while explicit open or rail preferences survive resizing and restoration.
38. Rail slideouts overlay other windows, retract when work moves elsewhere, and return focus to their tab on Escape. Pinning keeps the dock open.
39. Shared dock tabs support arrow keys, Home, End, Enter, Space and Delete, and respect a window's refusal to close.
40. Status changes update dock tabs, rails and taskbar without replacing content or losing focus.
41. Shared docks restore one width for all their tabs, including after the dock becomes empty.
42. Pinned shared docks omit title bars and provide tab menus, with the selected tab connected to its content.
43. A permanent side panel stays in a left or right dock, omits its title bar even in rail slideouts, and offers only applicable placement commands.
44. An application can omit docked windows from its taskbar while preserving their dock tabs.
