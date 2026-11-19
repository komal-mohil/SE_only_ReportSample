# SE Reports Summary

Survey reports checked against the live `WarehouseDB.dbo.FactTransfereeSurvey` and SE's `udv_transferee_survey_view_34` on 2026-11-18. Both survey pages were re-checked against this summary on 2026-11-19; the data is unchanged since the 2026-11-18 16:12 build. The Workload column was checked on 2026-11-05 and has not been re-checked.

| | Workload report | Transferee Survey report | Survey by Supplier report |
|---|---|---|---|
| **File** | [Workload_Report_SE.html](Workload_Report_SE.html) | [Transferee_Survey_Report_SE.html](Transferee_Survey_Report_SE.html) | [Supplier_Survey_Report_SE.html](Supplier_Survey_Report_SE.html) |
| **Gold table** | `FactWorkload` | `FactTransfereeSurvey` | `FactTransfereeSurvey` (the same table; `FactSupplierSurvey` is no longer used) |
| **SE view** | `udv_workload_view_34` | `udv_transferee_survey_view_34` | `udv_transferee_survey_view_34` |
| **Rows in the page** | 3,313 | 32 (3 test surveys) | The same 32; 5 are supplier answers |
| **Match to the view** | All rows match | Same 57 columns in the same order, same 32 rows. Auth Date / Benefit Expires (typed as dates) and the Service list order differ by design | As TE |
| **Columns used** | 24 of 50 | 24 of 57 | 16 of 57 |
| **Built** | 2026-11-04 13:44 | Fact rebuilt 2026-11-18 16:12 | Fact rebuilt 2026-11-18 16:12 |
| **Ready for real use?** | The data is, but the page's calculation rules need confirming | Layout yes; data is test only | Layout yes; data is test only |

All three pages are snapshots. `refresh_transferee_report.py` updates both survey pages from `FactTransfereeSurvey` in one run.

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

- **Contents:** 3 test surveys (278-0029, 278-0031, 278-0034), 32 question rows, all returned. 5 of the rows are the supplier answers added on 2026-11-18.
- **View update, 2026-11-18 (ticket 40217):** SE added Survey Last Sent Date, Number of Surveys Sent and Question Contact Company. They are now in `int_se_fact_TransfereeSurvey`, `FactTransfereeSurvey` and the page.
- **Formats:** the four Back Office formats plus two asked for by Lorrie and Bert:
  - Overall Rollup: counts per rating, Top / Top 2 / Top 3 Box, total row, return rate as Back Office defines it (TEs who answered ÷ TEs sent). Group by client, policy or service provider.
  - Consultant Scorecard (WOW / ACE): Bert's Survey Metrics. WOW is company-wide, judged per quarter or year from the dates entered, and ignores the Service provider filter. ACE is per service provider, per year.
  - Survey Status: sent, times sent, last sent, completed, days outstanding; show all, outstanding only or returned only.
  - Surveys Requiring Action: surveys with a negative answer, % negative, and whether they have been reviewed.
  - Detailed Survey Report and TE Detail Comments Report, both showing the Counselor Response under an answer when there is one (one test survey, 278-0034, has one).
- **Filters:** Corporate client, Service provider, Division, Policy, Date range (Survey Sent Date), Move type on every format. Some controls appear only with certain formats:
  - Transferee: Detailed, Comments and Survey Status.
  - Show metric box: Rollup and Scorecard.
  - Group by: Rollup.
  - Survey status: Survey Status.

  Department is shown but locked to (All Profit Centers), because SE has no profit center. Service, Section and Quick range were removed: Back Office had none of them and they did not change the results.
- **WOW / ACE targets in the page:**
  - WOW Tier 1: Overall, Responsiveness and Knowledgeable each need Top 2 Box of 90% or more and Top 3 Box of 96% or more; Expense Processing needs Top 2 Box of 95% or more.
  - WOW Tier 2: return rate of 45% or more.
  - ACE (Service Teams): Overall, Responsiveness and Knowledgeable each need Top Box of 60% or more, plus a return rate of 45% or more and at least 24 surveys returned.
  - ACE (REM): Expense Processing Top Box of 70% or more. The W-2 and Realty measures don't come from surveys, so the page doesn't show them.
- **Rating scale:** 5 points, Very Dissatisfied to Very Satisfied. Boxes count the rating label, because SE stores the points the other way round (Very Satisfied = 1).
- **Remove From Report / Remove From Calc:** not used. Every answer shows and counts. These flags apply only to the Survey by Supplier report.
- **Test data:** loaded by `te_survey_load_2026-11-06.sql`, `te_survey_answers_278-0031_2026-11-06.sql`, `te_survey_yesno_sample_2026-11-06.sql` and `supplier_survey_load_2026-11-18.sql` in `dbt/sql`, in that order. Re-run them if a reload from SE wipes the rows.
- **Rules to confirm:**
  - A survey is identified by file + sent date, because the view has no survey ID.
  - The question-to-category mapping for WOW / ACE (Overall, Knowledgeable, Responsiveness, Expense Processing).
  - Whether WOW Tier 1 is met per category or on the three categories combined.
  - Negative answer = Dissatisfied, Very Dissatisfied, or No.

## Survey by Supplier report

- **Purpose:** supplier performance management and scorecard reviews. Supplier Mgt uses Summary by Supplier with Detail, with comments always shown, and must be able to run one supplier.
- **Source:** the same `FactTransfereeSurvey` as the TE report. `FactSupplierSurvey` and its inferred-supplier logic are no longer used; the table is left in the warehouse untouched.
- **How a supplier answer is found:**
  - Supplier question = any question outside the NuCompass sections (NuCompass Mobility Inc., NuCompass Consultant, Expense Management, CoPilot, Other Comments).
  - Supplier = Question Contact Company. Supplier Type = the survey section (Household Goods, Auto Shipment, Temporary Living...).
- **Contents:** 5 test answers from `supplier_survey_load_2026-11-18.sql`, using SE's real supplier questions and contacts: ABC Van Line, Move Caddy, Arlington Auto Shippers, zReloQuest.
- **Formats:** Summary by Supplier with Detail (default), Summary by Supplier, Summary by Section, laid out as in the Back Office samples, with Totals For each question, section and supplier, and Total Over all Response.
- **Filters:** Corporate client, Service provider, Supplier type, Supplier, Show comments (hidden on Summary by Section), Date range. Profit Center is left out.
- **How answers are counted:**
  - Same 5-point scale and box rules as the TE report.
  - Yes counts under Satisfied and No under Dissatisfied, as Back Office put Yes under Agree and No under Disagree.
  - `Remove From Report` answers are hidden. `Remove From Calc` answers are shown but not counted. `Display Response` is not used.
  - "(VIP)" shows when Client VIP or NCM VIP is Yes.
- **Sample rows:** if the view has no supplier answers, the page offers clearly marked SAMPLE rows to show the layout. They switch off once real supplier answers exist.
- **Rules to confirm:**
  - SE's template gives the Temporary Living question the contact role File Manager instead of the housing provider.
  - What Display Response means, and whether comments should show only flagged ones.
  - The date filter uses Survey Sent Date, while Back Office filters on Surveys Created.

## What to do next

1. **Replace the test surveys:** when real surveys are loaded, undo the four test scripts in `dbt/sql` (each has undo statements) so test answers can't be mistaken for real ones.
2. **Confirm the rules:** take the "Rules to confirm" lists above to Bert, Lorrie and Supplier Mgt.
3. **Fix the Temporary Living contact role** in SE's survey template.
4. **Retire `FactSupplierSurvey`** once the business accepts the view-based supplier report.
5. **Work through the open points:** the list below shows who needs to answer each one.

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
| WOW Tier 1 reading | Bert's sheet merges Overall, Responsiveness and Knowledgeable into one cell. The page checks each one | Bert |
| Category mapping | SE's questions are mapped to WOW / ACE categories by their wording | Bert |
| Negative answer | Surveys Requiring Action counts Dissatisfied, Very Dissatisfied and No | Bert, Karen |
| Transferee Permission filter | Back Office has it, but SE has no such answer, so it can't be built | Business |
| Contact Preference column | Back Office's Requiring Action report shows it; SE has no such answer | Business |
| Resend rules | Number of Surveys Sent is now in the data, but how many resends are allowed and when is not defined | Business |
| Comparing with Back Office | The six-point Agree scale and longer survey became a five-point scale with fewer questions, so scores can't be compared question for question | Business |
| `Survey Complete Date` | It uses the admin date, so a survey completed but not administered shows no date. It is blank on all 3 test surveys | Business, data engineer |
| Odd question weights | "Consultant's responsiveness" is 1 2 2 4 5 and "local service provider" is 1 3 3 4 5, which look like typing errors. The page doesn't use points | SE admin |
| Test coverage | 3 test surveys, all returned, so Return Rate shows 100% and outstanding surveys aren't exercised | Data engineer |

### Survey by Supplier report

| Point | Why it's open | Who answers |
|---|---|---|
| Temporary Living contact role | SE's template sets File Manager. The page uses the section as Supplier Type, but the contact on the question still needs to be the supplier | SE admin, Supplier Mgt |
| Display Response | Not defined anywhere; possibly marks a comment as OK to share | SE team, Supplier Mgt |
| Fewer questions | SE has one rating question per supplier section, where Back Office has several plus "would recommend" | Supplier Mgt |
| Supplier types with no SE question | Mortgage, HFP Agent, Home Sale Agent, Rental Assistance and Property Management have no SE supplier question, so their scores would stop | Supplier Mgt |
| Back Office damage question | "Did you have damage..." counts No under Disagree, which lowers scores for a good outcome. Allow for this when comparing | Supplier Mgt |
| Back Office totals | Summary by Section totals restart when a heading repeats, and By section vs By supplier totals differ (283 vs 279). Don't reconcile to them | Report owner |

### Both survey reports

- **Real names:** the Transferee and Supplier All Points files and their screenshots show real names, and supplier scores are commercially sensitive. Take care if you share them outside the team.
