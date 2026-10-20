# 1. Introduction

PUDL is a design language for software people use to get work done: applications, tools, dashboards and the sites that sit beside them. I built it as an answer to flat design, which stripped out the cues that tell a person what can be pressed, what can be typed into and what can only be read. PUDL puts those cues back and gives each of them exactly one appearance, so the cues mean the same thing in every application that uses it.

This specification states the language independently of any platform. It says what a raised control is and when a component must use one; it does not say how a stylesheet or a XAML style draws it. A statement belongs here if it would still be true in a desktop application or a terminal. A statement that only makes sense on one platform belongs to that platform's implementation.

## Agents

PUDL is meant to be used by software agents, such as an AI model working for the reader, as well as by people, and every part of it is designed with both in mind. Where a part of the language gives a reader something to find out or to do, it SHOULD give an agent the same, by a documented and structured means that does not depend on reading the screen: what is there, what state it is in, and how to act on it. The applet contract in chapter 9 is the model: an applet's state is a string any caller can read and give back, its requests are verbs any caller can make without knowing which applet answers, and its actions can be listed and called with their input and output checked against schemas, under capabilities the reader grants. The restorable state of chapter 7, held in an address, serves an agent as it serves a reader returning to their work.

Not every part has a side for agents. A rule about appearance, such as how a raised control is lit, has none, and a part is not given one for its own sake. Where a part does have one, it is specified with the part, in its own chapter.

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
