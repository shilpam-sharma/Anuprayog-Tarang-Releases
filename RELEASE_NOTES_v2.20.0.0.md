# AnuPrayog: Tarang v2.20.0.0

A usability release. It adds app-wide default fonts and colours for new graphs,
maths and symbols in every piece of graph text, rules for the Live Data watch
folder, and a round of fixes to how legends are pasted, saved and restored.

## New

- **Default Typography and Colours for New Graphs** (Plot > Graph Frame Style).
  Set the fonts, sizes, bold/italic and the text, axes and tick colours that
  every new graph starts with. The same defaults apply to legend pieces and
  Data Labels. Apply them to the graphs that are already open with one Undo
  step. Projects you saved earlier keep their own look.
- **Maths and Insert Symbol wherever you type graph text.** Titles, axis
  labels, legend entries, annotations and Data Label formats all take the Math
  option and the Insert Symbol picker, including scientific notation. The picker
  now has Superscript and Subscript buttons.
- **Legend maths in Typography's Legend tab**, and a right-click on a legend
  opens Edit Legend... for exactly that legend.
- **Data Label: show only the Y value**, with its units.
- **Live Data > Watch Folder for New Files: Exclusions & Reading Rules.**
  Skip files by exact name, keyword or extension. Give each kind of file its
  own reading rule (delimiter, rows to skip, header, X and Y columns), in order.
  Columns can be given as letters, 1-based numbers or header names, and the
  delimiter can be detected automatically. A file that has a header but no data
  yet is waited on, and a real mismatch is reported instead of plotting an
  empty graph.
- **Import several files with one set of settings.** When you import several
  files at once, "Import all files with these settings" is ticked by default:
  the Import Wizard appears once, the other files load silently with the same
  settings, and any file that doesn't fit them is listed at the end.
- **WHH / G-L Hc2(T) plugin: Min and Max bounds** for each fit parameter.
  Bounds that don't make sense are refused, and you are told when a fitted
  value ends up on a bound.

## Fixed

**Legends**
- Paste Legend puts the legend on the panel you chose, including a different
  panel, a different graph window, and a twin-axis panel. It is refused on a
  PyQtGraph graph.
- A pasted legend keeps its swatch when pasted into another window, and its
  pieces on a twin axis are saved with that axis.
- A legend's look survives Save and reopen and Undo.
- Copy Legend keeps the look the legend was drawn with.

**Windows and import**
- Window > Switch To and the Data Matrix's dataset list no longer show graphs
  and datasets from a project you have closed.

**Saving and Undo**
- Save and Undo no longer lose a 3D graph's Z-axis label.
- Undo on a twin-axis graph now also undoes a change to the tick style.
- Pressing OK on a Data Label without changing anything no longer changes its
  format.

**WHH / G-L Hc2(T) plugin**
- The parameter list is no longer squeezed after a fit, and its boxes can no
  longer be changed by accident with the mouse wheel.

**Dialogs**
- The Math wrapper for Bold and Italic is no longer shown or doubled when you
  reopen an edited text.

## Help

Help pages for Typography, Legends, Annotations, Live Data and the WHH plugin
describe the new features.
