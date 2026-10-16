Save and reload X-Kiran fits, open old Excel (.xls) workbooks, read long LabVIEW datalog files, and renamed graph-style options.

## New
- **X-Kiran: save and reload a fit** (new **Fit** menu, and *Save XRD Fit...* / *Save XRR Fit...* / *Load Fit Parameters...* buttons). A small `.xkfit` file holds the phases, cell, profile and background parameters, range, exclusions and options (XRD) or the layer table, repeat block and fitted scale/background (XRR), plus the size/strain settings. Loading it with the same pattern redraws the fitted profile and R-factors without refining again. The measured pattern can optionally be stored inside the file; a file saved for a different pattern asks what to do, and a damaged or newer-version file is refused without changing anything. A new **Calculate Model** button on the XRR tab draws the reflectivity of the layer table as it stands.
- **Old Excel `.xls` workbooks now open** (File > Open, Append from File, drag and drop) with no extra software: numbers, text, dates and times, true/false values and formula results, several sheets. Text or HTML tables saved with the extension `.xls` are recognised and read as what they are.
- **LabVIEW datalog files of more than 128 records** now read in Instrument Import.

## Changed
- The graph-style options are renamed: **Classic Scientific Frame** (Plot > Graph Frame Style), **Palette with outlined markers** (Plot > Series Style Defaults) and the **ColorBrewer palette** in the colour dialogs. Graphs, projects and preferences saved with the earlier names open unchanged.

## Fixed
- A file named `.XLSX` or `.XLS` in capitals is now recognised; workbooks sent to the Import Wizard load as workbooks instead of showing a text preview.

Projects saved by earlier versions open unchanged.
