IR-FEL Absorptance reports the absorption in the film and the substrate of the measured sample, and every series - plotted, dragged, computed or fitted - now takes the look chosen under Plot > Series Style Defaults.

## IR-FEL Absorptance (film / bulk)
- **The absorption in the sample is the primary result**: the fraction of the incident beam absorbed in the film and in the substrate of the measured sample, over all passes and for either beam direction (T + R + A film + A substrate = 1). The free-standing film's absorptance and the one-pass absorptance in the stack are still reported beside it. The film's absorption coefficient, and the substrate's k and absorption coefficient (from an entered substrate thickness), are added.
- **The optics are consolidated to two**: the coherent film on an incoherent substrate (the default, either beam direction), and the film as an interface with the beam through the substrate. The incoherent film-first layers, the simple ratio and the film transmission taken as a ratio to the bare substrate are removed.
- **The coherent optics are the default**, and the film thickness has to be entered (there is no default thickness).
- **(n, k) branch**: where several (n, k) reproduce the measured T and R, the branch follows an expected value at the first wavelength and continuity between wavelengths; a wavelength without an exact solution no longer seeds the next one. The absorption in the sample does not depend on the branch.
- The report flags results against the measured uncertainty.
- Fixed: **Plot film, substrate and film + substrate** plotted nothing with the coherent optics; the calculator misread a text file whose columns are separated by two tabs (a transmittance column read as empty and every later column shifted).

## Plot styles
- **Classic Scientific Frame for New Graphs** (Plot > Graph Frame Style) is now on by default; untick it for matplotlib's standard frame.
- **New: Line Plots with Symbols** (Plot > Series Style Defaults, on by default): every new line plot carries the chosen style's symbols - a different shape per series for *Distinct symbol for each series*, outlined circles for *Thin lines* and *Palette with outlined markers*, matplotlib's circle for the previous look. Untick it and lines are drawn without symbols, in every style.
- **The series style now reaches every new series**: columns dragged onto a graph (one or several, onto a graph with curves or an empty one), Quick Plot of several columns, Live Data, derivatives, integrals, smoothing, filters, Plot Arithmetic, FFT, the Flowchart's result, fitted curves (Curve Fitting, Global Fit, Peak Fitting's graph) and the result graphs of the WHH, Tauc, Kramers-Kronig and Advanced FFT plugins. Before, a dragged column or a computed result was drawn as a plain line or circle whatever the style. A result placed in a new graph also gets the default frame.
- **Fitted curves** are drawn dashed in the series style, with about 20 symbols spaced along the curve rather than one at each point of the fine fitting grid. A new series takes a colour that no series on the graph already has, so a fit no longer comes out in the colour of the data points it fits.
- **Palette with outlined markers**: 6 pt markers (were 3.5 pt), and scatter plots now get the dark outline that line plots have (so do *Thin lines* scatters). The outline, and a marker's outline width, are kept by the Style dialog and by save and reopen. A hollow (Open) marker is outlined in its series colour unless an edge colour is picked.
- Fixed: a column dropped onto a curve with error bars was drawn as a bar chart, and one dropped onto a horizontal bar chart as vertical bars; Global Fit's curves were missing from the legend; a scatter copied into a ROI zoom inset lost its symbol and size (a hollow one came out filled blue); the Style dialog read a hollow scatter's colour as blue; WHH's Hc2(0) marker reopened as a filled circle.

## Notes
- This release includes everything in 2.17.0.0.
- Graphs you already have, and anything set in Style, are not restyled. Projects saved by earlier versions open unchanged.
- A line through many data points carries a symbol at every point; **Style > Skip N Points** thins them out, or untick Line Plots with Symbols.
- Plugins can draw their results in the series style through `_anu_plugin_api.add_series` (see the plugin template).
