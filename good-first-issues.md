# Good first issues

Seeded issues for new contributors. File each one on GitHub with
the `good first issue` and `help wanted` labels.

## 1. Report the largest sale discount in the summary

Title: Print the variation with the largest sale discount

Description: Add one line to the text summary naming the
variation with the largest discount (variation id, regular
price, sale price, discount amount), so a store owner can
act on the deepest cut without reading every finding. When
no variation is on sale, the line is omitted.

Difficulty: Easy

Acceptance criteria: the line appears for the sample file
naming V-106, $29.99 regular, $14.99 sale, $15.00 discount,
and for the clean file naming V-101 with a $5.00 discount;
JSON output is unchanged; a test checks both cases.

## 2. Flag variations priced below a floor

Title: Add a --min-price flag for bargain variations

Description: Some stores never sell below a floor price, and
a variation priced under it is usually a typo. Add a
--min-price flag (dollars) that reports a warning for every
variation whose regular price is below the floor. When the
flag is absent, no price floor is checked.

Difficulty: Easy

Acceptance criteria: with --min-price 20 the sample report
gains 9 warnings, one for each of V-301, V-302, V-303,
V-304 at $14.99 and V-401, V-402, V-403, V-404, V-405 at
$19.99, so the sample goes from 16 findings and 5 warnings
to 25 findings and 14 warnings; a test covers the flag;
README documents the flag.

## 3. Export the per-parent table as CSV

Title: Write the per-parent summary to a CSV file

Description: Add a --table-out flag that writes the
per-parent summary table (parent, variations, min_price,
max_price, on_sale) to a CSV file, so the numbers can go
straight into a spreadsheet or a catalog review. The text
report is unchanged.

Difficulty: Easy

Acceptance criteria: with --table-out table.csv the file has
the header above and 4 rows for the sample file, and the
P-100 row reads 8, 29.99, 34.99, 4; a test checks the file
contents.

## 4. Flag sales ending soon

Title: Warn on sale prices ending within N days

Description: A sale that ends next week needs a decision
now: extend it or let it lapse. Add a --ending-days flag
that reports a warning for every enabled variation whose
sale end date falls within that many days after the as-of
date. When the flag is absent, no ending soon check runs.

Difficulty: Easy

Acceptance criteria: with --ending-days 14 and --as-of
2026-11-18 the sample report gains 4 warnings, for V-101
and V-103 and V-404 (all ending 2026-11-30) and V-202
(ending 2026-11-25), so the sample goes from 16 findings
and 5 warnings to 20 findings and 9 warnings; a test
covers the flag; README documents the flag.
