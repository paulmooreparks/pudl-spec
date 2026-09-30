# 1. Introduction

PUDL is a design language for software people use to get work done: applications, tools, dashboards and the sites that sit beside them. I built it as an answer to flat design, which stripped out the cues that tell a person what can be pressed, what can be typed into and what can only be read. PUDL puts those cues back and gives each of them exactly one appearance, so the cues mean the same thing in every application that uses it.

This specification states the language independently of any platform. It says what a raised control is and when a component must use one; it does not say how a stylesheet or a XAML style draws it. A statement belongs here if it would still be true in a desktop application or a terminal. A statement that only makes sense on one platform belongs to that platform's implementation.

## Terms

The key words MUST, MUST NOT, SHOULD, SHOULD NOT and MAY are to be read as described in BCP 14 ([RFC 2119](https://www.rfc-editor.org/rfc/rfc2119) and [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174)) when, and only when, they appear in capitals.

An **implementation** is a body of code that lets applications on one platform use PUDL, such as the web implementation's stylesheet and scripts. An **application** is software built with an implementation. A **reader** is the person using an application, whether they read, type, point or listen.

A **px** is a logical pixel, the unit a platform lays out in before it scales for the display: the CSS pixel, the device-independent pixel of Windows, the Android dp and the Apple point.

## Conformance

An implementation conforms to a version of this specification when every component it offers meets that version's requirements for the component, and the tokens it offers are the ones chapter 3 defines. An implementation MAY leave components out, and says which it offers; it MUST NOT offer a component under a PUDL name that behaves differently from the one specified here.

Each component chapter ends in a conformance checklist of observable behaviour, and chapter 10 gathers them. An implementation shows it conforms by testing against the checklists and publishing the results.

## Versions

This specification and each implementation are versioned separately, each by [Semantic Versioning](https://semver.org/). The specification's version changes when the language does: a new component, a new rule or a changed token role. An implementation's version changes when its own interface does, and each of its releases states the version of the specification it implements.

Before 1.0 a minor version of the specification may change a requirement. From 1.0 on, only a major version may.
