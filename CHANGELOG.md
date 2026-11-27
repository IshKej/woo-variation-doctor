# Changelog

## 1.0.0 - 2026-11-26

Initial release.

* WooCommerce product variations audit over a variations
  CSV export: variations with no price, sale prices above
  the regular price, sale prices with no end date, expired
  sale dates still active, duplicate attribute
  combinations on one parent, duplicate SKUs across
  variations, variations with stock but disabled, and
  enabled variations with zero stock and no backorder.
* Data quality checks: duplicate variation ids, malformed
  rows, empty variation ids, invalid prices, invalid
  stock, invalid sale dates, invalid attribute entries,
  invalid enabled and backorder flags, and sale starts
  after sale ends.
* Per-parent price range table (variation count, minimum
  and maximum regular price, variations on sale), plus
  catalog totals for variations on sale, variations with
  no price, and duplicate SKUs.
* Attribute combinations compare ignoring order and case;
  a sale that ends today is not expired; an expired sale
  on a disabled variation is not flagged; a variation with
  an invalid price gets invalid-price, not no-price. Money
  uses Decimal math, so price ranges add up exactly.
* Defensive date parsing (ISO dates, slash dates, ISO
  datetimes) and attributes cell parsing (semicolon
  separated name:value pairs); a bad row is reported as
  a finding and never crashes the run. UTF-8 BOM headers
  and extra columns handled.
* Findings carry a variation (or parent, or catalog), a
  rule name, a severity (error or warning), and a message;
  errors and warnings are counted in the summary.
* Text and --json output, --out file output,
  --max-variations and --as-of thresholds, and a --check
  CI gate that exits 1 on errors (and on warnings with
  --strict).
* Zero dependencies, Python 3.9 or newer.
