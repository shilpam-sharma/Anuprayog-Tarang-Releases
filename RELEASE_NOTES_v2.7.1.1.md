# AnuPrayog: Tarang v2.7.1.1

A patch release fixing one regression introduced in v2.7.1.0.

## Fixed

**A floating graph kept no title-bar buttons, and could not be re-docked.**

In v2.7.1.0, popping a graph out into its own window — by double-clicking
its title bar, by the Float button, or by dragging it out — left the
window with no title bar at all: no **Close**, no **Maximize**, and no
**Float/Re-dock**. The only way back was to close the application.

The cause was the v2.7.1.0 change that set out to make a floating graph
resizable. It handed the title bar back to Qt while floating, on the
expectation that the operating system's own window frame would take over
and provide edges to drag. On Windows that does not happen, so the window
was left with nothing at all.

In this release:

- **A floating graph keeps its own title bar in both states**, so
  Maximize, Float/Re-dock and Close are always available and a floating
  graph can always be brought back.
- **Resizing comes from a grip in the bottom-right corner**, which drags
  the window to size. It appears only while floating; docked graphs are
  resized by their splitters as before.
- The darker border around a floating window is unchanged, so its edges
  stay easy to see.

Everything else in v2.7.1.0 is unaffected. If you are on v2.7.1.0, this
is a recommended update; earlier versions are unaffected by the
regression.
