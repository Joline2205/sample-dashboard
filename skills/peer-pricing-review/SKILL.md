---
name: peer-pricing-review
description: Review competitor pricing in Google Sheets against listed vendor sources, flag unverified prices, and create a dated copy of the dashboard.
---

# Peer Pricing Review

Run this workflow on demand or when invoked by an existing schedule. It requires a Google Sheets workbook URL, access to copy and edit workbooks in Google Drive, and access to the vendor pricing pages.

## Create the dated copy

1. Use the workbook supplied by the user on the first run. For later runs, use the most recent completed dated copy unless the user specifies a different baseline.
2. Duplicate the full workbook and name the copy `Sample Dashboard_MMM D YYYY`, using the actual review date in Europe/London. Create a dated copy even when the review finds no substantive changes.
3. Edit only **Company Details** in the copy. Preserve the original workbook and the copied **Summary** and **Calculator** tabs, including their formulas, pivot tables, and settings.

## Stamp the run date

1. Confirm that column B is **Product** and column V is **Last Updated**. Preserve the Product column. If Last Updated has moved, locate it by header and report the actual column used.
2. Before researching new competitors, write the actual run date as a fixed Sheets date to all 212 cells in `Company Details!V2:V213`, or the equivalent range if Last Updated has moved. Format the dates as `m/d/yyyy` so a run on November 26, 2026 displays `11/26/2026`.
3. Stamp every row in the range, including rows with unchanged or unverified prices. The date records when the workflow ran. Track pricing verification outcomes separately.

## Review existing entries

1. Review rows 2 through 213. Use the exact pricing URL already recorded in **Source**, column U, for each row. Preserve the listed URL. If it is missing, inaccessible, points to another product, or lacks comparable pricing, keep the existing price and record the reason.
2. Prioritize **Pay-as-you-go**, column O. Compare the same vendor, product, plan, currency, billing unit, usage tier, and billing cadence. Check included allowances and annual commitments where they affect the price.
3. Before editing a price, reread the listed source and double-check that the old and new values are on the same basis. Flag changes in the pricing model, tier, or unit when they prevent a direct comparison. Treat unavailable and quote-only prices as unverified.
4. Update verified monthly or annual-package pricing inputs where applicable. Distinguish a month-to-month price from a monthly equivalent that requires an annual commitment. Preserve calculated fields, including **Price per Unit** in column J and **Annual Discount** in column M.
5. Update classifications only when the evidence supports a change. Use the existing **Competition Lookout** dropdown values, including Active Competitor, Monitor Periodically, and Limited Relevance, and the existing **Product Competition Level** values of High, Medium, and Low. Record a brief rationale in the existing comments field.

## Add relevant unlisted companies or products

1. Check all of Company Details for duplicates, including alternate names and products listed under a parent company. Add entries in the first available data row in **For Any Unlisted Company/Products**, the section beginning at row 224. Preserve its heading and headers.
2. Record the exact official, product-specific pricing URL in column U. If public pricing is unavailable, leave the price blank and explain why in the comments.
3. Reuse the existing dropdowns for **Units**, **Competition Lookout**, and **Product Competition Level**. If no Units option matches what the vendor bills by, leave the dropdown blank and record the actual unit in the comments.
4. Enter `X` in **Not comparable for calculators** when the vendor bills in a different unit from the corresponding benchmark product. Flag uncertain comparisons in the comments and the run summary.
5. Follow the existing row structure, including Rubik, number formats, dropdown validation, formulas in calculated cells, and the black bottom border where the product or competition group ends. Record the run date using `m/d/yyyy`.

## Format, verify, and report

- Apply light red fill and dark red text to directly edited substantive values, including pricing inputs, classifications, comments, and new entry values. Keep routine date stamps and recalculated formula cells in their existing styles.
- Reread the full Last Updated range. Verify that **212 of 212** cells display the run date. Correct missing or incorrect dates and check again.
- Verify the copy’s name, edited prices, dropdown values, formulas, and change highlights. Check that Summary and Calculator still reference the copied workbook’s data. If new entries fall outside a pivot table’s source range, flag that in the summary.
- Return the dated dashboard link. Report the date-stamp count and pricing verification coverage separately. List confirmed price changes with the old and new amounts, billing units, cadence, and source links. Include classification changes, new entries, and unverified rows with reasons.
- If creating, editing, or verifying the copy is blocked, report the blocker and any findings you could verify.
