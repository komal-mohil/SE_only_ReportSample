# SE Reports Summary

Checked on 2026-11-05 against the live `WarehouseDB.dbo` tables.

| | Workload report | Transferee Survey report | Survey by Supplier report |
|---|---|---|---|
| **File** | [Workload_Report_SE.html](Workload_Report_SE.html) | [Transferee_Survey_Report_SE.html](Transferee_Survey_Report_SE.html) | [Supplier_Survey_Report_SE.html](Supplier_Survey_Report_SE.html) |
| **Gold table** | `FactWorkload` | `FactTransfereeSurvey` | `FactSupplierSurvey` |
| **Only from that table?** | **Yes** | **No:** it also has a test dataset, and that's what it opens on | **Yes**, but all of the table's rows are made-up samples |
| **Rows in the page** | 3,313 | 8 from the table, 41 test | 9, all sample |
| **Match to the live table** | All rows match | The 8 table rows match; 0 of the 41 test rows do | All 9 rows match on the 10 columns compared |
| **Columns used** | 24 of 50 | 31 of 53 | 20 of 28 |
| **Built** | 2026-11-04 13:44 | 2026-11-04 16:43 | Table data 2026-11-05 11:09; page remade 2026-11-05 16:34 |
| **Ready for real use?** | The data is, but the page's calculation rules need confirming | No, the table has no answered surveys yet | No, the table has no real supplier answers yet |

All three pages are snapshots, so none updates when its table is rebuilt.

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

## Survey by Supplier report

- **Purpose:** supplier performance management and scorecard reviews. Supplier Mgt uses Summary by Supplier with Detail, with comments always shown.
- **Contents:** 9 sample rows covering 5 surveys, 4 suppliers and 7 distinct rated answers. A notice on the page says they aren't real. Service Engine has no surveys with supplier sections yet, so the table has no real rows.
- **Formats:** Summary by Supplier with Detail (the default), Summary by Supplier and Summary by Section, as in Back Office. Supplier Scorecard and Supplier Comments are extras.
- **Selections:** client, service provider, supplier type, one or all suppliers, and date range. It can also group by service provider, client or supplier type. Profit Center is left out, as the business decided.
- **How answers are counted:**
  - The survey tables have no supplier column, so each answer goes to the supplier on the question, or else to the supplier in the matching role on the file. Role matches are tagged "Credited by role".
  - A shared answer counts for each supplier's own score, but only once in totals across suppliers.
  - `Remove From Report` rows are hidden. `Remove From Calc` rows are shown but not counted.
- **Not in the page yet:**
  - The VIP marker: the page is ready, but `FactSupplierSurvey` needs the VIP columns.
  - General survey comments: "Other Comments or Feed Bak" names no supplier, so these can't be credited.
  - Email as attachment, which a static page can't do. The Excel output is a CSV file.
- **Rules to confirm:**
  - The six section-to-role mappings in `int_se_fact_SupplierSurvey` are hard-coded and marked "To confirm with Supplier Mgt".
  - The five-point Satisfied scale replaces Back Office's six-point Agree scale, so Top Box, Top 2 Box and Top 3 Box need agreed meanings.
  - Yes and No answers have their own columns. Back Office counts them under Agree and Disagree, so scores won't match it exactly.
  - The date filter uses Survey Sent Date, while Back Office filters on Surveys Created.
  - Mortgage, HFP Agent, Home Sale Agent, Rental Assistance and Property Management have no SE question, so their scores would stop.

## What to do next

1. **Find the missing survey answers:** file 278-0031 has 7 answered rows in the test data but none in the gold table, and the reason isn't known yet.
2. **Remove the test data:** once answers are loaded, drop it or open on the gold table so test results can't be mistaken for real ones.
3. **Confirm the rules:** take the three lists above to Ops, Supplier Mgt or the report owners.
4. **Test the supplier logic on real data:** once surveys with supplier sections exist, rebuild `FactSupplierSurvey` and regenerate the page. The rebuild also clears the sample rows.
5. **Add the VIP columns:** carry `client_vip` and `ncm_vip` into `FactSupplierSurvey` at that rebuild.
6. **Work through the open points:** the list below shows who needs to answer each one.

## Open points

These come from the Observations section of each report's All Points file and from section 6 of the Workload guide. They add to the "Rules to confirm" lists above, which aren't repeated here. Points that the pages or tables have already settled are left out. "Who answers" comes from the Workload guide where it names someone, and is otherwise a suggestion.

### Workload report

| Point | Why it's open | Who answers |
|---|---|---|
| Report grain | The spec says one row per role per action. The live table has one row per action (3,313 rows, 3,313 Action IDs), so the unique index holds, but the table doesn't match the spec | Data engineer, Ops |
| Back Office match | The fact holds action-level time. Back Office shows service-level hours from `tblServiceHours`, so the two may not reconcile | Ops |
| Front load label | The page says "Every open action's full hours", but only cancelled actions are removed, so completed actions still count | Ops |
| Front load start date | The heading shows "Authorizations from" the start date, but earlier authorizations are still included | Ops |
| Closed services | The status date is only checked against the start date. A service closed after the end date can be included, and with the box off it's left out even if it was open on the end date | Ops |
| Active-only rule | The Word document says a closed service drops off, but `pr_GetWorkLoadTransferees` keeps services completed or cancelled on or after the start date | Ops |
| Report headers | Samples suggest "Authorizations from" goes with Front Load and "Active Files from" with Monthly Distribution, but nothing confirms it | Ops |
| Cancelled actions | 35 rows have status `Cancelled`, but only 18 have a cancelled date. The page relies on the status | Data engineer |
| Service-level values | Client, division, move type and status come from the first action row read for each service | Data engineer |
| Monthly split | The Word document gives BVO/MVP 15.5 hours, but the listed months total 12.25 because month 12 is blank | Ops |
| Weighted Workload | The Word document describes it and the menu lists it, but the Client Relations list says "NOT NEEDED". Its worked example also doesn't calculate: 2.25 / 28 is about .080, not .089 | Ops |
| Report names | The Word document still has two unfilled placeholders, and two trackers say "name TBC" although `Phase 1 Ops Reports.xlsx` names the four variants | Ops |
| Spec and view differ | The spec says `udv_Workload Detail_34`, but the view is `udv_workload_view_34`. The spec lists `File Status Date`, which the view lacks, and the view has `Client`, which the spec lacks | Data engineer |
| Tracker | `Test/Tracker.xlsx` row 52 still says "No fact yet" and "Not Started" | Report owner |

### Transferee Survey report

| Point | Why it's open | Who answers |
|---|---|---|
| Points direction | The spec gives Very Satisfied 5 points, but the test surveys and current template give it 1. Anything built on points could read backwards | Business |
| Odd question weights | "Consultant's responsiveness" is 1 2 2 4 5 and "local service provider" is 1 3 3 4 5, which look like typing errors | SE admin |
| Return Rate | It needs surveys sent, including those never returned. The page uses the surveys in the data, so confirm unanswered surveys are kept, and how 2nd and final requests count | Business, data engineer |
| Transferee Permission filter | Back Office has it, but SE has no such question. The page shows it as not available, so the business needs to decide whether to drop it | Business |
| WOW Factor and Ace Award | Bert uses this report to calculate them, but no file gives the formula, and the scores may not carry across | Bert |
| Comparing with Back Office | The six-point Agree scale and longer survey became a five-point scale with fewer questions, so "compare manually" can't match question for question | Business |
| Surveys Requiring Action | There's no sample or definition, and it's unclear whether it's in Phase 1 | Ops |
| Comments format | The DE note says "No comment option", but Back Office and both report lists expect comments. The page has them, so the note needs correcting | Report owner |
| View version | The view text we hold is older than the dbt model (ticket 39063), so the port couldn't be checked. Get the current view from SE | SE team |
| Older forms | The model matches on exact question text, and older forms use different wording. That would leave Service blank. The live table has 0 blanks in 8 rows, which is too few to show this | Data engineer |
| "Action at least Started" rule | The dbt model needs `act_dateactive`, which may be the same rule | Data engineer |
| `Survey Complete Date` | It uses the admin date, so a survey completed but not administered shows no date | Business, data engineer |
| Test coverage | The data is too small to test the rollup: 1 unanswered survey in the table, and 6 test surveys, of which 4 are answered | Data engineer |
| Test workbook errors | Screenshots and ratings for Russell, Hamilton and Leclerc disagree, so check it before using it to reconcile | Report owner |
| Trackers and report lists | Row 50 of `Test/Tracker.xlsx` is out of date. One tracker row may cover two reports. The report path differs between sheets. `Report Variants` points to the wrong sample. "KM to confirm which format Anna uses" is unanswered | Report owner |
| Spec and data definitions | The spec names a different view, and its description looks copied from another spec. The data definitions cite `ResponseText`, but the schema has `ResponseComments` | Data engineer |

### Survey by Supplier report

| Point | Why it's open | Who answers |
|---|---|---|
| No approved spec | The Service Information spec says "no requirements for Supplier Surveys", so the fact's design isn't signed off. The supplier link is our own logic | Supplier Mgt |
| Wrong supplier credit | Back Office stored the vendor on each response. SE infers it from the question contact or from any service on the program, so a supplier that wasn't rated could get the score | Supplier Mgt |
| Answers with no supplier | The joins are inner, so these answers are dropped without warning. Compare counts with `FactTransfereeSurvey` once real data exists | Data engineer |
| Fewer questions | SE has one rating question per supplier section, where Back Office has several plus "would recommend". The "compare manually" plan can't match question for question | Supplier Mgt |
| How comments should appear | No sample shows a comment, so the layout is a guess. The business also needs to say what to do with general comments that name no supplier | Supplier Mgt |
| Missing fact fields | Besides VIP, the fact has no Service Type (`BO Data Fields!B55`) or response date. The page uses the survey section as Service Type | Data engineer |
| Number of reports | The report list shows four lines but counts 1. Confirm the "grouped by" versions are just options on one report | Supplier Mgt |
| "Service Provider" meaning | In the dialog it's the NuCompass consultant, which is what the page uses. `BO Data Fields` maps it to "Supplier Authoorized?" | Supplier Mgt |
| Destination Services weights | They're 1 3 3 4 5, which looks like a typing error and changes Rating Points. The page doesn't use points | SE admin |
| Back Office damage question | "Did you have damage..." counts No under Disagree, which lowers scores for a good outcome. ABBE's Top 2 Box would be about 97% instead of 89% without it, so allow for this when comparing | Supplier Mgt |
| Back Office section totals | Summary by Section totals restart when a heading repeats, so don't reconcile to them. Total Over all Response is correct | Report owner |
| Back Office format totals | By section has 283 counted responses and By supplier has 279 for the same dates and filters. The reason isn't known | Report owner |
| Trackers and docs | `Test/Tracker.xlsx` row 49 says "No fact yet" and "Not Started". The report is ID 47, 40 and 52 in three trackers. The owner is blank or TBC, though `Contents!D14` says Anna. Section 11 of the All Points file still says there's no sample page. The model comment on service codes overstates the case | Report owner |

### Both survey reports

- **Real names:** the Transferee and Supplier All Points files and their screenshots show real names, and supplier scores are commercially sensitive. Take care if you share them outside the team.
