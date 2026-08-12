AnuPrayog: Tarang v2.7.0.0 — A scientific data analysis and plotting application.

Windows installer: **AnuPrayog_Tarang_v2.7.0.0_win64_Setup.exe**.
Upgrades an existing v2.x install in place, and now offers to remove v1.0/v1.2 as well; coexists with them if you decline.

## New

**Advanced Nonlinear Fitting Wizard** (Plugins > Advanced Nonlinear Fitting Wizard) — an OriginPro-style NLFit dialog covering **all three** of Origin's nonlinear tools from one window: curve `y = f(x)`, implicit `f(x, y) = 0`, and surface `z = f(x, y)`. The layout follows Origin's, with the six settings pages (Function Selection, Data Selection, Fitted Curves, Find X/Y, Advanced, Output) under the Settings / Code / Parameters / Bounds tabs.

**121 fitting functions across 23 categories**, named and grouped from OriginLab's own documentation, so a name here means the model it means in Origin — and a function appears in every category Origin lists it under, as one shared definition. Changing the fit type re-filters the catalogue, so a surface model can never be offered to a curve fit.

Every function derives its **own starting values from your data** — a peak's amplitude and half-width read off the curve, a sine's period taken from an FFT rather than assumed, a polynomial's coefficients from a linear prefit. A nonlinear fit is only as good as where it starts.

Some models are **over-parameterised**, and the wizard says so rather than letting them mislead you. In `y0 + A1*exp(-(x-x0)/t1)` the pair `A1` and `x0` is redundant — `A1*exp(x0/t1)` is a single effective amplitude — so infinitely many parameter sets give exactly the same curve. Fitting both returns R² = 1.0000 with parameters wildly wrong, which is the worst failure there is because nothing on screen looks wrong. Those functions start with the redundant parameter held, and explain why.

An **implicit fit reports no R²**: with no dependent variable there is nothing to compare residual variance against, so the orthogonal RMSE is given instead. The solver minimises the perpendicular distance from each point to the curve, because for a circle a "vertical residual" is not defined at all.

**Delete several selected columns at once** — the worksheet's right-click Delete now follows your selection the way Cut and Copy already did.

**The Data Matrix remembers where you were.** Extracting rows used to send you to the new dataset and bring you back at row 1; each dataset's scroll position is now restored. A **pin** on the Data Matrix header stops a dataset created by an extraction taking the pane at all — choosing one from the dropdown or the explorer still works normally and moves the pin with it.

**Floating dataset windows can plot.** They carry the same 17-type ribbon and a right-click Quick Plot menu, and they plot *their own* dataset rather than whatever the Data Matrix happens to be showing.

**An icon toolbar** under the menu bar with 35 commands from File, Edit and Interact, including their submenus. The buttons *are* the menu commands, so anything greyed out in the menu is greyed out here. Hide it from Window > Show Command Toolbar.

**Graph navigation for crowded projects.** Past a dozen graphs the tabs are too narrow to read, so each pane gains a jump list at the top and previous/next arrows at the bottom with an "n of m" position, plus `Ctrl+PgUp`/`Ctrl+PgDown`. They appear only when there is more than one graph, so a single-graph project keeps its full canvas.

**Images in graphs** (Graph > Insert Image...) — PNG, JPG, TIFF or BMP. An empty panel of a grid takes the image full size, including a panel with no data plot at all; a panel that already has curves gets it as a corner inset. The picture is stored *inside* the project, so it survives the original file being moved, renamed or deleted.

**Project history records what each operation read and produced** — two new columns naming the source dataset, columns and rows, and the dataset or graph that came out.

**Auto-Backup snapshots can be deleted**, several at once or all of them, with the confirmation naming each one and the total size.

## Changed

**Axis limits smaller than the spin box's precision are no longer destroyed.** A QDoubleSpinBox rounds its stored value, so an axis running to 1.2e-7 held 0.0 and read "0.0000" — and pressing OK wrote that zero back to the axes. Limits now carry full precision and display in engineering notation (`120e-9`) outside 10⁻²–10², exact decimal within it.

**Close Project offers to save.** It deletes the project's workspace, but asked only "are you sure?" — so Yes discarded every unsaved dataset and graph without mentioning them. It now offers Save / Discard / Cancel, and a save that fails or is cancelled leaves the project open.

**The installer removes the previous build before installing**, so files dropped between releases cannot survive an upgrade, and it offers to uninstall v1.0/v1.2 if they are present. Your `.anu` files are never touched.

## Fixed

- **Plotting from a floating dataset window drew the wrong data.** "Line" re-read the Data Matrix's dataset even when the caller had resolved another, so the wrong numbers appeared under the right column names — silently, and only for that one plot type.
- **A false "recover unsaved work?" prompt after running the test suite**, and a startup deadlock where that prompt could open behind the splash screen and leave the application frozen at "Building interface...".

---

## Citing this release

```bibtex
@software{sharma2026anuprayog,
  author  = {Sharma, Shilpam},
  title   = {{AnuPrayog: Tarang}},
  version = {2.7.0.0},
  year    = {2026},
  doi     = {10.5281/zenodo.21887356},
  url     = {https://github.com/shilpam-sharma/Anuprayog-Tarang-Releases},
  note    = {Free to use, closed source. See the EULA for full terms.}
}
```

The citation above uses the **concept DOI**, which always resolves to the
newest version. A version DOI specific to 2.7.0.0 is minted by Zenodo
when this release is archived, and appears here and in the application
once it exists.

## Licence

Free to use, closed source. See the EULA for full terms. The source code is not public. See
[EULA.md](https://github.com/shilpam-sharma/Anuprayog-Tarang-Releases/blob/main/EULA.md).
