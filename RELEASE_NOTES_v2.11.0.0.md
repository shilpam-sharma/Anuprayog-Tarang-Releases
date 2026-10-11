Three new analysis plugins, an X-Kiran that now genuinely fits X-ray data, and a Peak Deconvolution that copes with noisy, narrow peaks.

## New and rebuilt

**X-Kiran Suite — rebuilt from the ground up.** The old plugin placed an identical peak at every allowed reflection over a fixed background and refined only scale, a and c, so it could not fit real X-ray data. It now has:

- **XRD Refinement** — Le Bail and Rietveld refinement of cell, zero shift, sample displacement, peak widths (Thompson-Cox-Hastings), asymmetry, B_iso and preferred orientation, with intensities, phase scales and a Chebyshev background solved exactly at each step. Reflection multiplicities and centring rules are correct, structure factors use the International Tables scattering factors, CIF files can be loaded, Kα2 is modelled, and the fit reports R_wp, R_p, R_exp, χ² and parameter uncertainties, with quantitative phase analysis for Rietveld phases. If strong peaks in your data are not explained by the model (for example a starting cell too far from the true one), the status line turns red and says where.
- **Size / Strain** — individual peak fits with instrument-broadening correction, **Scherrer** crystallite size, **Williamson-Hall** (UDM, USDM, UDEDM) and the size-strain plot, including the cubic anisotropic Young's modulus.
- **XRR** — the reflectivity engine was wrong in two ways inherited from the original program: layer thickness did not affect the curve at all, and an absorbing layer *amplified* the beam. Both are fixed and checked against an independent reference simulation and real measured scans. It now also fits background, resolution, footprint and substrate roughness.
- **File readers** for Bruker RAW (binary and text), UXD, XRDML, Rigaku RAS, MDI and plain text.

**Peak Deconvolution** now fits noisy, narrow peaks (tested on a real grazing-incidence Ge pattern that it previously failed on): starting widths and heights come from the data, a background term is fitted by default, several starting strategies are tried and the best kept, and Auto Find Peaks ignores noise spikes.

**IR-FEL Imaging Pro** — a matrix-image viewer and processor (new plugin).

**THz-TDS Thin Film Analyzer** — batch extraction of optical constants and superfluid density from THz time-domain scans (new plugin).

## Good to know

- X-Kiran does not model anomalous dispersion or ionic scattering factors, and XRR multilayers need one table row per layer (no "repeat N times").
- Projects saved by earlier versions open unchanged.
