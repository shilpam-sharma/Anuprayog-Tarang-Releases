A patch release, mostly fixing what v2.8.0.0's own build slipped on.

## Fixed

- **The RF/Microwave Suite plugin failed to open in the installed app** ("scikit-rf (skrf) is not installed"), even though it worked fine from source. `scikit-rf` was missing from the Nuitka packaging list — plugins ship as data files, so Nuitka never scans them for imports. This is what actually forced this patch.
- **A real floating-point bug in the Kramers-Kronig plugin** (`kk_n_from_k`/`kk_phase`): the singularity exclusion checked whether a *computed* denominator was exactly zero, but NumPy's vectorized and scalar squaring aren't guaranteed to round identically — on an irregular energy grid this let a near-zero denominator through and produced spikes as large as ~7.8e11. Reproduces on Windows, not just Linux.
- **Maximize → Restore → Maximize could leave the left pane (Explorer/Notes) and the graph pane skewed.** The layout-recording suspend was a blind fixed timer, not tied to whether Qt had actually finished converging — a resize event firing in that gap could record a still-squeezed, transient size as if the user had dragged it.
- **A column designated as an error column, dragged onto a plot, drew as its own curve** instead of becoming error bars — the one entry point (drag-and-drop) that had no `(err)` check. Also added **Plot > Add Error Bars...**, since every existing route started from the column, not the graph.
- **Several Help topics were silently losing most of their text.** A bare `<placeholder>` in the manual's prose was parsed as an unknown HTML tag and swallowed everything after it — "Recalculation" rendered 27% of its content, "Data Matrix & Column Roles" 19%.

## New

- **X Error column role** (`(xerr)`), alongside the existing Y Error (`(err)`). A trace can carry both directions at once for the familiar cross-shaped uncertainty marker; Swap X/Y Axes exchanges them correctly, and both survive a `.trg` save/load round trip.
- **The Help window can now be maximized** (and minimized) — useful now that several topics carry embedded diagrams.
- All 26 Help topics were substantially expanded with worked examples, and 7 new diagrams were added.

## Everything else

Unaffected. If you're on v2.8.0.0, this is a recommended update — the RF/Microwave Suite plugin does not work there.
