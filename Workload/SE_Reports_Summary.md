# SE Reports Summary

Checked on 2026-11-05 against the live `WarehouseDB.dbo` tables.

| | Workload report | Transferee Survey report |
|---|---|---|
| **File** | [Workload_Report_SE.html](Workload_Report_SE.html) | [Transferee_Survey_Report_SE.html](Transferee_Survey_Report_SE.html) |
| **Gold table** | `FactWorkload` | `FactTransfereeSurvey` |
| **Only from that table?** | **Yes** | **No:** it also has a test dataset, and that's what it opens on |
| **Rows in the page** | 3,313 | 8 from the table, 41 test |
| **Match to the live table** | All rows match | The 8 table rows match; 0 of the 41 test rows do |
| **Columns used** | 24 of 50 | 31 of 53 |
| **Built** | 2026-11-04 13:44 | 2026-11-04 16:43 |
| **Ready for real use?** | The data is, but the page's calculation rules need confirming | No, the table has no answered surveys yet |

Both pages are snapshots, so neither updates when its table is rebuilt.

## Workload report

- **Contents:** one row per Service Engine workflow action, covering 497 files and 374.12 total hours.
- **Views:** Service Provider and Client Summary, plus an overall summary, optional TE detail and a monthly view with FTE.
- **Data differences:** blank `Division` and `Corp Code` values became empty in the HTML, with no real values changed.
- **Zero hours:** 1,232 of the 3,313 rows have no hours, which pulls totals down. The page's notice says hours come from the action templates, so a missing time setting there gives a service 0.00 hours.
- **Rules to confirm:**
  - The 154 hours per month used for FTE.
  - A service is identified by file + service name + workflow name, because the table has no service ID.
  - Auth/Srvc Date is really the earliest action initiated date.
  - The hardcoded lists of closed and on-hold statuses.

## Transferee Survey report

- **Contents from the table:** 1 survey (file 278-0031) with 8 question rows and no answers.
- **Contents from the test data:** 6 surveys and 28 answered rows from an SE_DEV extract. None of these rows are in the gold table.
- **Formats:** Overall Rollup, Detailed Survey Report, TE Detail Comments and Surveys Requiring Action.
- **Data differences:** three flag columns hold a single space in the table and are empty in the HTML, with no effect on results.
- **Rules to confirm:**
  - A survey is identified by file + sent date, because the table has no survey ID.
  - Top Box scores count rating labels, not points.
  - The Surveys Requiring Action rule is still marked as proposed, for Ops to confirm.

## What to do next

1. **Find the missing survey answers:** file 278-0031 has 7 answered rows in the test data but none in the gold table, and the reason isn't known yet.
2. **Remove the test data:** once answers are loaded, drop it or open on the gold table so test results can't be mistaken for real ones.
3. **Confirm the rules:** take both lists above to Ops or the report owners.
