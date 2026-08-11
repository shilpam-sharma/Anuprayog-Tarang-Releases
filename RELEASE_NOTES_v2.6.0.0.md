Windows installer: **AnuPrayog_Tarang_v2.6.0.0_win64_Setup.exe**.
Upgrades an existing v2.x install in place; coexists with v1.0/v1.2.

## New

**Live Data now captures every column.** It used to bind one X and one Y by index and never read the rest of the file — so a logger writing a dozen channels cost you ten of them permanently, because nothing ever parsed those fields. Now **all columns land in the dataset** and the tick boxes only choose which are *drawn*; each ticked column gets its own curve and follows its own data as rows arrive. A field that won't parse blanks that one cell instead of dropping the whole row, so a timestamp string in the first column no longer costs you the numeric channels beside it.

**Watch a folder for new measurement files** (File > Live Data > Watch Folder for New Files...). Each new file that lands is offered for live plotting; answering Yes opens Live Data pre-filled with it. Files already present when watching starts are the baseline rather than discoveries, and a file is offered as soon as it holds one complete line — so a run that is *still logging* is picked up straight away, which is the whole point.

**Read LabVIEW measurement files** (Plugins > Import Instrument File):
- **TDMS** via npTDMS, with the time axis rebuilt from `wf_increment`/`wf_start_offset`
- **LVM**, including multi-segment files and the waveform form that stores only `X0`/`Delta_X` with no X column at all
- **Flattened binary waveforms** from "Write to Binary File" — one or many, big- or little-endian, DBL or SGL, each keeping its own `t0` and `dt`
- **Datalog files** (DTLG) — many records of many channels, with channel names and units read from the waveform attributes, so columns arrive labelled `Dev1/ai0 (Volts)`. Recognised by content, so a file with no extension still works.

Nothing is guessed in the binary readers: a candidate layout is accepted only if it consumes the file to the last byte, so a truncated file, trailing junk or a wrong guess is refused rather than half-read.

**Kramers-Kronig analysis** (Plugins > Kramers-Kronig) — the complex refractive index n + ik and the dielectric function from a measured reflectivity or transmittance spectrum, recovering the phase an intensity measurement discards. The extrapolations beyond your data are an explicit choice (Hagen-Rubens, ω⁻², ω⁻⁴, constant, none), because the integral runs over all frequencies and a measurement never does — that truncation is the dominant error in any real KK analysis, so it is not hidden behind a default. Transmittance takes a different route entirely, via Beer-Lambert and the k→n relation, because pushing it through the reflectivity formula is a known way to produce confident nonsense.

**Eight further analysis plugins**: Batch Import with Filename Metadata (builds the datasets *and* the mapped column in matching order, removing the manual reordering in 3D from Multiple Datasets), Spectral Axis Converter, I-V Curve Analyser, Tauc Plot, Peak Tracker, Instrument File Import, Journal Figure Preset, and Auto-Backup.

**The Spectral Axis Converter now offers 16 units** — wavelength in m/mm/µm/nm/Å/pm, photon energy in J/eV/meV/keV, wavenumber in cm⁻¹/m⁻¹, frequency in Hz/GHz/THz, and equivalent temperature in K.

**A Plugin Reference in the manual** — what every plugin expects as input, every operation it offers, and what each deliberately will not do.

## Changed

**The menus have been consolidated, fourteen down to eleven.** `Grid`+`Tools` became **Graph**; `Mode`+`Annotations` became **Interact** (the drawing tools *are* modes); `Advanced Features` became **Tools**; `Statistics` moved under **Analysis**. Long flat runs became submenus: `File > Project / Live Data / Export`, `Plot > Arrange / Legend / 3D`, `Graph > Inset`. Every command is still there.

**The manual was rewritten against the running application.** Auditing it command by command found 38 commands documented nowhere, several statements that were simply wrong (it claimed 16 plot types when there are 17, seven annotation tools when there are eight, and that the app had no keyboard shortcuts when it has four), and menu paths pointing at commands that had been renamed. All 124 menu commands are now documented, and a test keeps it that way.

## Fixed

- **Rotating a large 3D plot is usable again.** On twelve datasets of two thousand points a frame took 1456 ms — under one frame per second. A 3D scatter is handed to the renderer as one path *per point* and depth-sorted every frame, and the legend was 62% of the frame on its own. While you drag, each curve is stood in for by a lighter version in its own colour and the legend steps aside; let go and the full plot returns. **About eighteen times faster.**
- **A 3D graph that was not already active could not be rotated at all** — clicking it took the rotation over and redrew a *different* graph, so the view turned while nothing repainted.
- **The primary legend no longer disappears** when a secondary-Y or inset legend is shown, hidden or restyled.
- **The pairing panel in 3D from Multiple Datasets no longer eats the dataset list** above it.
- **Four defects in the X-Kiran suite**, including a Bruker RAW reader that silently returned denormal garbage for integer-valued files, and a degenerate unit cell that quietly behaved like a 1 Å cube — producing confident, wrong peak positions.
- **The version can no longer drift.** It now has a single source of truth, with a test that fails if the app, the installer script and the build script disagree — the failure that left three of five places carrying the wrong version for several releases.
