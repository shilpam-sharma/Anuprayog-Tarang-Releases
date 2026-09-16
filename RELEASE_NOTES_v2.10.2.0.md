A fix for the on-plot tools quietly refusing to work on any plot with a date or time on the X axis.

## Fixed

**Data Reader and Data Label did nothing on a date/time plot.** Clicking a point with **Interact > Data Reader** gave no reading at all, and **Annotations > Data Label** kept saying "click closer to a plotted point" however precisely you clicked it. Both now work normally.

Live data was the usual way to run into this — a watched file with a timestamp column — but it was never really about live data: *any* plot with dates on the X axis was affected, including one made by importing a file with a date column.

The reason both failed together is that they share the same piece of work: taking a curve's X and Y values and pairing them up to find which plotted point your click landed nearest. That pairing simply cannot be done when the X values are dates and the Y values are numbers, so the search never got as far as looking at your click. Data Reader was left with nothing to report, and Data Label concluded — wrongly — that there was no point near you.

**Two more tools on the same plots were affected the same way, and are fixed too:**

- **Delete** mode would not remove a point.
- **Drag** (Anchor) mode would not pick a curve up.

Neither was reported, because both simply did nothing at all — the same silence as the other two.

**A Data Label on a date plot now reads as a date.** It shows the actual timestamp — `(2026-01-01 00:03:00, 4.5)` — rather than the internal number the axis counts in. That holds wherever the label is redrawn: when you place it, when **Recalculate** updates it, and when you reopen the project. Labels on ordinary numeric plots are untouched, and still show numbers exactly as before.

## Everything else

Unaffected. Projects saved by earlier versions open unchanged.
