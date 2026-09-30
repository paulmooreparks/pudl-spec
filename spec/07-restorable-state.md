# 7. Restorable state

Status: not yet written.

This chapter will say what a reader must be able to leave and come back to, and hand to somebody else: the windows they have open and where, the record in view, a filter in force, the tab they chose. It will say what each implementation must restore, and leave how to the implementation. The web implementation keeps all of it in the address, as its architectural principles require. A desktop implementation might keep it in a session file, or in a link its application can open.

Questions this chapter must settle:

- Which state is the reader's own and which belongs to the application, such as a sidebar's width.
- Whether restorable state must also be shareable on every platform, as it is on the web, or only restorable.
