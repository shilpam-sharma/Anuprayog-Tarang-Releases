Fixes the X-Kiran Export Graphics button, adds Veusz-like graph styles and colour palettes, stacks plots from a reference plot, and sends X-Kiran reports to the project Notes.

## Fixed
- **X-Kiran Export Graphics did nothing in the installed program.** The Export button silently failed for every image format; it now saves PNG, TIFF, JPEG, SVG, PDF and EPS, and any problem saving is reported instead of ignored.
- **A new plot could replace an existing graph.** After closing a graph other than the last one, the next Quick Plot reused the name of an open graph and replaced it instead of opening a new pane. New graphs now always get an unused name.

## New
- **Typography before export** in X-Kiran: font family, base size, title / axis label / tick / legend / hkl label sizes, bold and italic, with a live preview; the last settings are remembered.
- **X-Kiran reports go to the project Notes** instead of data sheets: the XRD refinement report (lattice constants with uncertainties, R factors, phase quantification, reflections), the XRR layer report (thickness and roughness with uncertainties, density, statistics) and the size/strain report. Each send adds a dated block and never overwrites your notes.
- **Stacking plots from a reference plot.** Y-Offset (Cascade Plots) now has a **Reference plot**: it keeps its true Y values and every other plot is separated from it (fixed step, automatic no-overlap spacing, or a custom offset for each plot). The original step-between-consecutive-plots mode remains, and the Plot dialog's own Y-Offset is unchanged.
- **Plot > Series Style Defaults** chooses how each new series is drawn: a distinct symbol for each series (default), thin lines with small markers, a Veusz palette with outlined markers, or the previous look.
- **Plot > Graph Frame Style**: a Veusz-like frame (full box, inward ticks on all four sides, thin lines, serif fonts) for the active graph or for every new graph.
- **Colour palette in every colour dialog**: matplotlib's default colours (the default blue first), Veusz's 16 palette colours and the usual basics.

Projects saved by earlier versions open unchanged.
