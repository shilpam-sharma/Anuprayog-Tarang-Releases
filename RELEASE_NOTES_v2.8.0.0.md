# AnuPrayog: Tarang v2.8.0.0

A feature release: a new plugin for RF/microwave network analysis, a
new default project file format, and a new application icon.

## New: RF/Microwave Suite plugin

A full network-analysis toolset built on the open-source
[scikit-rf](https://scikit-rf.org/) library, reachable from **Plugins >
RF/Microwave Suite (scikit-rf)...**. Imports Touchstone (`.s1p`...`.s16p`),
CITI and MDIF S-parameter files, and offers:

- A Smith chart / dB-magnitude / phase / polar / VSWR / time-domain viewer
- Network operations: cascade, connect, de-embed, renormalize, flip,
  crop, resample, single-ended ↔ mixed-mode conversion, plain-language
  passivity/reciprocity/losslessness checks
- **One-port, two-port SOLT, and TRL calibration**, each verified to
  machine precision against a synthetic error network
- **De-embedding**: Open, Short, OpenShort, SplitPi, SplitTee, and the
  modern **IEEE P370** (2×-thru) standard
- **Named transmission-line media** — microstrip, coplanar waveguide,
  coaxial — built from physical dimensions, alongside the original
  generic gamma/Z0 line
- A **Circuit** schematic solver, **Vector Fitting** (pole-residue
  modelling), **Q-Factor extraction**, and **NetworkSet** statistics
  across repeated measurements
- A guarded **Instrument** tab for live VNA acquisition via `pyvisa`
  (inactive unless that optional package is installed)

Every numeric claim is verified against a synthetic case with a known
answer, and separately validated against real cryostat resonator
measurements from a NanoVNA.

## New: `.trg` project file format

**Project files now save as `.trg` by default** instead of the old
pickle-based `.anu` format — smaller, safer, and built to survive a
corrupted file cleanly rather than crash or hang.

- **Smaller.** Repeated data (a dataset column plotted in several
  traces) is stored once and referenced, evenly-spaced axes (time,
  wavelength, 2θ) collapse to a few bytes instead of one value per
  point, and the file is compressed. Meaningfully smaller than the
  equivalent `.anu` in testing.
- **Safer.** The old format was a raw Python pickle, which — like any
  pickle — can be crafted to run arbitrary code the moment it's opened.
  Opening a `.trg` file can never do that: the format has no code-
  execution path by construction. Opening an old `.anu` file is also
  safer now, going through a restricted loader that only reconstructs
  the specific data types a genuine project needs, rather than
  anything a file might ask for.
- **`.anu` is still fully supported** — every existing project opens
  with no loss, and Save As still offers `.anu` as an explicit target
  for sharing with an older install. "Save" (not "Save As") always
  writes back in whatever format a file already is; it never silently
  converts one to the other.

## New application icon

A new icon, plus two distinct icons for `.trg` and `.anu` project files
in Windows Explorer, each echoing the same design rather than an
unrelated symbol. The installer now registers `.trg` as a file
association (double-click to open) alongside `.anu`.

## Everything else

Unaffected. If you're on an earlier v2.x release, this is a recommended
update.
