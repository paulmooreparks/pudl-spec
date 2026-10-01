# 9. Applets

An applet is interactive content, such as a game, a calculator, an editor or a terminal, that runs unchanged wherever it is put: in a page or view of its own, embedded in a document among other content, or inside a window. PUDL does not build or manage applets. It defines the contract between an applet and whichever host it lands in, so that one applet serves every host and a host can take any applet. An implementation that offers applets MUST offer this contract.

An applet knows itself and never its host. It MUST NOT reach outside the space the host gives it, look for the window around it, or keep its state anywhere the host has not given it, except in the one case below where it owns its own place.

## Starting and stopping

A host starts an applet by giving it a space to build in and the options below, and the applet returns an instance. The host stops it by asking the instance to destroy itself, and the instance MUST then undo everything it set up, including anything it listens to outside its space and any timer it started. A host starts the applets in its content when the content appears, and destroys them when it goes, such as when a window closes, so that an application needs no wiring of its own.

## What the host tells the applet

- The host says whether the applet is inside a window.
- The host says how the applet should size itself. A host that gives a definite space asks the applet to fill it without scrolling, as a window or a page that holds nothing but the applet does. A host that gives only a width asks the applet to flow, capping its own height and letting the surrounding content scroll, as a document does. A window asks it to fill and anything else asks it to flow, unless the content says otherwise, as a document shown in a window does for an applet among its text. A window sized by its content is the exception among windows: it gives the applet no box, since the applet's own size is what sizes the window, so it asks the applet to flow.
- The host says whether the applet is on its own page, where it may keep its state in the page's own restorable state as chapter 7 describes. Anywhere else the applet MUST leave that state alone, since in a window the windows own it and in a document the document does.
- The host says where the applet's own page is, so that the applet can offer a link that reaches its current state from anywhere.
- The host gives the name this instance goes by, which is its window's name inside a window and otherwise the applet's name, so that a host can keep each instance's state apart.
- The host gives the state it kept for the applet, or a request made of it just now, as a string, or nothing.
- The host gives the applet a way to report its state, as a string, when that state settles.

## State

An applet's state is a string, and the applet defines what it means. The instance MAY offer a way to read its state and a way to be given a new one.

PUDL keeps no applet state for the applet. A host chooses whether to keep it and where. A window that should remember its game keeps the state it is told of and hands it back when the window opens again; a document that wants its embedded game shared with the document keeps the state in the document's own restorable state. An applet MUST NOT keep its state for itself anywhere but on its own page.

A link in a document MAY set up an applet in the same document or window, such as "a glider gun" in an article about the Game of Life. Following the link hands its state to the running instance instead of leaving the page, and a link with nothing to take it goes where it points, where the applet reads the same state. The applet's own-page state and the state such a link carries SHOULD therefore share one form.

## Requests between applets

Applets can ask each other for things without naming each other. An applet declares the requests it serves, each a verb, optionally restricted to kinds of thing, and how many instances of it may run at once. A caller asks for a verb and a path, optionally with a kind and further parameters, and never names an applet. The verbs and kinds are the application's own words, which PUDL routes and gives no meaning. A caller MAY ask first whether anything would serve a request, and hide the action if nothing would.

The first applet declared that serves the verb, and the kind if it lists kinds, answers. On a host with windows, the request goes to that applet's newest instance, whose window comes forward and which takes the request as a new state. With none running, or when the verb asks for a fresh instance each time, it opens a new instance in a new window while fewer than the applet's limit are running, and the new instance starts with the request. At the limit, the newest instance takes it. On a host without windows, the request goes to the applet's own page.

## Commands

An instance MAY offer commands of its own, such as Save, Word wrap or Show hidden files, each with a label, an action, and optionally whether it is switched on and whether it is disabled. The host asks for them each time it shows them, so the applet builds the list from its current state and every label and tick is true when the reader sees it. Where the application has a menu bar, the commands are the applet's front menu, under one title, its name. Without one, in a window they join the window menu, after the window's own, and outside a window the host shows them in a menu of their own, opened by a button with the `gear` glyph above the applet.

## Menus

An instance MAY offer a menu bar's front menu in full, asked afresh each time a panel opens, as its commands are. The menu is a list of titles, the first being the applet's name, each with its commands, and what the applet adds to the host's own titles, by the host title's name. A command has a label, and either an action or a list of commands making a submenu, and MAY say whether it is on, which of a named group it belongs to, whether it is disabled, whether it destroys something, and its shortcut. A list MAY hold separators and headings for the commands below them. The section on menu bars sets out the rules the menu must keep.

## Questions this chapter must settle

- Whether a request's state should survive the host restoring its windows, as the rest of an arrangement does. In the web implementation it reaches a new window through memory, so a reload keeps the window but loses the request unless the host keeps it.
- Whether an applet's instance limit belongs to the applet or to the host.
