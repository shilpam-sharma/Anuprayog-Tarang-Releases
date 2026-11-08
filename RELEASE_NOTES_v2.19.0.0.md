# AnuPrayog: Tarang v2.19.0.0

A reliability release. It adds Normalize Columns and an error log, stops several
ways of silently losing data, and corrects the help against what the program
actually does.

## New

- **Data > Normalize Columns.** All 14 methods of Origin's Normalize Columns
  (divide by a value, to [0, 1] / [0, 100], Z scores, divide by max / min /
  mean / median / SD / norm / mode / sum, by a reference column or cell).
  Output a new column or overwrite; Recalculate Manual, Auto or None; live
  preview; one Undo step. Also on the column-header menu. A zero or constant
  divisor, or a column that cannot be normalised, is refused with a message
  naming the column instead of giving NaN or infinity.
- **Help > Error Log.** An unexpected error is written to
  `~/.anuprayog/logs/errors.log` with the command that was running, and a
  small non-modal notice tells you so.
- **Licence texts are installed with the program.** The EULA and the
  third-party licence texts now sit in the program's folder.
- **Global Curve Fit across graphs.** Pick traces from every graph of the
  project; each fit curve is drawn on its own trace's graph.
- **Drag a single point.** Drag has a third choice, "Only the point under the
  cursor".
- **STFT and CWT honour the Data Range**, like the other operations.
- **Advanced FFT plugin** takes its windows from the app's own builder (same
  Kaiser and Gaussian defaults as Analysis > FFT) and supports Tukey.

## Fixed

**Your data is no longer silently lost**
- Open Project (with close first) asks Save / Discard / Cancel for every
  unsaved project and stops if you cancel or a save fails.
- Projects saved as .trg now keep each dataset's units, long names and
  Math/Fill formulas (they were dropped on reopen). Older installs still open
  these files.
- Units, long names and formulas also survive appending rows, pasting rows
  and Live Data.
- The .trg ramp encoding is now exact; a column is stored as a ramp only if it
  comes back bit for bit.
- Batch Processing keeps blanks and text as NaN instead of turning them into 0.
- Live Data (TCP, UDP, file) keeps every column the stream sends.
- Append from File keeps a last line with no line ending until it is complete.
- Typing "2.3M", "4u" or "1.5k" into a Data Matrix cell is read like any
  numeric box; text a number column cannot hold is refused instead of becoming
  a blank NaN.
- Save Project As / Save All adds .trg (or .anu) when the name has no extension.
- Each project has its own Scripting-tab script.

**Plots and graphs**
- Plot... with a date X column draws dates, and a text X column draws labelled
  categories (they were nanosecond integers and "No Data").
- Plot... 3D Scatter with Twin Axis no longer raises an error and leaves an
  empty graph; Twin Axis is disabled for 3D.
- Graph > Axis Behaviour > Add Functional Axis opens its dialog (it raised an
  error before).
- Interact > Analysis Uses Data Range: the tick works.
- Data > Reduce Rows is one step on Edit > Undo.
- Peak Fit shading sent to the project is saved, reopened and deleted with its
  curve.
- Live Link: a Data Label follows its point when a cell edit moves the curve.
  Reader decimals also redraw existing Data Labels.
- Plot... opens on the dataset shown in the Data Matrix, not the first one.
- Dragging points on a date axis writes the times back without stray
  sub-second digits.
- The Data Label tool on a 3D graph, and ROI Zoom on a PyQtGraph graph, now
  say why they cannot be used there instead of doing nothing.
- Error bars never attach to another curve when their own curve is not plotted.
- Change 3D Plot Type keeps a scatter's colour.
- Tick labels by Plot Column Label stay with their ticks; the Image Digitizer
  handles logarithmic axes per axis; the Peak Deconvolution table keeps full
  precision; Scatter no longer shows Line Style / Width / Skip rows and a
  small marker is kept under 1 pt.

**Commands and dialogs**
- Data Matrix: dragging several selected columns from the header corner works.
- Statistics commands give a message instead of returning silently, and
  explain NaN results.
- Project History names the source trace and result dataset for Smooth,
  Derivative, Integration, Filter, Plot Arithmetic and FFT.
- Batch Import: "*{}nm*" gives 405 for scan_405nm.csv.
- The floating dataset window no longer has a re-dock button with nowhere to
  dock.
- The proxy timeout box accepts full precision.
- The Live Data preview shows all its rows, and a literal "&" is no longer
  swallowed in button, tab, group-box and label texts.

**Plugins**
- IR-FEL Absorptance: T and R are shown beside an absorption in the sample
  (were NaN); Sets tab headers are readable; its help says a tick only marks a
  change until "Recalculate the average" is pressed.
- IR-FEL Imaging Pro csv reload; WHH with an empty project and 1-sigma
  columns; JCAMP-DX factors, and DIF/DUP in XY refused with a message;
  NLFit Fixed boxes and curve list; calculator math errors; Batch Import row
  alignment; data-log detection by content with per-channel units; Flat Top
  taper.

## Help corrections

- 99 statements across help pages 02-25 corrected against the code (menu
  paths, defaults, FFT windows, column names, legend anchors, plugin
  installation rules, worked examples).
- 13 more corrected after running the real program: Line does not attach the
  error column by itself, Recalculate keeps the same parameters, Baseline
  Subtract & Save leaves the label, Bar and Histogram edges, inset placement,
  tutorial "Do it" steps, SSP accuracy, XRD absorption and mean a(i) wording,
  WHH deviation, and the extinct-reflections export box.
- Pages for Normalize Columns, the Sets tab, Drag, Global Curve Fit, the
  floating dataset window and the licence files updated.

## Reliability and testing

- Every test now runs in an isolated profile and never touches your real
  `~/.anuprayog` folder; a parallel runner and a guard check this.
- A harness drives every menu command (165 of 214 inventory commands are menu
  actions) and checks: no hidden exception, one Undo restores, .trg round trip
  identical, change notification. It currently has no known failures.
- A mutation runner re-introduces 19 recent bugs on purpose; all 19 are caught.
- New tools: an exe menu-command smoke test (`packaging/run_frozen_command_smoke.py`)
  and a real-display dialog clipping check.
- Slow IR-FEL and X-Kiran test scripts were split to fit the per-script time
  limit.
- The standalone X-Kiran shares network.py with this release; its proxy
  timeout box works there too.
