# Selection actions and margin notes

Selection actions offer explicit raised buttons beside a nonempty selection inside one content scope. A selection crossing scopes MUST NOT offer actions. Pointer and keyboard activation MUST retain the selected passage for the action. The offer sits near the final selected line, constrained to its content and visible viewport, and wraps when necessary. Escape dismisses it without consuming the key. The application owns each action, permission check and persistent passage identity.

Margin notes are flat content aligned beside passages, with ordinary links both ways. They MUST NOT change the reading column's width or horizontal position when their presentation changes. A margin is used only when space within the component permits a 14rem note and 1rem gap beside the reading column's logical end. Notes follow anchor order and move down with at least half a rem between them to avoid collisions. Container changes, content growth and completed font loading update placement.

Where the margin cannot fit, notes remain after the reading content and raised numbered markers beside passages lead to them. The same note elements remain mounted. A note provides an explicit action to return focus to its passage. Missing anchors leave readable notes without misleading passage controls. Print presents notes after the reading content and omits transient controls.

Without scripting, content and notes remain readable and ordinary links provide navigation. A selection offer may remain hidden. Domain operations and storage are outside the control contract.
