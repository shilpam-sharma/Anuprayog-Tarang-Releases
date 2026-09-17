Fixes for the previous release: a date-axis plot could reopen with its curve drawn off-screen, most plot types' Style settings didn't fully work, Append from File couldn't match a real logger file, and dragging a point on a date/time axis threw the curve off-screen instead of moving it.

## Fixed

**A date-axis Line could reopen with nothing visible.** The data and the axis were both correct — the curve itself was being drawn roughly 100 trillion times further right than it should have been, because reopening a project converted a date column to a plain number the wrong way. It only affected the *restore* path, so a curve plotted fresh in a session was never touched; saving and reopening it is what triggered it.

**Style settings didn't work properly for most plot types.** An audit of every plot type this app offers — 17 in total — found that only Line and Scatter fully worked:

- Eight types (Smith Chart, Polar/Ternary/3D Scatter, both Contour types, 3D Surface, 3D Wireframe) failed silently the moment you pressed Apply or OK.
- Bar charts lost their colour and reopened black.
- Horizontal Bar, Box Plot, Violin Plot and Vector/Quiver ignored the colour picker entirely.
- A Histogram's colour cycled through blue, orange, green... on every Apply, rather than staying the colour you picked, and its Y axis didn't rescale when you changed the bin count or turned on Density.
- Pressing Apply with nothing changed still thinned every line from 1.5 to 1.0 pixels wide, and added circle markers to error bars that had none.
- Attaching error bars to a curve silently recoloured it.

All of the above is now fixed, and the dialog only shows the settings that actually apply to the plot type you're styling — a Contour gets a colour map picker, a Bar chart gets an edge colour and opacity, and so on. Every setting now survives save, close and reopen exactly as set.

**Append from File couldn't match a real logger file.** If the file had no header row — the normal case for an instrument log — the first row of actual data was mistaken for column names and silently dropped, and nothing else in the file could ever match afterward. Columns are now matched by name where possible, or by position when the file has exactly as many columns as the dataset; if neither is possible, nothing is appended and you're shown both column lists so you can see why. A file logged only as a time of day (no date) is now anchored to the date already in the dataset, so appending the same growing log again the next day correctly adds only the new rows instead of duplicating the whole thing.

**Dragging a point on a date/time X axis threw the curve off-screen.** The point actually being dragged updated correctly in the data, but the drawn curve jumped far outside the visible plot — including when dragging along Y only, which shouldn't touch X at all. Restricting the drag to "only points inside the Data Range" on a date axis also crashed outright. Both are fixed, and a curve **Live Link**ed to a date column no longer has its dates silently replaced with meaningless numbers when the link updates.

## Everything else

Unaffected. Projects saved by earlier versions open unchanged.
