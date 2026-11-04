# Workload Report: All Points Found, With File Locations

Compiled 2026-11-04 from the files in the `dwh` folder. No database was connected to or queried.

**How to read this file**

- Text in quote blocks and code blocks is copied **exactly as written in the source**, including its spelling mistakes (for example "repot", "Serivice", "reveiwed").
- Every point has a **Location**. Paths are relative to the `dwh` folder. Excel locations are given as sheet and cell.
- Where a file exists in several folders, the copies are listed once. They were checked as identical unless stated otherwise.
- Screenshots are stored in `Workload_Report_Screenshots/`, next to this file. Keep the two together so the images display.
- Section 13 is the only part that is not source text. It holds my own observations and is labelled as such.

**Contents**

1. [Workload description (business explanation)](#1-workload-description-business-explanation)
2. [Phase 1 requirements: Workload sheet](#2-phase-1-requirements-workload-sheet)
3. [Phase 1 Ops Reports summary](#3-phase-1-ops-reports-summary)
4. [Business Owners report list](#4-business-owners-report-list)
5. [Trackers and report lists](#5-trackers-and-report-lists)
6. [Other business mentions](#6-other-business-mentions)
7. [Sample reports and screenshots](#7-sample-reports-and-screenshots)
8. [NCM Workload Detail View spec](#8-ncm-workload-detail-view-spec)
9. [Service Engine objects](#9-service-engine-objects)
10. [Legacy Back Office stored procedures and tables](#10-legacy-back-office-stored-procedures-and-tables)
11. [dbt models](#11-dbt-models)
12. [Searched but not quoted](#12-searched-but-not-quoted)
13. [Observations (mine, not from the source files)](#13-observations-mine-not-from-the-source-files)

---

## 1. Workload description (business explanation)

**Location:** `Reports/Building Report Views/Workload Reports/Workload description current state.docx`
**Identical copy:** `Sharepoint/Building Report Views/Workload Reports/Workload description current state.docx`

The document opens with the heading "Workload" and a sample report image with two callout text boxes. The rest of the text follows in document order.

![Sample report embedded in the Word document](Workload_Report_Screenshots/01_docx_sample_service_provider_report.png)

*Image embedded in the Word document: Service Provider Workload Report, Authorizations from 01/01/21 to 12/31/21, United Airlines.*

### Callout text boxes on the sample report

> Let’s look at Household Goods-I.  The “I” means it is an international Service.

> We see that Anita has 26 active HHG services in her case load.  We see the Workload hours for those 26 HHG services is = 117.00.  So, to find the workload for the HHG service divide 117 by 26 which gives us a workload of 4.5 for Household Goods – I.

> Looking at the first on the list.  Discard and Donate.

> The “D” at the end of the service name indicates that this is a US domestic service.

> # of Services = 1 meaning the consultant is currently managing 1 Discard and Donate Services. 

> Workload Hours = the number of services X the workload hours for that service.  

> In this case, we see workload hours of .25 for 1 service.  So, we can deduce that the workload for Discard and Donate is .25 hours.

### How workload is measured

> We measure workload in hours. We do this in increments of 15 minutes. (.25 = ¼ of an hour or 15 minutes).

> We have identified each step the team takes to administer the service.  We then measured the time it takes for each step.

> Workload hours can vary based on the service type.  Domestic (US) or International.  For example.

> HHG – D =2.25 hours where as HHG – I = 4.50 hours

> We further break down workload over a 12-month period.  For example, if a service has a workload of 1 hour.  When does the work typically take place?  In the first month, second month, last month?  

> NOTE:  We have 

> Front Loaded Workload. This method shows the full weight of the workload up front.  It is what we see on the sample report above.  

> Because we break out workload over 12 months, it also means we can look at an individual’s workload for a specific point of time.  WE NEED TO KNOW WHAT THIS IS CALLED.  L

> Let’s use this example: The BVO/MVP service has a workload of 15.50.  Cheryl has 10 active BVO services for a total, front loaded workload of 155.00. 

> The 15.5 hours are split out as follows:

| Month | Workload | | Month | Workload |
|---|---|---|---|---|
| 1 | 2.00 | | 7 | 2.00 |
| 2 | 3.00 | | 8 | 1.50 |
| 3 | .75 | | 9 | .75 |
| 4 | .75 | | 10 | .25 |
| 5 | .50 | | 11 | .25 |
| 6 | .50 | | 12 | |

> We could run a report for 1 month, and rather than just saying that the consultant has 10 active home sale services that month for a workload of 155, the report looks at each of the10 home sale services determines the month and assigns the weight for that month.  

> If TE Jane Doe was in her 3rd month of the BVO service, the report counts .75 hours.  If TE Tom Jones is in his 7th month of the BVO service, the report will count 2.00 hours…

> Currently, Bert uses the Front-Loaded workload.  Lorrie will run the NAME OF THE REPORT to get a good understanding, at any point in time, what a consultant’s workload is at.

### Which services are included

> When report is run, it pulls active services only.  When a service closes, it drops off the report.

> A Service that is put on hold, the service does not pull to the workload report.  For example, if during the implementation call, the consultant finds out TE is not going to use the home finding purchase service for 3 months, they will put the service on hold.  This prevents the workload for that service from pulling to the workload reports until the service is taken off hold.

### Capacity and how managers use it

> It has been determined that each FTE can manage 154 workload per month, in other words a consultant that is at 154 workload hours is at full capacity.  Annually, that is 1,848 per year.

> Managers  look at the report monthly.  Bert and Lorrie provide a 60-day workload snapshot and report that up to  Serena.  The goal is to keep the workload balanced across the teams.  If someone has a spike in workload, they may re-distribute work until the workload comes back down.

### Using Workload for Projecting Business

> For new business, we look at the services that the client will be using and the estimated volume of TE’s and we estimate the workload.  This helps us understand/project the number of head count needed to manage the new client.  This is done in Excel.

### Weighted Workload

> Used by the ET to estimate revenue. Not exactly sure how they do this, but they developed a correlation between those two things.

> Used a baseline for a standard move the ET came up with 28 hours to manage a typical move (with a package of services).

> 28 is used as the common denominator to calculate the weighted workload each service.  

> Example.  We know that for HHG, it takes 2.25 hours to manage the service.  To get the weighted workload, we take 2.25 hours for HHG / 28, you get .089 as the weighted workload.  

---

## 2. Phase 1 requirements: Workload sheet

**Location:** `Sharepoint/Phase 1 Report Requirements - Ops.xlsx`, sheet `Workload`
**Identical copies:** `Extra docs/Phase 1 Report Requirements - Ops.xlsx`, `Ops_data/sharepoint/Phase 1 Report Requirements - Ops.xlsx`
**Text-only CSV export of the same sheet:** `dbt/Phase 1 Report Requirements - Ops(Workload).csv`

| Cell | Text |
|---|---|
| A1 / C1 | Backoffice Report / Workload Report |
| A2 / J2 | Description / BD: This looks good from a workload repot perspective. We run it by both Service Provider and Client Summary, so we can analyze revenue and staffing needs. |
| A3 | How it is used |
| A4 / C4 | Path to Report / Reports/Internal Reports/ Workload Report |
| A5 | Report selections |
| A6 | Which are the most commonly used Filters |
| A8 | Note for Ruchika, the last page of the report shows overall workload by Service. |
| A99 | Run by Client Summary, front load |
| A100 | LK - use this report to look at workload by client for REM workloads |

**Location:** same workbook, sheet `Instructions`, cells N1:Q1

| Report | Rank | Phase | Owner |
|---|---|---|---|
| Workload report by service provider | 1 | 1 | Bert |

### Screenshots on the Workload sheet

**Service Provider run** (image anchored at A11)

![Report dialog: Service Provider, Front Load All Hours](Workload_Report_Screenshots/02_req_dialog_service_provider_front_load.png)

**Service Provider report, page 1** (image anchored at K11)

![Service Provider Workload Report page 1](Workload_Report_Screenshots/03_req_service_provider_report_page1.png)

**Service Provider report, page 6: Overall Workload Summary** (image anchored at K53). This is the last page referred to in cell A8.

![Overall Workload Summary page 6](Workload_Report_Screenshots/04_req_service_provider_overall_summary_page6.png)

**Client Summary run, with the selections highlighted in yellow in the source** (image anchored at A102)

![Report dialog: Client Summary with highlights](Workload_Report_Screenshots/05_req_dialog_client_summary_highlighted.png)

**Client Summary report, page 1** (images anchored at J102 and K123)

![Client Summary Workload Report page 1](Workload_Report_Screenshots/06_req_client_summary_page1.png)

![Client Summary page 1 continued, with report total](Workload_Report_Screenshots/07_req_client_summary_page1_total.png)

**Client Summary report, Overall Workload Summary** (images anchored at K130 and K154)

![Client Summary Overall Workload Summary page 2](Workload_Report_Screenshots/08_req_client_summary_overall_page2.png)

![Client Summary Overall Workload Summary continued](Workload_Report_Screenshots/09_req_client_summary_overall_page3.png)

---

## 3. Phase 1 Ops Reports summary

**Location:** `Sharepoint/Phase 1 Ops Reports.xlsx`, sheet `Ops Phase 1 Reports`, row 5

| Column (row 4 header) | Row 5 value |
|---|---|
| # | 1 |
| Report (Phase 1) | Workload |
| Back Office Report / Path | Workload Report<br>Reports/Internal Reports/Workload Report |
| Business Owner(s) | Bert Dodson (Lorrie Kaiser for REM) |
| BO Rank | 1 |
| How It Is Used | Run by Service Provider and by Client Summary to analyze revenue and staffing needs. Last page shows overall workload by Service. LK uses Client Summary to review REM workloads. |
| Key Filters / Selections | Service Provider; Client Summary; Front-load all hours; Monthly distribution |
| # Report Variants | 4 |
| Data Source | SE only |
| Schema / Data Status | SE only data source |
| Sample Queries Available | None yet |
| Decisions & Notes | Data will come from SE. For BO data, Ops will generate in BO and compare manually. |
| Open Items | Need sample data and report format based on SE data. |
| Build Status | Not Started |

**Location:** same workbook, sheet `Report Variants`, rows 5 to 8

| Report | Variant / Format | Description | Sample / Query Reference |
|---|---|---|---|
| Workload | Service Provider Workload | Workload by Service Provider | Building Report Views/Workload Reports/SrvcProviderWorkLoad.xls |
| Workload | Service Provider Monthly Distribution | Monthly distribution of workload by provider | Ops Reports/SrvcProviderWorkLoad_Monthly Distribution.pdf |
| Workload | Client Summary with TE Detail (front-load all hours) | Workload by client; used by LK for REM workloads | Ops Reports/ClientWorkLoad_Client Summary with TE detail and Frontloading all Hours.pdf |
| Workload | Overall Workload by Service | Last page of report - overall workload by Service | Same as above |

**Location:** same workbook, sheet `Open Questions`, row 8

| # | Report | Question | Owner |
|---|---|---|---|
| 4 | TE Survey / Survey Follow Up / Workload | Provide SE sample data and screenshots so the SE-based report formats can be designed. | Ops / SE team |

---

## 4. Business Owners report list

**Location:** `Reports/Business Owners List Reports- BO vs SE  data fields.xlsx`
**Same cell values:** `Sharepoint/Business Owners List Reports- BO vs SE  data fields.xlsx` (the file bytes differ, the cell values do not)
**Earlier version without the two "Report List by RB" sheets:** `Reports/Building Report Views/Ops Reports/Reports- BO vs SE  data fields.xlsx`, identical copy at `Sharepoint/Building Report Views/Ops Reports/Reports- BO vs SE  data fields.xlsx`

### Sheet `Operations`, BO fields and sort options (columns A to E)

| Cell | Column | Text |
|---|---|---|
| A8 | BO Report Name | Workload report by service provider |
| B8 / C8 | BO Data Fields / SE fields | Consultant / Consultant |
| B9 / C9 | BO Data Fields / SE fields | Services / ? |
| B10 / C10 | BO Data Fields / SE fields | # of services / ? |
| B11 / C11 | BO Data Fields / SE fields | Workload Hours / ? |
| E8 | BO Reporting Sort Options | All clients, all service providers, front loaded within a date range. Total workload for each Consultant and all client |
| E9 | BO Reporting Sort Options | Individual clients by all service providers, front loaded within a date range |
| E10 | BO Reporting Sort Options | Offer to preview, print or email as a pdf or excel |

### Sheet `Operations`, rank list (columns F to H)

| Domestic Ops Back Office Reports (F2) | Rank (G2) | Phase 1/2 (H2) |
|---|---|---|
| Workload report by service provider | 1 | 1 |

### Sheet `Report List by RB`, row 10

Also exported to CSV, line 48 of `Extra docs/Business Owners List Reports- BO vs SE  data fields(Report List by RB).csv` and `Ops_data/Queries & Data Points/Business Owners List Reports- BO vs SE  data fields(Report List by RB).csv`.

| Cell | Column (row 1 header) | Text |
|---|---|---|
| B10 | Report category | Workload |
| E10 | (no header) | The data will come from SE. We need sample data and report format based on SE data. Report Count based on BO data |
| F10 | No of Reports | 4 |
| G10 | NCM schema status | SE only data source |

### Sheet `Final Reports List 5.29.26 RB`, row 13

| Cell | Text |
|---|---|
| G13 | Workload report by service provider |
| H13 / I13 | 1 / 1 |
| K13 | Data will come from SE, For BO data, ops will generate in BO and compare manually |

The title in A1 of that sheet and of `Final Reports List 5.29.26` reads:

> Final list reveiwed and approved by the business 5.29.26 - Pending reports needed for Accounting and Dave.

### Other cells in this workbook

| Sheet | Cell | Text |
|---|---|---|
| `Contents` | C6 to F6 | Workload Report / Bert / Ops / 1 (columns: Report List, Assigned to, Team, Phase) |
| `Contents` | K46 | Workload report by service provider (under Consolidated List) |
| `Final Reports List 5.29.26` | A4 to D4 | Workload report by service provider / Workload report by service provider / 1 / 1 |
| `Final Reports List 5.29.26 RB` | A4 | Workload report by service provider |
| `KM Working Doc` | A44 / B44 | Workload report by service provider / Y (columns: Consolidated List, Posted to Teams) |
| `Screen Shots ` | A41 / H41 | Workload report by service provider: / Report Sample |

### Screenshots on sheet `Screen Shots `

Both are anchored at row 42, under the cells A41 and H41.

![Report dialog: Service Provider, Front Load, eMail as Attachment](Workload_Report_Screenshots/10_bo_list_dialog_email_attachment.png)

![Report Sample for Alenja Alvarez](Workload_Report_Screenshots/11_bo_list_report_sample.png)

---

## 5. Trackers and report lists

### `Test/Tracker.xlsx`

**Identical copy:** `Test/final_solution/cube/Tracker.xlsx`

**Sheet `Tracker`, row 52** (header in row 2; last updated 2026-10-22)

| Column | Value |
|---|---|
| ID | 50 |
| Domain | Operations |
| Owner Team | Ops |
| Business Owner | Bert |
| Report Family | Workload |
| Sub-report / Variant | Workload by Service Provider (4 formats) |
| Phase 1 List Name | Workload |
| Legacy Artifact (.rpt / PBI) | BO report |
| Source System(s) | SE |
| In Scope (Ph 1) | Yes |
| Scope Decision / Reason | Data will come from SE; report count is based on BO. |
| SE Data Needed? | Yes |
| SE Mapping Status | Not Started |
| SE Mapping Notes / SE Objects | Need SE sample data and report format based on SE data. |
| Fact Loaded in DW? | No fact yet |
| DW Query Exists? | No |
| DW Query Result | N/A |
| Txn Query Exists? | No |
| DW vs Txn Reconciled? | N/A |
| Data Definitions Doc | No |
| Business Sample Provided | Yes |
| Build Status | Not Started |
| Notes | Added from Phase 1 business list — no query in inventory. |

**Sheet `Dashboard`, cell B29**

> • 5 in-scope sub-reports have no DW query (mostly SE-based survey/workload reports) — IDs 47, 48, 49, 50, 51.

**Sheet `How To Use`, cell C8**

> SE Data Needed? = Yes when the report must read SE data (surveys, workload, diversity field, SE file ledger). TBD means: confirm whether SE files must also appear in the BO-based report.

### `Ops_data/Queries & Data Points/currentTracker.xlsx`

**Sheet `Tracker (RB list)`, rows 25 to 28.** The same text appears on all four rows, with Report 1 to Report 4 in column B.

> Workload - Report 1 (name TBC)

> RB: Workload = 4 reports, data from SE; need sample data / format

Other values on those rows: Operations, TBC, Not Started in every status column, New (from RB list), SE only data source.

**Sheet `Detail_Sheet`, rows 19 to 22.** The same text appears on all four rows.

| Column | Value |
|---|---|
| Domain | Operations |
| RB List Change | New (from RB list) |
| Overall Status | Not Started |
| RB Report (Count) | Workload (4) |
| Business Notes (RB) | The data will come from SE. We need sample data and report format based on SE data. Report Count based on BO data |
| NCM Schema Status | SE only data source |
| Gap / Next Action | NO QUERY YET. SE data source - need sample data and report format; get the 4 report names from RB |

### `Ops_data/Queries & Data Points/Reporting Work Tracker (Report Wise)(OPS Report Data Tracker).xlsx`

**Sheet `OPS Report Data Tracker`, rows 30 to 33** (No 13 to 16). Also exported to CSV, lines 30 to 33 of `Ops_data/Queries & Data Points/Reporting Work Tracker (Report Wise)(OPS Report Data Tracker).csv`.

| No | Domain | Report Family | Sub-report / Variant | In Scope (Ph 1) | DW Query Exists? | Txn Query Exists? | Scope Decision / Reason |
|---|---|---|---|---|---|---|---|
| 13 | Operations | Workload | Report 1 (name TBC) | Yes | No | No | RB Report List: added - RB: Workload = 4 reports, data from SE; need sample data / format |
| 14 | Operations | Workload | Report 2 (name TBC) | Yes | No | No | RB Report List: added - RB: Workload = 4 reports, data from SE; need sample data / format |
| 15 | Operations | Workload | Report 3 (name TBC) | Yes | No | No | RB Report List: added - RB: Workload = 4 reports, data from SE; need sample data / format |
| 16 | Operations | Workload | Report 4 (name TBC) | Yes | No | No | RB Report List: added - RB: Workload = 4 reports, data from SE; need sample data / format |

Progress % for these rows is 0, and RB List Change is "New (from RB list)".

### `Test/Ops Reports Details.xlsx`

**Identical copy:** `Test/final_solution/cube/Ops Reports Details.xlsx`

**Sheet `Updated Report List`**

| Cell | Text |
|---|---|
| B10 | Workload |
| Same row | The data will come from SE. We need sample data and report format based on SE data. Report Count based on BO data |
| Same row | 4 |
| I12 | Workload (with count 4 on the same row) |

### `Sharepoint/Phase 1 Report List as of 7.17.26.xlsx`

**Identical copy:** `Ops_data/sharepoint/Phase 1 Report List as of 7.17.26.xlsx`

Sheet `Sheet1`, title in A1: "Phase 1 Report List Summary based on Business Owners  (July 17, 2026)"

| Cell | Text |
|---|---|
| A32 / B32 | Workload / Ops |

---

## 6. Other business mentions

### `Reports/Report Improvement/SE Reports for CR 4.03.25.xlsx`

**Identical copy:** `Sharepoint/Report Improvement/SE Reports for CR 4.03.25.xlsx`

Sheet `Reports to Replicate in SE`, title in A1: "Reports Client Relations Needs in SE"

| Cell | Report | Path | Need |
|---|---|---|---|
| A34:C34 | Weighted Workload Report | Reports, Internal Reports | NOT NEEDED |
| A36:C36 | Workload Report | Reports, Internal Reports | NEEDED |

### `Reports/NCM Profile Information View for Approval 10.14.26.xlsx`

**Same sheet text in:** `Reports/Archive/NCM Profile Information View Approved 3.31.26.xlsx`, `Sharepoint/NCM Profile Information View Approved 3.31.26.xlsx`

Sheet `Workload Reports`:

| Row | Text |
|---|---|
| 1 | clientworkload _client summary with TE detail… / Client Name / # of services / workload hours / #of files |
| 2 | SrvcProviderworkload report / consultant / Serivice / workload hours / client |

### `Sharepoint/Client Note Explained - Supplier Usage and Active TE.txt`

**Location:** line 177, section "2.3 How users run it (from Ops sheet)". This section is about the Active TE report and mentions workload as a use of it.

> Bert: all clients for one service provider (review workload / reassign TEs);

---

## 7. Sample reports and screenshots

### Back Office menu location

**Location:** `dbt/ops-reports-screenshots.docx` (images only, no text)

Reports > Internal Reports contains both "Weighted Work Load Report" and "Workload Report".

![Back Office Reports menu, Internal Reports](Workload_Report_Screenshots/14_ops_back_office_menu_internal_reports.png)

### Monthly Distribution run for Company ABBE

**Location:** `dbt/ops-reports-screenshots.docx`

![Report dialog: Monthly Distribution, Company ABBE](Workload_Report_Screenshots/12_ops_dialog_monthly_distribution.png)

![Service Provider Workload Report, Active Files from 10/30/25 to 10/30/26](Workload_Report_Screenshots/13_ops_monthly_distribution_report.png)

![Overall Workload Summary, Monthly Distribution](Workload_Report_Screenshots/15_ops_monthly_distribution_overall_summary.png)

### Report dialog options

Labels read from the screenshots above:

| Group | Options |
|---|---|
| Title | Service Provider Workload Report |
| Top selections | Select Corporate Client, Select Service Provider, Select Profit Center/CAC, Parent Company |
| Date Range | Start Date, End Date |
| Report Type | Service Provider, Client Summary, Include TE Detail |
| Hours to Report | Monthly Distribution, Front Load All Hours |
| Report Output | Preview, Print, eMail as Attachment, Report in Excel Format |

### `ClientWorkLoad_Client Summary with TE detail and Frontloading all Hours.pdf`

**Location:** `Reports/Building Report Views/Ops Reports/`
**Identical copy:** `Sharepoint/Building Report Views/Ops Reports/`

Printed 03/13/26. Header: "Client Summary Workload Report", "Authorizations from 02/01/26 to 02/28/26", "Mercedes-Benz USA, LLC", "All Profit Centers".

![Client Summary PDF page 1](Workload_Report_Screenshots/16_pdf_client_summary_te_detail_page1.png)

![Client Summary PDF page 2](Workload_Report_Screenshots/16_pdf_client_summary_te_detail_page2.png)

![Client Summary PDF page 3, TE Detail](Workload_Report_Screenshots/16_pdf_client_summary_te_detail_page3.png)

### `SrvcProviderWorkLoad_Monthly Distribution.pdf`

**Location:** `Reports/Building Report Views/Ops Reports/`
**Identical copy:** `Sharepoint/Building Report Views/Ops Reports/`

Printed 03/13/26. Header: "Service Provider Workload Report", "Active Files from 02/01/26 to 02/28/26", "Mercedes-Benz USA, LLC", "All Profit Centers".

![Service Provider Monthly Distribution PDF page 1](Workload_Report_Screenshots/17_pdf_service_provider_monthly_distribution_page1.png)

![Service Provider Monthly Distribution PDF page 2](Workload_Report_Screenshots/17_pdf_service_provider_monthly_distribution_page2.png)

### `SrvcProviderWorkLoad.xls`

**Location:** `Reports/Building Report Views/Workload Reports/SrvcProviderWorkLoad.xls`
**Identical copy:** `Sharepoint/Building Report Views/Workload Reports/SrvcProviderWorkLoad.xls`

Report dated 04/08/26, "Active Files from 04/01/26 to 04/08/26", Mercedes-Benz USA, LLC, All Profit Centers.

| Sheet | Column headers (exact) |
|---|---|
| `Service Provider` | Service Description, # of Services, Workload Hours |
| `Service provider TE details` | Summary: same as above. TE detail, rows 73 and 74: TE File No, Name, Service, Auth/Srvc Date, Start Date, End Date, Complete / CancelDate, Month, Days, Workload Hours |
| `Client Summary TE details` | Summary, row 9: Client, # Services, Workload Hours, # Files. TE detail, rows 42 and 43: same as the TE detail above |

Layout text used by the reports:

```text
Total Workload:
Workload for 4 Files
Report Total  Workload:
5 Files
Overall Workload Summary
Summary Total Workload:
Total  Report Workload:
```

---

## 8. NCM Workload Detail View spec

**Location:** `Reports/NCM Workload Detail View Approved 4.13.26.xlsx`
**Identical copy:** `Sharepoint/NCM Workload Detail View Approved 4.13.26.xlsx`

### Sheet `General`

| Row | Item | Value |
|---|---|---|
| 1 | Component Name | NCM Workload Detail View |
| 2 | UDV | udv_Workload Detail_34 |
| 3 | Development Type | New Dynamic Report View |
| 4 | Variation Source (if applicable) | |
| 5 | Description | This view is a detailed of workflow actions with time and resources broken out by Role |
| 6 | Overall Requirements | 1. One row per Role/Resource per Action |
| 7 | Source: | |

### Sheet `Spec History`

| Date | Change | Reference |
|---|---|---|
| 2026-04-10 | Spec Created  | PBI 37098 |

### Sheet `Spec`

| Row | Field | Form | Section | Field | Calculation | Notes | Testing Notes |
|---|---|---|---|---|---|---|---|
| 2 | Profile Details |  |  |  |  |  |  |
| 3 | File # | NuCompass Profile (34.99.3400) | Key Information | File Number |  |  |  |
| 4 | File Status | NuCompass Profile (34.99.3400) | Key Information | File Status |  |  |  |
| 5 | File Status Date | NuCompass Profile (34.99.3400) |  | Date of Current File Status |  |  |  |
| 6 | Name | NuCompass Profile (34.99.3400) | General Information | Last Name, First Name |  |  |  |
| 7 | Employee ID | Program Master Fields |  | Employee Number |  |  |  |
| 8 | Division |  |  |  | New: For the Division Field for all Custom Views<br>1. If the Source Org is a Division or a Department, then Division = Source Name<br>2. If Source Org is a Company, then Division = Program Master Field Division (Division is the Alias Name) |  |  |
| 9 | Start Work | NuCompass Profile (34.99.3400) | Key Information | Work/Assignment Start Date |  |  |  |
| 10 | Employment Type | NuCompass Profile (34.99.3400) | Professional Information | Employment Status |  |  |  |
| 11 | Policy | NuCompass Profile (34.99.3400) | Program Details | Policy |  |  |  |
| 12 | Approver | NuCompass Profile (34.99.3400) | Program Details | Approver |  |  |  |
| 13 | Dest Work Country | NuCompass Profile (34.99.3400) | Locations | Destination Work Country |  |  |  |
| 14 | Dept Work Country | NuCompass Profile (34.99.3400) | Locations | Departure Work Country |  |  |  |
| 15 | Move Complete Date | NuCompass Profile (34.99.3400) | Key Information | Move Complete Date |  |  |  |
| 16 | Move Type | NuCompass Profile (34.99.3400) | Program Details | Domestic Move Type name or International Move Type name | If "Domestic or International" = "International", then International Move Type name, otherwise, Domestic Move Type name |  |  |
| 17 | Consultant | NuCompass Profile (34.99.3400) | Key Information | Consultant |  |  |  |
| 18 | Client Descriptor 1 | Program Master Fields |  | Client Descriptor 1 |  |  |  |
| 19 | Client Descriptor 2 | Program Master Fields |  | Client Descriptor 2 |  |  |  |
| 20 | Client Descriptor 3 | Program Master Fields |  | Client Descriptor 3 |  |  |  |
| 21 | Client Descriptor 4 | Program Master Fields |  | Client Descriptor 4 |  |  |  |
| 22 | Client Descriptor 5 | Program Master Fields |  | Client Descriptor 5 |  |  |  |
| 23 | Client Descriptor 1 Drop List | Program Master Fields |  | Client Descriptor 1 Drop List |  |  |  |
| 24 | Client Descriptor 2 Drop List | Program Master Fields |  | Client Descriptor 2 Drop List |  |  |  |
| 25 | Client Descriptor 3 Drop List | Program Master Fields |  | Client Descriptor 3 Drop List |  |  |  |
| 26 | Client Descriptor 4 Drop List | Program Master Fields |  | Client Descriptor 4 Drop List |  |  |  |
| 27 | Client Descriptor 5 Drop List | Program Master Fields |  | Client Descriptor 5 Drop List |  |  |  |
| 28 | Corp Code | Program Master Fields |  | Corp Code |  |  |  |
| 29 | Cost Center | Program Master Fields |  | Cost Center |  |  |  |
| 30 | Resource Role | Workflow Action | Action Template: Time and Resources | Role |  |  |  |
| 31 | Resource User Name | Service Control |  | Name of User assigned to Resource Role for the Workflow |  |  |  |
| 32 | Resource Time | Workflow Action | Action Template: Time and Resources | Hours/Minutes (Hours + Minutes as a decimal) |  |  |  |
| 33 | Resource Description | Workflow Action | Action Template: Time and Resources | Description |  |  |  |
| 34 | Action ID | Workflow Action |  | Action UID |  |  |  |
| 35 | Action Subject | Workflow Action |  | Subject |  |  |  |
| 36 | Action To Role | Workflow Action | Action Template | To Role |  |  |  |
| 37 | Action To User Name | Workflow Action |  |  |  |  |  |
| 38 | Action Status Group | Workflow Action | Action Template | Service Status |  |  |  |
| 39 | Action Priority | Workflow Action |  | Priority |  |  |  |
| 40 | Action Group | Workflow Action | Action Template | Action Group |  |  |  |
| 41 | Action Status | Workflow Action |  | Status |  |  |  |
| 42 | Action Initiated Date | Workflow Action |  | Date Action became Initiated |  |  |  |
| 43 | Action Started Date | Workflow Action |  | Date Action became Started |  |  |  |
| 44 | Action Completed Date | Workflow Action |  | Date Action became Completed |  |  |  |
| 45 | Action Cancelled Date | Workflow Action |  | Date Action became Cancelled |  |  |  |
| 46 | Service Name | Service Control |  | Service Type Description |  |  |  |
| 47 | Workflow Template Name | Service Control |  | Workflow Template Name |  |  |  |
| 48 | Workflow Name | Service Control |  | Service Label |  |  |  |
| 49 | Service Status | Service Control |  | Service Status |  |  |  |
| 50 | Service Status Date | Service Control |  | Date of Current Service Status |  |  |  |
| 51 | Program Status | Profile / Program Management |  | Program Status |  |  |  |
| 52 | Program Status Date | Profile / Program Management |  | Date of Current Program Status |  |  |  |

---

## 9. Service Engine objects

### View `udv_workload_view_34`

**Location:** `CPC_data/SP/allReportView.txt`, lines 14869 to about 15031
**Also listed in:** `dbt/mapping/alltableviewsall.txt:5899`

Header, lines 14870 to 14880:

```text
*  Object Name: udv_workload_view_34
*  Object Type: View
*  Programmer : SS
*  Create Date: 04/22/2026
*  Description: Custom Adhoc report view for NUCOMPASS
*
************************************************************************** 
*  Revision History:
*  04/22/2026 - SE - 37581 - NCM - Workload View
```

Resource columns from the view:

```sql
'Resource Role' = r1.role_desc,
'Resource User Name' = c1.cont_fname + ' ' + c1.cont_lname,
'Resource Time' = cast(round((((time_hh * 60) + time_mm)/60.0),2) as float),
'Resource Description' = ar.descr,
```

Core joins from the view:

```sql
join service s with (nolock) on s.program_uid = p.program_uid
join code SVCTYP with (nolock) on SVCTYP.code_type = 'SVCTYP' and SVCTYP.code_value = s.serv_type
join workflow_template wt with (nolock) on wt.workflow_template_uid = s.workflow_template_uid
join action a with (nolock) on a.act_serv_uid = s.serv_uid
join process_definition pd with (nolock) on pd.proc_uid = a.act_proc_uid
join action_resource ar with (nolock) on ar.action_template_uid = a.act_template_uid
join role r1 with (nolock) on r1.role_uid = ar.role_uid
```

### Table `contact_workload_summary`

**Schema location:** `CPC_data/SP/2seSchema.txt:4680-4684` (also `CPC_data/2seSchema.txt`)

```text
contact_workload_summary	cont_uid	int
contact_workload_summary	cont_cur_service_count	int
contact_workload_summary	cont_past_service_count	int
contact_workload_summary	cont_cur_poc_count	int
contact_workload_summary	cont_cur_spoc_count	int
```

| What | Location |
|---|---|
| Data extract, 262 rows plus header | `Test/SE_DEV(main)/dbo.contact_workload_summary.csv`, also `Test/final_solution/cube/SE_DEV(main)/dbo.contact_workload_summary.csv` |
| Sample rows | `CPC_data/SP/5seRows.txt`, from line 886 |
| Object listing | `dbt/mapping/alltableviewsall.txt:3855` |
| Used in report views as `cws` | `CPC_data/SP/allReportView.txt`, lines 855-858, 1039, 1380-1383, 1419, 8690-8693, 8843, 9019-9022, 9057 |
| Listed in data groups | `Test/SE_DEV(main)/dbo.report_data_group.csv`, lines 31, 39, 58, 227 (Supplier, Client Contact, Supplier Contact, Client Organzation) |
| Table attribute entry | `Test/SE_DEV(main)/dbo.table_attribute.csv:246` |
| Replication article | `Test/SE_DEV(main)/dbo.sysarticles.csv:116` |

Example from `dbo.report_data_group.csv`, line 39:

> Includes fields from contact,cont_type,contact_login,contact_role,contact_team,contact_workload_summary,x_contact,x_contact_designations,x_contact_language. Each row represents a single Client Contact.

### Other SE object

`ap_v2BatchUpdateWorkload`, a stored procedure, listed at `dbt/mapping/alltableviewsall.txt:2253`. Its body was not found in the folder.

---

## 10. Legacy Back Office stored procedures and tables

**Location of all procedures:** `CPC_data/SP/allReloSP.csv`

| Procedure | Line | Parameters |
|---|---|---|
| `WeightedWorkLoad` | 12880 | `@StartDate DATETIME, @EndDate DATETIME, @Initials VARCHAR(4), @CorpCode VARCHAR(4)` |
| `pr_GetWorkLoadServiceHours` | 30279 | `@initials varchar(4), @Hours varchar(5)` |
| `pr_GetWorkLoadTransferees` | 30517 | `@CorpCode, @ParentRollup, @ServiceProvider, @ProfitCenter, @CAC, @StartDate, @EndDate` |
| `pr_GetWorkLoadServiceHoursTEDetail` | 30906 | `@initials varchar(4), @Hours varchar(5)` |
| `pr_GetWorkLoadTransfereesByAuthDate` | 31167 | `@CorpCode, @ParentRollup, @ServiceProvider, @ProfitCenter, @CAC, @StartDate, @EndDate` |

### Hours calculation, `pr_GetWorkLoadServiceHours`

When `@Hours='MONTH'`, lines 30297 to 30301:

```sql
		sum(convert(numeric(10,2),round(isnull((st.days * (sh.hours/30)),0.00),2),1)) as workloadhours 
		--sum(convert(numeric(10,2),round(isnull(((sh.hours)),0.00),2),1)) as workloadhours 
		from vwtefullservicelist vw
		inner JOIN dbo.tblTmpServiceHours st on vw.tefileno=st.tefileno and vw.servicecode=st.servicecode and vw.servicetype=st.servicetype
```

Otherwise, line 30317:

```sql
		sum(sh.hours) as workloadhours 
```

### Hours calculation, `pr_GetWorkLoadServiceHoursTEDetail`

Line 30932:

```sql
		convert(numeric(10,2),round(isnull((st.days * (sh.hours/30)),0.00),2),1) as workloadhours
```

Line 30959, in the branch that is not `MONTH`:

```sql
		0 as workloadhours
```

### Service selection, `pr_GetWorkLoadTransferees`

Lines 30552 to 30566:

```sql
	and (@ServiceProvider='' or vw.SrvcProvider = @ServiceProvider)
	and (
	   (
		 ((vw.ServiceStartDate is not null) and (vw.completedate is null and vw.canceldate is null) and (vw.ServiceStartDate <= @EndDate)) or
		 ((vw.ServiceStartDate is null) and (vw.completedate is null and vw.canceldate is null) and (vw.AuthDate <= @EndDate))
		)
	or (
		 ((vw.completedate is not null) and (vw.completedate >= @startdate) and ((vw.AuthDate <= @EndDate) or (vw.ServiceStartDate<=@EndDate))) or
		 ((vw.canceldate is not null) and (vw.canceldate >= @startdate) and ((vw.AuthDate <= @EndDate) or (vw.ServiceStartDate<=@EndDate))) 
		)
	)
	and ((@profitcenter='' or vw.profitcenter=@profitcenter))
	and vw.CorpCode <> 'GLC2' and vw.CorpCode<>'ACME'
	and vw.UserType=1 and vw.DisplayType='C' --and vw.tefileno='BIRD100018'
	and vw.ComponentService=0 and (st.OnHold <> 1 or st.OnHold is null)
```

### Weighted workload, `WeightedWorkLoad`

Lines 12939 to 12947:

```sql
              Multiply the Weight in RAServices with count of Services
**************************************************************************************************/
INSERT INTO dbo.tblTmpWeightedWorkLoad
SELECT ProfitCenter, ServiceCode,  NoOfSrvcs* Weight AS TotalWeight, @Initials AS Initials, NoOfSrvcs, ServiceFee, ServiceType
FROM #TMP_NumberofSrvcs WITH (NOLOCK)  WHERE ServiceType=1

INSERT INTO dbo.tblTmpWeightedWorkLoad
SELECT ProfitCenter, ServiceCode,   NoOfSrvcs* WeightIntl AS TotalWeight, @Initials AS Initials, NoOfSrvcs, ServiceFee, ServiceType
FROM #TMP_NumberofSrvcs WITH (NOLOCK)  WHERE ServiceType=2
```

Comments in the procedure:

```text
/** EAR Sept 10, 2002 WO # 7720
modified to separate by service type to use different weights for Internationl vs. Domestic **/
```

```text
/* jpacheco 12/30/03 - at some point CancelDate Is Null was taken out of the other weighted workload reports, so I'm taking out of here to be
			consistent.  I will comment all places taken out.
```

### Table `tblTmpWeightedWorkLoad`

| What | Location |
|---|---|
| Columns: ProfitCenter, ServiceCode, TotalWeight, Initials, NoOfSrvs, ServiceFees, ServiceType | `CPC_data/SP/ReloSchema.csv:9657-9663` |
| Column list | `CPC_data/SP/2ReloSCHEMA.csv`, from line 10531 |
| Sample rows | `CPC_data/SP/5ReloRows.csv`, from line 5051 |
| Sample JSON | `CPC_data/SP/Allrelo.csv:674` |

---

## 11. dbt models

These models were written on 2026-11-04 from 12:04, while this document was being compiled, and `int_se_fact_Workload.sql` was changed again at 12:25. Someone is still working on them, so this section is a snapshot taken at 12:26 and the files may have moved on.

### `dbt/dbt/models/marts/Facts/FactWorkload.sql`

Lines 1 to 7:

```sql
-- Gold FactWorkload: Service Engine rows only (int_se_fact_Workload), one per workflow action.
-- Replaces udv_workload_view_34 (NCM Workload adhoc report): same columns, same names, same order.
-- No NCM counterpart, so no union model and no KeyMap IDs: [Action ID] (action.act_uid) is the key.
-- The NCM index post-hook finds no rows for this table and does nothing.
{{ config(
    post_hook=["create unique clustered index CIX_FactWorkload_ActionID on {{ this }} ([Action ID])"]
) }}
```

### `dbt/dbt/models/intermediate/SE/service_engine/fact/int_se_fact_Workload.sql`

Lines 1 to 15:

```text
{# FactWorkload -- grain: one row per workflow action (action x its action_resource).
   Port of Service Engine's udv_workload_view_34 (NCM Workload adhoc report, ticket 37581).
   Same joins and inner/left choices as the view, so the same rows; gold FactWorkload
   renames the columns to the report's names.

   Differences from the view, none of which change the rows:
     - the view's left join to cust_address (ORIGIN) is dropped: no column is selected from it,
       and it could only ever duplicate rows (checked 2026-11-04: no customer has two ORIGIN rows).
     - none other: "Client Descriptor 1 Drop List" is kept although no program has that label
       today (see int_se__master_fields), so it is NULL, as in the view.

   Performance: ~30 joins over the computed staging views made SQL Server pick a plan that
   re-ran lookups per row (the build ran > 10 min for ~2k rows). So every lookup input is cut
   down first: master_fields aggregates only the 15 labels used (int_se__master_fields' full
   80-label pivot was the worst offender), and code keeps only the code types the report reads. #}
```

Lines 96 to 101:

```sql
    -- Resource (who is expected to do the action, and for how long)
    r1.role_desc                                           as resource_role,
    c1.cont_fname + ' ' + c1.cont_lname                    as resource_user_name,
    cast(round((((ar.time_hh * 60) + ar.time_mm) / 60.0), 2) as float)
                                                           as resource_time,
    ar.descr                                               as resource_description,
```

### `dbt/dbt/models/marts/_gold.yml`

Lines 886 to 893:

```yaml
  - name: FactWorkload
    description: >
      Service Engine only (no NCM rows, no KeyMap IDs): port of udv_workload_view_34,
      one row per workflow action. Column names match the legacy report view.
    columns:
      - name: Action ID
        quote: true
        data_tests: [unique, not_null]
```

### `dbt/dbt/models/_sources.yml`

Lines 79 to 82:

```yaml
      # Added for FactWorkload (udv_workload_view_34): service workflow actions.
      # No ct_* change tables exist for these, so they are snapshot-only.
      - name: action                          # workflow step on a service
      - name: action_resource                 # estimated time + resource role per action template
```

### Staging models

`dbt/dbt/models/staging/service_engine/snapshot/stg_se__action.sql`, lines 4 and 5:

```text
  One row per act_uid: a workflow step (task) on a service
  (act_serv_uid -> service.serv_uid). Read by the Workload report.
```

`dbt/dbt/models/staging/service_engine/snapshot/stg_se__action_resource.sql`, lines 4 and 5:

```text
  Estimated effort (time_hh / time_mm) and the resource role for an
  action template (action_template_uid -> action.act_template_uid).
```

### Mentions of `udv_workload_view_34` in other models

`dbt/dbt/models/intermediate/SE/calculations/int_se__form_3400_customer_34.sql`, lines 6 and 7:

```text
    NCM udv views use for these exact fields (confirmed in
    udv_profile_information_view_34 / udv_workload_view_34):
```

`dbt/dbt/models/intermediate/SE/calculations/int_se__customer_domestic_intl.sql`, lines 8 and 9:

```text
    views either -- every udv_*_view_34 that needs it compares the raw value
    directly against the literal 'INTERN' (see udv_workload_view_34,
```

### Run log

**Location:** `dbt/dbt/logs/dbt.log`, line 105708

```text
12:06:11.703047 [info ] [Thread-2 (]: 20 of 23 OK created sql view model intermediate.int_se_fact_Workload ........... [OK in 0.16s]
```

The next step started at 12:06:11. As of 12:26 the log has no OK or ERROR line for it:

```text
12:06:11.708865 [info ] [Thread-1 (]: 21 of 23 START sql table model dbo.FactWorkload ................................ [RUN]
```

---

## 12. Searched but not quoted

| Item | Why it is not quoted |
|---|---|
| `Reports/Ops Reports_Data def and sample/REM/REMSampleData.xlsx` | False match: expense text such as "Front load wash..." |
| `CPC_data/SP/BASEDATA.csv`, `CPC_data/SP/AppliedbyDBT.csv`, `CPC_data/SP/ChangesOFmAIN.csv` | False match: job titles such as "Coordinator-System Mtc. Workload" and "Network Load Control" |
| `airflow/ncm-airflow/config/airflow.cfg`, lines 2246 and 3193 | False match: Airflow's own technical "workload" settings |
| `dbt/mapping/AlldevView.txt`, lines 90 and 363 | Other view definitions that reference `contact_workload_summary` |
| `dbt/dbt/target/` | Generated copies of the dbt models in section 11 |
| `Ops_data/action.csv` | Raw data for the `action` table with 84,693 lines. It holds no written points about the report |
| `*.zip` files | Not opened |
| `*.mp4` files (2) | Video content could not be searched |
| `*.msg` email files (8) | Searched as plain text only, with no workload match. Text stored in compressed form would not have been searched |
| `Reports/Building Report Views/Expense Mgt Reports/DNU Client Expense Payment Example 1.xlsx` | Could not be opened: the file is not a valid xlsx |

---

## 13. Observations (mine, not from the source files)

These are my own notes on where the sources disagree or leave gaps. Nothing here was checked against a database.

1. **The tracker is out of date against dbt.** `Test/Tracker.xlsx` row 52 says "No fact yet" and "Not Started" (last updated 2026-10-22), but `FactWorkload` now exists in dbt. As of 12:26 the log shows no OK or ERROR line for the gold model, so I can't say whether the table was built.
2. **`FactWorkload` may not match the agreed grain.** The spec says "One row per Role/Resource per Action", and the intermediate model says "action x its action_resource". Yet the gold model puts a unique clustered index and a `unique` test on `[Action ID]` alone. If any action has more than one resource row, the index and the test would fail.
3. **The Detail View is not the same thing as the Back Office Workload Report.** `FactWorkload` holds action-level resource time. The Back Office report shows service-level hours per consultant or client. None of the dbt models contain the front-load or monthly distribution logic, `tblServiceHours` values, the on-hold filter, or the active-services rule.
4. **Spec and view differ.** The spec names the UDV `udv_Workload Detail_34`, while the actual view is `udv_workload_view_34`. The spec lists `File Status Date`, which the view does not have. The view has `Client`, which the spec does not list.
5. **The monthly split does not add up.** The Word document says BVO/MVP is 15.5 hours, but the listed months total 12.25 because month 12 is blank. That leaves 3.25 hours unaccounted for.
6. **The weighted workload example does not calculate.** The Word document says 2.25 / 28 gives .089, but it gives about .080. A result of .089 would match 2.50 / 28.
7. **Two placeholders were never filled in.** The Word document still says "WE NEED TO KNOW WHAT THIS IS CALLED" and "NAME OF THE REPORT". The report dialog suggests the answer is "Monthly Distribution", but this needs business confirmation.
8. **"Active only" differs from the code.** The Word document says a closed service drops off the report. `pr_GetWorkLoadTransferees` also includes services completed or cancelled on or after the start date. The on-hold rule does match the code.
9. **The two report headers appear tied to the Hours option.** Front Load samples say "Authorizations from" and Monthly Distribution samples say "Active Files from". That suggests `pr_GetWorkLoadTransfereesByAuthDate` serves Front Load and `pr_GetWorkLoadTransferees` serves Monthly Distribution, but I found nothing that confirms it.
10. **The report names are known but still marked TBC.** `currentTracker.xlsx` and the Reporting Work Tracker say "name TBC", while `Phase 1 Ops Reports.xlsx` already names the four variants.
11. **Weighted Workload may be out of scope.** The Word document describes it and the Back Office menu lists it, but `SE Reports for CR 4.03.25.xlsx` marks it "NOT NEEDED". That file is the Client Relations list, so Ops should confirm.
