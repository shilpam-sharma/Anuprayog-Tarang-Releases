X-Kiran gets a fuller Rietveld refinement and an XRR x-axis in Q, and the Universal XRD Converter no longer invents angle axes.

## New: X-Kiran Rietveld
- **Anomalous dispersion** (f′, f″) in the structure factors, from the Henke tables; the absorption coefficient is computed from f″. Saved in the `.xkfit` file (older files load with it off, so they reproduce exactly).
- **Atom positions and B_iso**: refine x, y, z along the directions the site symmetry allows (the origin is pinned for polar groups) and a B_iso per atom; new Atoms-table columns and a report with uncertainties.
- **Texture**: spherical-harmonic texture symmetrised over the Laue group, and up to four March-Dollase components.
- **Anisotropic line broadening**: Stephens strain (symmetry-allowed terms) and spherical-harmonic crystallite size, for Le Bail and Rietveld.
- **Micro-absorption**: a Brindley correction for mixtures (the particle size D is an input - the pattern cannot determine it).
- **Ties and restraints** between refined parameters.
- The eight parameter tabs fit the pane.

## New: X-Kiran XRR
- **The x column can be 2θ (°), θ (°), Q (Å⁻¹) or Q (nm⁻¹)**, with the wavelength entered in the tab. **Convert 2θ → Q** rewrites the column with Q = 4π sin θ / λ (and **Convert Q → 2θ** reverses it exactly). A curve given in Q is fitted directly. The plot, the exported figure, the report and the dataset sent to the project use the chosen axis, and the axis and wavelength are saved with the fit. Points with Q beyond 4π/λ have no angle and are ignored, with a message.
- **Resolution convolution for thick layers**: a stack with a thick layer (for example a 300 nm oxide) has fringes finer than the old nine-point quadrature could sample; the model is now convolved on a fine grid with cubic interpolation (within 3×10⁻⁴ of a brute-force average, where the old rule was off by up to 5×10⁻²). Thin stacks give identical numbers to before.

## Fixed: Universal XRD Converter
- **Bruker RAW 1.01 files that start at 2θ = 0 - every XRR scan - were exported with an invented axis** (5.0 - 21.0° in steps of 0.02, whatever the scan really was), because the reader treated a start angle of 0 as "header unreadable" and replaced both the start and the step. The start, step, point count and wavelength now come from the header, and an unreadable header is an error, never a guessed axis. The preview title shows the point count, the angle range and the step.
- Also fixed: `.xrdml` files that list Omega before 2Theta, single-column `_COUNTS` `.uxd` files, and `.mdi` files with a title line; the `.xrdml`, `.ras` and `.mdi` files the converter writes are now read back correctly by X-Kiran; a file that cannot be read or written is reported on screen instead of only in a console.
- **New: export to `.uxd`** (Bruker-style text with the wavelength, start, step and the angle/counts table).

## Notes
- **Any `.xy` made from a `.raw` file by an earlier converter has the wrong angle axis; convert it again from the `.raw`.**
- This release includes everything in 2.14.0.0 - 2.16.0.0.
- Projects and `.xkfit` files saved by earlier versions open unchanged.
- The standalone X-Kiran program (a separate folder) shares these files and was updated alongside.
