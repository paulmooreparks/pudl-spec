# 10. Conformance

Status: begun.

This chapter will gather the conformance checklist of every component, so an implementation can be tested against one list. Each item is observable behaviour, stated so a test can check it on any platform.

| Component | Checklist |
|---|---|
| Buttons | [Buttons, conformance checklist](08-components/buttons.md#conformance-checklist) |

The web implementation's browser tests, run in Chromium, Firefox and WebKit with an accessibility audit, are its evidence of conformance. Each other implementation brings its own.

## Skin admission

Structural validation of a skin definition does not establish rendered conformance. Admission MUST cover component category assignments, relevant states and pseudo-elements, light and dark forms, text and control-boundary contrast, focus visibility, target geometry, clipping and reflow, and system-colour behavior. Runtime switching MUST retain focused elements, edited content and application state.

Standard preservation MUST compare against expectations captured before the token changes. Expectations derived from the changed tokens cannot establish preservation. Existing Standard defects MUST be recorded separately and MUST NOT waive requirements for a new skin. Each admitted skin MUST have explicit surface-treatment expectations; a universal requirement for a gradient would incorrectly reject a conforming bevel.

Release evidence MUST identify the reviewed assets and distinguish automated measurements, visual inspection, unsupported environments and manual checks not performed. A release MUST NOT claim an unperformed check passed.
