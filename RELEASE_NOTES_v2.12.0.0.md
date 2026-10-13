Legends that keep their order, goodness of fit for every fit, plot stacking with variable spacing, proxy support and an update check, and a much more capable X-Kiran.

## Legends
- **The legend now always follows the plot order.** Restyling a curve, renaming an entry, converting a plot type, adding error bars, Recalculate and save/reopen no longer reshuffle it. **Re-order Plots** works on any open graph and stays put afterwards.
- Fixed along the way: a Bar chart got one legend entry per bar after any restyle; an error-bar curve left a ghost duplicate entry after a restyle or deletion; clearing the legend box in Style deleted the entry; Recalculate overwrote a name you had typed; Edit Legend could not reopen a legend whose entries were all hidden; a restyled curve jumped in front of the others; Copy Legend lost the order; a Line converted to Scatter reopened with invisible markers.

## Fitting
- **Every fitting routine reports the same goodness-of-fit statistics** — R², adjusted R², RMSE, reduced χ², AIC and BIC — plus a standard error for every parameter: Curve Fitting Wizard, Global Curve Fit (which reported none before), Peak Deconvolution, the Nonlinear Fitting Wizard and the fits inside the WHH/G-L, Tauc, I-V, Pattern Search, THz-TDS, RF/Microwave and X-Kiran plugins.
- Each has a remembered tick box **Save parameters and goodness of fit to a sheet**, which adds them to the project.

## Plots
- **Y-Offset (Cascade Plots)** stacks curves with a fixed step, an **automatic no-overlap spacing** that adapts to each curve's height, or a **custom gap for each pair**.
- The **Zoom Box** tool shows a magnifying-glass pointer.

## Network
- **Tools > Network / Proxy Settings...** — a proxy server for every online feature, with an optional saved password (encrypted for your Windows account), a certificate file for proxies that inspect HTTPS, and a Test connection button.
- **Help > Check for Updates...** — asks once whether to check daily; it only reads the latest version number and never downloads anything.

## X-Kiran
- **COD search rebuilt:** pick the COD server (mirrors included), search by up to 8 elements, excluded elements, exact element count, formula or text, and choose from every match. It previously could not find anything.
- **CIF library:** every CIF you load or download is kept and can be loaded again offline (Tools > CIF Library...).
- **XRR:** optical constants from the Henke tables at the real wavelength (anomalous dispersion included); type any compound formula and density in a layer; density lookup from COD; its own wavelength; repeated multilayers (repeat rows × N); optional density refinement; uncertainties on every fitted value; a global search that really searches.
- **Extinct reflections** (space-group and atom-position absences) are identified and hidden by default from ticks, tables, reports and exports; a Le Bail fit no longer gives them intensity.
- **Size-Strain Plot (SSP) fix:** its strain was the *apparent* strain η, four times the microstrain ε that the Williamson–Hall UDM reports, so SSP looked four times more strained than UDM for the same sample. It now reports ε, with η shown beside it. SSP is now checked against exact Voigt peak breadths. A size or strain that does not follow from a Williamson–Hall fit is shown as "not resolved" with the reason, instead of "nan".
- **Export Graphics...** for the XRD and XRR plots, choosing the components (observed, calculated, difference, background, phases, reflection ticks, hkl labels...), size, DPI and format (PNG, TIFF, JPEG, SVG, PDF, EPS). The calculated reflection ticks are also exported with the curves and sent to the project.

## Everything else
- **SVG and EPS export now work in the installed app.** Export Graph, Batch Export and the X-Kiran and IR-FEL exports to SVG or EPS failed in the installed program (they worked only when run from source), because the installer left out the part of the plotting library that writes those formats. Every build is now checked from inside the installed program before release.
- Projects saved by earlier versions open unchanged.
