AnuPrayog: Tarang v2.6.1.0 — A scientific data analysis and plotting application.

Windows installer: **AnuPrayog_Tarang_v2.6.1.0_win64_Setup.exe**.
Upgrades an existing v2.x install in place; coexists with v1.0/v1.2.

## New

**Advanced FFT plugin** (Plugins > Advanced FFT) — the full transform dialog: 13 windows, window correction by amplitude or energy, the ±1 factor convention, one-/two-sided spectra, MSA/SSA power normalisation, and fourteen plottable quantities from Real/Imag through to Normalized dB. Window X Min/Max and Window Center (Data Center, Data Max Y, Custom X Position) mirror the built-in Analysis > FFT exactly, so the same settings give the same numbers in both.

**The window defaults to None.** Applying a window is a deliberate act with a cost — it suppresses amplitude and broadens peaks — so it no longer happens unasked. "Rectangle" remains in the list under its formal name and is numerically identical.

**The X column for the frequency axis is chosen explicitly.** This fixes a silent wrong answer: the frequency axis is built from the X column's spacing, and the plugin previously took whichever column happened to be designated X. On a dataset with more than one candidate, the spectrum came out with peaks at plausible but wrong frequencies and nothing said so. The plugin now also reports whether the chosen X is actually evenly sampled — an FFT assumes uniform spacing and will otherwise return a confident answer built from the median step.

**Every plugin can reach the data in the active project** through a shared project → dataset → column selector, instead of each one guessing at the current selection.

**X-Kiran can read patterns out of the project** (Project > Load XRD/XRR data from Project..., and beside each Load button). Data already imported, trimmed or background-corrected in the app no longer has to be exported to a file and read back to be refined. X and Y are chosen separately rather than assumed from column order, and rows are dropped as pairs where either value is missing — dropping them independently would shift intensities against angles.

**Live Data reads files with preamble.** **Rows to skip before header** matches the Import Wizard's setting of the same name. Instrument files routinely open with a block of text before the data; without this the first preamble line was read as the column names, or parsed as data and discarded. Only the initial seed is affected — a running watch reads appended bytes and never revisits the top of the file.

**Tab is the default delimiter for Live Data**, since instruments and LabVIEW VIs mostly write tab-separated text. Static import deliberately stays on Auto-detect: it gets pointed at arbitrary files, and a comma file read as tab-separated arrives as a single column with nothing on screen to say so.

**A folder watch can run unattended.** *Use the first file's settings for every later file* (on by default) and *Load new files automatically, without asking*. The first file always opens the Live Data dialog even with automatic loading on — nothing can guess which column is X, or how many rows of preamble there are, on a file it has never seen. Every file after it reuses the delimiter, skip, header, X column and plotted columns.

**File > Live Data > Stop Watching Folder**, which names the folder and greys out when nothing is being watched. Stopping previously meant re-opening the watch dialog and unticking a box.

**Auto-Backup snapshots can be deleted** — several at once, or all of them. The confirmation names each snapshot and the total size before doing anything.

**How to cite the software.** Help > How to Cite... offers BibTeX, RIS, APA and plain text for the exact version you are running, one click to copy. Releases are archived on Zenodo with a concept DOI (10.5281/zenodo.21887356) and a per-release version DOI, and are mirrored publicly at github.com/shilpam-sharma/Anuprayog-Tarang-Releases.

**The opening screen carries the name in Devanagari** — अणुप्रयोग: तरंग above the English.

## Changed

**A rebuilt Scientific Calculator** — an expression evaluator that rejects input by structure rather than by blacklist, unit and base conversion, and three tabs of functions.

**Install Plugin... now sits directly under Reload Plugins**, above the separator, instead of among the plugins themselves.

**Advanced Typography, Demo Feature and Calculator Tool have been removed.**

## Fixed

- **The application could hang at startup, frozen at "Building interface...".** The auto-backup recovery prompt ran on a fixed timer that fired while the splash screen was still animating. Animating pumps events, so the modal opened *inside* the animation and the always-on-top splash covered it — the splash never closed and the main window never appeared, leaving the app waiting on a dialog nobody could see. The prompt now waits until the main window is genuinely up.
- **A false "recover unsaved work?" prompt after running the test suite.** Each headless test registered a session in the real backup directory and left its marker behind, so the next launch was told a session had crashed that never existed.
- **The version can no longer drift** between the application, the installer and the build script.

---

## Citing this release

If this software contributed to work you are publishing, please cite it.
The running application offers the same citation, for the exact version
you used, under **Help > How to Cite...**.

```bibtex
@software{sharma2026anuprayog,
  author  = {Sharma, Shilpam},
  title   = {{AnuPrayog: Tarang}},
  version = {2.6.1.0},
  year    = {2026},
  doi     = {10.5281/zenodo.21887356},
  url     = {https://github.com/shilpam-sharma/Anuprayog-Tarang-Releases},
  note    = {Free to use, closed source. See the EULA for full terms.}
}
```

The citation above uses the **concept DOI**, which always resolves to the
newest version. A version DOI specific to 2.6.1.0 is minted by Zenodo
when this release is archived, and appears here and in the application
once it exists.

## Licence

Free to use, closed source. See the EULA for full terms. The source code is not public. See
[EULA.md](https://github.com/shilpam-sharma/Anuprayog-Tarang-Releases/blob/main/EULA.md) and
[THIRD_PARTY_LICENSES.md](https://github.com/shilpam-sharma/Anuprayog-Tarang-Releases/blob/main/THIRD_PARTY_LICENSES.md).
