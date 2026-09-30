# Dialogs

A dialog interrupts the reader to ask a question or take a short input before a task goes on, such as confirming that unsaved changes should be discarded. It is modal, so while it is open the reader can act only inside it, and it closes with an answer. Content the reader might want to come back to or send to somebody else belongs in a page or a window of its own, where it has an address.

## Anatomy

A dialog is a panel lifted above the view, over a backdrop that dims everything behind it. The panel is filled with `dialog-bg`, which makes it one step brighter than the page it sits on, bounded by a 1px line in `border`, and has `radius` corners and 24px (`space-5`) of padding. It casts `shadow-dialog`, which is a card's shadow with a deep soft shadow of `shade` added, 24px below the panel and blurred over 64px, at 1.8 times the strength `depth` sets, and that deep shadow does the work of lifting it. The backdrop is `backdrop`, which is `shade` at 40% opacity and dims the view gently. Both are derived tokens, so a theme's lighting reaches them.

The panel is centred in the window. It is as wide as the window allows up to 480px, and no taller than the window less 24px above and below; when its contents are taller it scrolls.

A dialog holds, from top to bottom, these parts.

- **A title**, which asks the question or names the task, such as "Discard unsaved changes?". It is set at `text-lg` and weight 700, in `text`, with 8px (`space-2`) below it.
- **A body**, which says what the choice means, set at `text-md` with a line height of 1.55, in `text-muted`, with 24px (`space-5`) below it. The body MAY hold fields, when the dialog takes a short input.
- **Actions**, a row of buttons at the end of the panel, 8px (`space-2`) apart. The action that leaves things as they were comes first, and the action that commits comes last, at the end.

A dialog is a visible context, so it holds at most one primary button, as chapter 2 requires. When the committing action destroys something or cannot be undone, it is a danger button, leading with the warning glyph, and the dialog holds no primary button. Each action's label says what it does, such as "Stay" and "Discard changes", so the reader can answer without reading the body.

## States

| State | Appearance |
|---|---|
| Closed | Nothing is drawn |
| Open | The backdrop dims the view, and the panel sits above it, centred |

The dialog's buttons have the states the buttons section specifies.

A toast raised while a dialog is open appears inside the dialog, above its backdrop, where the reader can read and dismiss it. When the dialog closes, the toast moves back to the page's toasts. The section on notices and toasts specifies the toast itself.

## Interaction

Opening a dialog moves focus into it. Focus SHOULD land on the action that leaves things as they were, or on the first field when the dialog takes an input, so that a reader who presses Enter without reading does no harm.

While a dialog is open, the tab order covers only the dialog's own controls, and nothing behind the backdrop can be pressed, focused or reached by assistive technology.

Pressing an action closes the dialog, and the application learns which action closed it. Escape asks the dialog to close without an answer, as the action that leaves things as they were would. The application MAY refuse that request, for example while the dialog holds input that would be lost. When a dialog closes, focus returns to the control that opened it.

## Accessibility

A dialog is exposed with the dialog role, as modal, and with its title as its accessible name. Its body MAY be exposed as its description. Everything behind the backdrop is hidden from assistive technology while the dialog is open.

In the platform's high-contrast mode the panel keeps a visible border, since its shadow will not show there.

## Questions this section must settle

- Whether a press on the backdrop closes the dialog, as Escape does. The web implementation does not close it, so a stray press cannot lose an answer, and some platforms' conventions do close it.
- Whether a dialog that is open is part of the restorable state of chapter 7. Today a dialog is shown by the application in response to an action, and reloading the view closes it.
- Whether an application on a desktop platform may use that platform's own message box instead of a PUDL dialog. The web implementation forbids the browser's equivalent, which cannot be styled and cannot name its buttons in the application's words, and a desktop message box shares only some of those faults.
- What a dialog becomes on a narrow window, whether it stays a centred panel as it does today or fills the window as a sheet.

## Conformance checklist

1. A dialog's panel is filled with `dialog-bg`, has `radius` corners, casts `shadow-dialog`, and sits centred above a `backdrop` that dims the view.
2. The panel is no wider than 480px and scrolls when its contents are taller than the window allows.
3. The title is `text-lg` at weight 700, and the actions sit at the end, with the committing action last.
4. A dialog holds at most one primary button, and none when its committing action is destructive.
5. Opening a dialog moves focus into it, and while it is open nothing behind it can be pressed or focused.
6. Escape asks the dialog to close, and the application can refuse.
7. Pressing an action closes the dialog and tells the application which action it was.
8. Focus returns to the control that opened the dialog when it closes.
9. A dialog is exposed as a modal dialog named by its title, and everything behind it is hidden from assistive technology while it is open.
10. A toast raised while the dialog is open appears inside the dialog, above its backdrop, can be read and dismissed there, and moves back to the page's toasts when the dialog closes.
11. In high-contrast mode the panel keeps a visible border.
