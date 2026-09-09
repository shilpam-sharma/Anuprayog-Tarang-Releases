A feature release: Live Data now reads dates and times, plots can run against a point count instead of a real column, and a new plugin finds and chops out repeats of a pattern.

## New

**Live Data reads date/time columns.** Watching a file, a TCP or UDP stream, or a folder for new files, a timestamp column used to be forced to a number and arrived as all-blank. It is now read as real dates - the same rule the Import Wizard already uses - and choosing it as X gives the plot a proper calendar axis.

**Plot against iteration / point number.** *Live Data...* gains "Plot X as iteration / point number (not a data column)" - every reading still lands in the dataset as usual, but the curve's X axis becomes a running count (1, 2, 3...) instead of one of the file or stream's own columns. Useful for a logger with no meaningful X at all, or for comparing runs by reading number. A watched folder's remembered settings carry this to every later file too.

**Pattern Search: chop out repeats of a shape.** *Plugins > Pattern Search (Chop Similar Segments)...* - select a range on a plot with *Interact > Data Range Select*, and it searches the rest of that curve for other segments shaped like the selection, either the raw selected points or a function fitted to them. Matches are highlighted before anything is written, then chopped into a new dataset - one X/Y column pair per segment, side by side for comparison - plus a summary of where each was found and how well it matched.

## Fixed

Three issues surfaced while building the date/time support, all in code that predates this release:

- Rescaling a graph (auto-fit, or the Rescale X/Y/XY buttons) could crash if a trace held even one unparseable value - previously only possible for a stray non-numeric field, now also relevant to a bad timestamp.
- A date/time column chosen as a Y series is now shown as blank rather than crashing or plotting a meaningless number - a date is a position in time, not a quantity.
- A source file whose header line reappears mid-stream (e.g. after being truncated and rewritten while being watched) no longer leaks blank points into the plot.

## Everything else

Unaffected. Projects saved by earlier versions open unchanged.
