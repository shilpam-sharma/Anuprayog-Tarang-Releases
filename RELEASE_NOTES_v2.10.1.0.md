A fix for live plots reopening unreadable, and font control for the last text in a plot that did not have it.

## Fixed

**A live plot on a date/time column came back wrong after save, close and reopen.** The times on the X axis were replaced by raw internal date numbers — `20453.99` where `00:02` belonged — which made a reopened live graph look like it had not survived the save at all.

Your data was never actually lost: the curve, its values and their timestamps were all saved and restored correctly every time. What went missing was the one flag that tells a reopened graph "this axis is dates", so the axis came back as plain numbers. It is now recorded with the curve, and a reopened live plot shows its times again — in both the `.trg` and the older `.anu` project formats.

The same gap had a second effect while you worked: a **TCP or UDP** live source begins with nothing to read, so it only discovers its X column holds timestamps when the first record arrives — and it never switched the axis over at that point. It does now.

## New

**Choose the typeface for annotation text.** Text annotations, Data Labels and legend pieces already offered size, colour, bold/italic and rotation; they now have a **Font** picker too, in both the dialog that places a text annotation and the Properties dialog for an existing one. The choice is saved with the annotation and restored with the project.

Titles, axis labels, legends and tick labels have had this all along under **Typography**, so this covers the remaining text in a plot.

Annotations you made before this existed are left exactly as they were: the typeface is only written when you actually pick one, so opening an old annotation's Properties and pressing OK will not quietly restyle it.

## Everything else

Unaffected. Projects saved by earlier versions open unchanged.
