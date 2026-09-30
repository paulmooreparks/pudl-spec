# Trees and path bars

A tree shows a hierarchy of places, such as folders or nested categories, and lets the reader open its branches and go to any place in it. A path bar shows where the reader stands inside a hierarchy they are browsing, as the list of places above the current one. The two often sit together, a file manager's folder tree beside the path of the folder in view, and each works without the other.

Every node of a tree and every entry of a path bar is a place with an address of its own, so going to one is navigation, and the reader can come back to it or hand it to somebody else as chapter 7 describes.

## Anatomy

### Trees

A tree is a list of nodes, and a node that has children holds a nested list of them, indented 16px (`space-4`) from its parent. Each node is one row. The row holds a toggle, or an empty space the same size where the node has no children, followed by the node's name. The name is set in the interface face at `text-sm`, with a line height of 1.5, in `text`, on one line. The row has 3px of padding above and below, 6px at its start and 10px at its end, and 6px between the toggle and the name.

The rows are flat, as the rows of a list are, because each is a place to go. The row for the current place has a fill of `surface-alt`, a 3px edge in `accent` on its end side, and its name in weight 700.

The toggle is a small raised button, because pressing it opens or closes the branch. It is a 16px square with 4px corners, filled with `raise-grad`, bounded by a 1px hairline in `raise-border` and shadowed with `raise-shadow`. It holds the caret glyph at 10px in `text-muted`. While the branch is closed the caret points toward the end of the reading direction, and while it is open the caret points down.

### Path bars

A path bar is an ordered list of places, from the top of the hierarchy down to the place in view. Every entry but the last is a link to its place, drawn as any link is, underlined. The last entry is the current place. It is set in weight 700 in `text` and is not a link, because the reader is already there.

The entries are set at `text-sm`, 2px apart, and separated by the slash glyph at 12px in `text-muted`, drawn with 1px either side of it. Each entry has 2px of padding above and below and 3px either side, and grows no wider than 16 times its text size, ending in an ellipsis when its name is longer. When the entries outrun the width, the list wraps onto further lines. A path bar that shows file paths sets its entries in the monospace face, `mono`.

A path bar belongs only to a hierarchy the reader browses, such as a file system. An application MUST NOT use one as a breadcrumb trail for its own sections, which are its section tabs, or as the way back from a record to its list, which is the record's back link.

## States

| State | Appearance |
|---|---|
| A node at rest | Flat, with no fill |
| A node under the pointer | Filled with `surface-alt` |
| A node focused from the keyboard | A 3px ring in `focus-ring` drawn inside its row |
| The current node | Filled with `surface-alt`, with a 3px `accent` edge on its end side and its name in weight 700 |
| A toggle at rest | Raised, with the caret in `text-muted` |
| A toggle under the pointer | The fill becomes `raise-grad-hover`, the border `raise-border-hover` and the caret `text` |
| A branch closed | Its children are not shown, and its toggle's caret points toward the end of the reading direction |
| A branch open | Its children are shown beneath it, and its toggle's caret points down |
| The current entry of a path bar | Weight 700 in `text`, and no link |

The current node never rests on colour alone, since its edge and its weight mark it as well as its fill.

## Interaction

### Trees

A tree is one stop in the keyboard's tab order. The stop is on the current node when that node is showing, and otherwise on the first node. Once the tree has focus, these keys move within it.

- Down and Up move focus to the next and the previous node showing.
- Right opens a closed node, and on an open node moves focus to its first child.
- Left closes an open node, and on a closed node or one without children moves focus to its parent.
- Home and End move focus to the first and the last node showing.
- Enter goes to the focused node's place.
- A printable character moves focus to the next node showing whose name starts with it. Characters typed less than 700ms apart join into one search, so the reader can type the start of a name. The search wraps around from the last node to the first.

Right and Left are mirrored in a right-to-left layout, so that the key pointing toward the children opens a node there as well.

Moving focus does not go anywhere. The reader goes to a place by pressing Enter or by pressing the node's name with the pointer. Pressing a toggle opens or closes its branch and moves focus to its node, without going to the node's place.

Each time a node opens or closes, the tree tells the application, which may remember which nodes are open, or fill in a branch's children as it opens. A tree MUST take in nodes the application adds after it first appears, giving them the same behaviour as the rest.

### Path bars

Each linked entry of a path bar is a link, a stop of its own in the tab order, and pressing it goes to its place. A path bar has no other behaviour.

## Accessibility

A tree is exposed with the tree role and an accessible name, such as "Folders". Each node is exposed as a tree item with its name and its level in the hierarchy, and a node with children is also exposed as expanded or collapsed. The current node is exposed as the current page. A node's toggle is not exposed, because the tree item's expanded state already carries what it shows, and the keyboard reaches the same action through Right and Left.

A path bar is exposed as a navigation region with an accessible name, such as "Location", holding an ordered list of its entries. The current entry is exposed as the current location. The separators are drawn and are not exposed, so assistive technology hears the list of places and nothing between them.

In the platform's high-contrast mode, the current node takes the system's highlight colours, a toggle keeps a visible border, and the toggle's caret and the path bar's separators are drawn in the system's text colours so that they still show.

## Questions this section must settle

- Whether which nodes of a tree are open is part of the restorable state of chapter 7, or a convenience the application may keep or drop. The web implementation reports each opening and closing to the application and keeps nothing itself.
- Whether a tree may also be a tree of choices, whose nodes are selected rather than gone to, as rows to choose from are, and if so how a selected node is drawn and exposed.
- What a branch shows while the application fills in its children, and how that is announced.
- Whether a toggle 16px square is a large enough target for touch, which depends on the minimum target size chapter 6 has yet to set.
- Whether a path bar too long for its width keeps wrapping, as it does today, or folds its middle entries into one that opens a menu of them.

## Conformance checklist

1. A tree's nodes are flat, and the current node has a `surface-alt` fill, a 3px `accent` edge on its end side and its name in weight 700.
2. Each node with children has a raised toggle whose caret points toward the end of the reading direction while it is closed and down while it is open, and each node without children keeps the toggle's space empty.
3. A tree is one stop in the tab order, on the current node when it is showing and otherwise on the first node.
4. Down, Up, Home and End move focus among the nodes showing, without going anywhere.
5. Right opens a closed node or moves into an open one, and Left closes an open node or moves to the parent, both mirrored in a right-to-left layout.
6. Typing the start of a node's name moves focus to the next node showing whose name starts with it.
7. Enter, or a pointer press on a node's name, goes to that node's place, and a pointer press on a toggle opens or closes the branch without going there.
8. A tree is exposed as a tree, each node as a tree item with its level, each node with children as expanded or collapsed, and the current node as the current page.
9. A path bar lists the places from the top of the hierarchy down, each but the last a link, and the last, the current place, is not a link and is exposed as the current location.
10. A path bar's separators are drawn glyphs and are not exposed to assistive technology.
11. A path bar's entries wrap onto further lines rather than widening the view.
12. In high-contrast mode the current node, the toggles and the separators stay visible.
