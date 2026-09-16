Plot settings you can change after plotting, a way to top a dataset up from a file that has grown, spreadsheet copy-and-paste inside the Data Matrix, and the fix for a reopened graph coming back empty.

## Fixed

**A saved graph could reopen empty.** Reported as live-data plots not surviving save–close–open: the dataset came back intact, but the graph opened with nothing drawn in it.

The plot was never actually lost. It was being drawn into an axes roughly 57 pixels square — present, correct, and far too small to see. Reopening a project applied the graph's **Equal Aspect** setting before the panel it lives in had been given its size, so "make this plot box square" squared it against a pane that was still effectively zero. On the project this was found with, the same axes now restore at 608 pixels square.

Two things changed so it cannot happen again: the pane is sized first and the aspect applied afterwards, and any axes that still ends up smaller than a usable minimum has its box aspect dropped rather than being left invisible. A graph that was saved before this fix opens correctly now — nothing about the saved file was wrong, only the way it was being rebuilt.

## New

### Plot settings you can change after plotting

Some plot types have numbers that *are* the plot rather than its appearance, and until now those were fixed the moment you created it — trying a different bin count meant deleting the histogram and plotting it again from scratch.

**Plot > Style...** (or double-click the plotted data) now shows a section for the settings that belong to the trace's own type:

- **Histogram** — number of **bins**, the **range** the bins span (or the data's own full range), **density**, **cumulative**, plus opacity, fill colour and edge colour.
- **Box Plot** — show **outliers**, and **notched** medians.
- **Vector / Quiver** — arrow **scale**.

Applying any of them redraws the plot from its own stored data while keeping the trace's identity, so its Data Labels, its legend entry and its place in the graph all stay exactly where they were. The new settings are saved with the project — a histogram reopens with your bin count and your colours, not the defaults.

Every other plot type was checked at the same time; the rest were already editable through Style.

### Append from File

**File > Append from File...**, and a button on the command toolbar, adds rows to a dataset you *already* have instead of importing the file again as a second copy.

Pick the dataset, pick the file, and only the rows the dataset does not already hold are added — so running it twice on the same file adds nothing the second time, and a logger's file that has grown since you imported it can be topped up as often as you like.

Columns are matched by name **ignoring the `(x)`/`(y)` role suffixes**, so the original file still works against a sheet whose headers now read `Time(x)` rather than `Time`. A column the file has gained since is ignored rather than widening the sheet and leaving every earlier row blank in it.

Because the dataset keeps its identity, everything already built on it carries straight on with the longer data — plots, fits, and anything locked with **Live Link**, where the curve redraws with the new points the moment they land.

### Copy and paste in the Data Matrix

The sheet now works like a spreadsheet, with no dialog in between:

- **Ctrl+C / Ctrl+X** put the selected block on the clipboard as tab-separated text — what Excel and OriginPro exchange — so it pastes straight into either of them.
- **Ctrl+V** writes the clipboard's block in starting at the **top-left cell of your selection**, and grows the dataset down and to the right if the block runs past the edge. A block from Excel, from OriginPro, from another dataset here, or from elsewhere in the same sheet all paste the same way. A column that arrives full of numbers becomes a numeric column, so it is immediately plottable rather than staying text.
- **Delete** clears the selected cells and leaves the rows and columns in place.

**Data > Paste from Clipboard...** is still there for the different job of turning a pasted block into a whole new dataset.

### Blank columns

Right-click a column header for three ways to add one, none of which stops to ask for a name: **Insert Blank Column Before '...'**, **Insert Blank Columns...** for several at once, and **Add Blank Column at End**. Inserting keeps the order of everything around it, which matters here because order carries meaning — a `(y)` column is paired with the `(x)` column to its left. **Add Named Column...** is still there when you do want to name it up front.

## Everything else

Unaffected. Projects saved by earlier versions open unchanged.
