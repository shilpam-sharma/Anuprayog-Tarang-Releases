# AnuPrayog: Tarang v2.22.0.0

A refinement release. It adds hiding of individual curves, a rectangular zoom
inset, one place to edit every annotation, and an automatic check for newer
versions. Drag-and-drop plotting now uses each curve's own X column.

## New

- **Hide Plot / Show Hidden Plot.** Right-click a curve and choose Hide
  Plot. Bring it back from the graph's right-click menu under Show Hidden
  Plot, or with the Show boxes in Re-order Plots. A hidden curve is not drawn, has no
  legend entry, is ignored when the axes autoscale, and stays out of exports.
  Hiding and showing take one Undo step and are saved with the project.
- **Rectangular zoom inset** (Interact > Annotate > ROI Zoom (Rectangle)). Drag
  edge or corner handles to re-frame the inset, and use the Square option to
  keep it square.
- **Data Label reads the clicked position freely.** A label can show the exact
  point you click, not only a point on a curve.
- **Annotation tool cursors.** Every annotation tool now shows an arrow with
  the tool's own icon beside it.
- **Annotation Properties lists every annotation of the graph.** It opens on
  the selected annotation, or on the first one. If you move to another row with
  unapplied edits, you are asked to Apply, Discard or Cancel. Apply takes an
  Undo step for every kind of annotation.
- **Automatic update check at startup.** AnuPrayog checks once a day, silently
  when offline, and shows a small notice if a newer version exists. It is on by
  default and can be turned off in Network / Proxy Settings.
- **Peak deconvolution sends a parameter table for each peak** to the project.
  Save to Notes is available, and the table includes FWHM/center (%), the
  FWHM as a percentage of the peak center (100 x FWHM / |center|).
- **Style dialog Source section for derived curves.** For curves made from
  derived or result columns, it shows the dataset and columns they came from,
  and says so when the source was inferred.

## Fixed

**Plotting**
- Drag-and-drop plots each curve against its own X column. Before, curves whose
  X spacing differed could be drawn against the wrong X.

**Annotations**
- Annotations are clipped to their axes on every view change and in exports.

## Help

Help pages for plotting, annotations, Network / Proxy Settings, the update
check and peak deconvolution describe the new features.
