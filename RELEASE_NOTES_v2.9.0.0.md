A feature release: new ways to get data in, new things to do with an axis, a guided way in for new users, and a template for writing your own plugins.

## New

**Write your own plugins, starting from a worked example.** *Plugins > New Plugin Template (worked example)...* is a plugin that runs *and* the file you copy to start your own. It reads the datasets and graphs already in your workspace, runs a calculation on a column you pick, and then hands the result back four different ways — as a new dataset, as a new graph, overlaid onto a graph you already have open, and as a restyle that adds no data at all — with a button for each. A **How** tab shows the exact code for every route, and *Save a copy to edit...* writes the whole commented file wherever you like.

**An interactive tutorial.** *Help > Interactive Tutorial* walks through the whole loop — import, designate column roles, plot, label, analyse, export — one step at a time. It is not a slideshow: each step watches the application and ticks itself off once you have actually done the thing, so you can follow along exactly or get there your own way. Every step also offers "Do it for me".

**FITS and HDF5 import** (*Plugins > Import FITS / HDF5...*). Both are containers holding many named arrays and tables, so it lists what is inside — walking HDF5 groups recursively — and you tick what you want; each becomes its own dataset, named after the entry. 2-D arrays can be read either orientation, tables keep their own column names, and complex arrays split losslessly into real and imaginary columns.

**Dates and text columns now survive import, and can be plotted against.** Import used to force every column numeric and quietly drop whatever would not convert, so a timestamp column or a column of sample names never reached the sheet. Now a text X gives a categorical axis (the strings become the tick labels) and a date X gives a real calendar axis. Date parsing is deliberately cautious: a column only becomes dates if most of it actually parses, so one date-shaped value in a column of labels leaves it as text.

**Linked axes across a panel grid** (*Graph > Axis Behaviour > Link Axes Across Panels...*). Zooming or panning one panel moves the others, in X, Y or both — for small multiples that have to stay comparable.

**Functional (linked-scale) axes** (*Graph > Axis Behaviour > Add Functional Axis...*). A second axis whose scale is a function of the first, so one curve can be read in two quantities at once: wavelength along the bottom and photon energy along the top, or 2θ against d-spacing. Presets for nm↔eV, nm↔cm⁻¹, °C↔°F, or type your own expressions.

**Ginzburg-Landau fitting for Hc2(T)**, alongside WHH, in the upper-critical-field plugin — and **the fitted curve now extrapolates to T = 0 K** instead of stopping at your lowest measured point. Hc2(0) is the number that analysis gets quoted for and it is essentially never measured directly; drawing the curve only across the measured span left that extrapolation invisible. Hc2(0) is now marked on the graph, and the fit says when it was made in the orbital limit (α and λ_so held at zero), because that assumption reads Hc2(0) high on Pauli-limited data while still showing a high R².

**Watched folders can plot into one shared graph panel** instead of a new panel per file — right when the files are repeats of the same measurement. **Live Data gains X/Y axis labels**, falling back to the column names.

**JPEG export**, alongside PNG/PDF/SVG/EPS.

**Analysis honours the selected Data Range, and you can switch that off.** Curve Fit and Baseline Subtractor now respect an active range like the other operations do, and *Interact > Analysis Uses Data Range* lets a range stay on the plot as a marker while operations run over the whole trace.

**Drag can move only the points inside the Data Range**, for shifting one region of a curve without cutting it out into its own dataset first.

**About shows the splash artwork.**

## Fixed

**Axis break marks were effectively invisible, and misplaced.** The slashes and the gap cut into the spine were sized in *data* units while written as if they were axes fractions, so on a typical axis they collapsed to sub-pixel hairlines; they were also pushed through the break transform twice, landing beside their own gap rather than in it. Both fixed — the marks now render at a constant visual size whatever the data range, centred on the break.

**Two or more axis breaks displaced everything below the first one.** With breaks at [10,20] and [50,60], a value at x = 5 was drawn at −3. A single break was correct, which is why this went unnoticed.

**A text column is no longer auto-designated as a Y series.** It could be, once text columns started surviving import — and plotting one drew an empty graph with no error. The first column is still tagged X whatever its type, since a text X is exactly the categorical-axis feature.

## Everything else

Unaffected. Projects saved by earlier versions open unchanged, including the legacy `.anu` format.
