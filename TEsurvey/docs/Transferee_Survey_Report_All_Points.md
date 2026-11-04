# Transferee Survey Report: All Points Found, With File Locations

Compiled 2026-11-04 from the files in the `dwh` folder. No database was connected to or queried. The dbt run results in section 11 come from reading the existing log file only.

**How to read this file**

- Text in quote blocks and code blocks is copied **exactly as written in the source**, including its spelling mistakes (for example "requireing", "requeest", "Feed Bak", "Transfee").
- Every point has a **Location**. Paths are relative to the `dwh` folder. Excel locations are given as sheet and cell.
- Where a file exists in several folders, the copies are listed once. They were checked as identical unless stated otherwise.
- Screenshots are stored in `Transferee_Survey_Report_Screenshots/`, next to this file. Keep the two together so the images display.
- Section 13 is the only part that is not source text. It holds my own observations and is labelled as such.
- `dbt/` was being reorganised while this was compiled. Paths are as of 16:45 on 2026-11-04.

**Names used for this report**

| Name in the source | Where it is used |
|---|---|
| TE Survey | Ops requirements sheet, Back Office menu item, `Phase 1 Report List` row 29 |
| Transferee Survey | Supplier Mgt requirements sheet, Back Office menu folder, Report List by RB |
| Transfee Survey | `Phase 1 Report List` row 30 (misspelled in the source) |
| Transferee Survey (incl. Comments) | Trackers and the DE team screenshot document |
| ROL Survey | Title of the Back Office report dialog |
| Satisfaction Survey Detail View | NCM view spec |
| Customer Satisfaction Survey (0.0.164) | Service Engine form |

**Contents**

1. [TE Survey requirements (Ops)](#1-te-survey-requirements-ops)
2. [Transferee Survey requirements (Supplier Mgt)](#2-transferee-survey-requirements-supplier-mgt)
3. [Phase 1 Ops Reports summary](#3-phase-1-ops-reports-summary)
4. [Business Owners report list](#4-business-owners-report-list)
5. [Trackers and report lists](#5-trackers-and-report-lists)
6. [Data definitions](#6-data-definitions)
7. [Sample reports and screenshots](#7-sample-reports-and-screenshots)
8. [NCM Satisfaction Survey View spec and test files](#8-ncm-satisfaction-survey-view-spec-and-test-files)
9. [Service Engine objects](#9-service-engine-objects)
10. [Legacy Back Office objects](#10-legacy-back-office-objects)
11. [dbt models](#11-dbt-models)
12. [Related reports and items searched but not quoted](#12-related-reports-and-items-searched-but-not-quoted)
13. [Observations (mine, not from the source files)](#13-observations-mine-not-from-the-source-files)

---

## 1. TE Survey requirements (Ops)

**Location:** `Sharepoint/Phase 1 Report Requirements - Ops.xlsx`, sheet `TE Survey`
**Identical copies:** `Extra docs/Phase 1 Report Requirements - Ops.xlsx`, `Ops_data/sharepoint/Phase 1 Report Requirements - Ops.xlsx`
**Text-only CSV export of the same sheet:** `dbt/Phase 1 Report Requirements - Ops(TE Survey).csv` (holds no images)

| Cell | Text |
|---|---|
| A1 | Backoffice Report |
| A2 | Description |
| A3 | How it is used |
| A4 / C4 | Path to Report / Reports/Navigator/Survey Reports |
| A5 | Report selections |
| A6 | Which are the most commonly used Filters |
| A10 | Note, there are various report formats this report can be run in. |
| A12 | The first example is based on the report format = Overall Roll Up, which is the format Bert used when previously sharing screenshots. |
| A13 | The second example is the Detailed Survey Report which is what  BPD uses the report to manage the weekly "Surveys Requiring Review". |
| A14 | KM TO CONFIRM WHICH FORMAT ANNA USES |
| A15 | Bert and Lorrie, do you ever use the Surveys Requiring Action or the TE Detail Comment Report? |
| A16 | BD: I depend on the surveys requireing action report that Karen sends out weekly, so I do not run that report myself. I do run the TE detail comment report on rare occasion, but I primarily run the overall report, either by all providers or by individual provider, to calculate the WOW Factor and Ace Award scores. |
| A17 | I know the DCR's run this report by individual client when preparing for annual reviews or quarterly reporting |
| A18 | LK   - I run the TE Detail Comment report for Sales/Marketing - we also want the ability to run all reports in adobe or excel |
| A21 | TE Survey - Survey Overall Roll Up |
| A62 | TE Survey - Detailed Survey Report |
| A64 | Note to Ruchika, the report output is based on which services the TE receives. |

The Description, How it is used, Report selections and Filters rows are blank in the source. The business explanation is only in the cells above.

The sheet also lists the report in `Instructions!N3` as "TE survey ". The `Instructions` sheet of the Client Relations and Finance & Dave workbooks has "TE Survey" at A54 and "Survey report when run by Deatiled Survey Report" at A98.

### Screenshots on the TE Survey sheet

**Rows 23 to 61, Overall Rollup.** Dialog at A23, report at M23.

![Report dialog: Overall Rollup](Transferee_Survey_Report_Screenshots/02_ops_dialog_overall_rollup.png)

![Survey Overall Rollup, All Clients, 07/01/26 to 07/02/26](Transferee_Survey_Report_Screenshots/03_ops_overall_rollup_report.png)

**Rows 65 to 102, Detailed Survey Report.** Dialog at A65, report at M66.

![Report dialog: Detailed Survey Report](Transferee_Survey_Report_Screenshots/04_ops_dialog_detailed_survey.png)

![Detailed Survey Report, Survey ID 45,511](Transferee_Survey_Report_Screenshots/05_ops_detailed_survey_report.png)

**Rows 106 to 130, TE Detail Comments Report.** Dialog at A106, report at L106. There is no cell label for this pair.

![Report dialog: TE Detail Comments Report](Transferee_Survey_Report_Screenshots/06_ops_dialog_te_detail_comments.png)

![TE Detail Comments Report in Excel](Transferee_Survey_Report_Screenshots/07_ops_te_detail_comments_report.png)

---

## 2. Transferee Survey requirements (Supplier Mgt)

**Location:** `Sharepoint/Phase 1 Report Requirements - Supplier Mgt1.xlsx`, sheet `Transferee Survey`
**Identical copy:** `Ops_data/sharepoint/Phase 1 Report Requirements - Supplier Mgt1.xlsx`

| Cell | Text |
|---|---|
| A1 / C1 | Backoffice Report / Transferee Survey |
| A2 | Description |
| A3 | How it is used |
| A4 / C4 | Path to Report / Reports/Navigator/Transferee Survey |
| A5 | Report selections |
| A6 | Which are the most commonly used Filters |
| A9 | Note to Ruchika - report output varies based on the services the TE is authorized for. |
| A10 | SM does not use this particular report but the data from this report is required and  pulls to the "Survey by Supplier" report that we use to manage performance. |

### Screenshots on the Transferee Survey sheet

**L1, Back Office menu.** The menu path is Reports > Navigator > Transferee Survey, with three items: TE Survey, Survey Follow Up Report, Survey Audit Report. The source image also shows a second monitor with a Teams chat list, which I cropped out.

![Back Office menu: Reports, Navigator, Transferee Survey](Transferee_Survey_Report_Screenshots/01_bo_menu_navigator_transferee_survey.png)

**A14, dialog. L14 and L51, Detailed Survey Report for Survey ID 45,484.** The report notes: "NOTE:  Report only includes questions TE responded to."

![Report dialog: Detailed Survey Report](Transferee_Survey_Report_Screenshots/08_sm_dialog_detailed_survey.png)

![Detailed Survey Report page 1](Transferee_Survey_Report_Screenshots/09_sm_detailed_survey_page1.png)

![Detailed Survey Report page 2](Transferee_Survey_Report_Screenshots/10_sm_detailed_survey_page2.png)

---

## 3. Phase 1 Ops Reports summary

**Location:** `Sharepoint/Phase 1 Ops Reports.xlsx`

### Sheet `Ops Phase 1 Reports`, row 8

| Cell | Text |
|---|---|
| A8 / B8 | 4 / TE Survey |
| C8 | Survey Reports, Reports/Navigator/Survey Reports |
| D8 | Bert Dodson, Lorrie Kaiser |
| E8 | 3 |
| F8 | Overall Roll Up by all or individual provider to calculate WOW Factor and Ace Award scores. DCRs run by client for annual reviews / quarterly reporting. TE Detail Comment report run for Sales/Marketing. Detailed Survey Report used by BPD for weekly 'Surveys Requiring Review'. |
| G8 | Client; Date range; Service Provider; Service; Show metric box. Output to PDF or Excel. |
| H8 | 3 |
| I8 / J8 | SE only / SE only data source |
| K8 | None yet |
| L8 | Report output depends on which services the TE received. Supplier Mgt has a related Transferee Survey / Survey by Supplier report. |
| M8 | KM to confirm which format Anna uses. Need screenshots / sample data from SE. |
| N8 | Not Started |

### Sheet `Report Variants`, rows 11 to 13

| Report | Variant | Use | Sample file |
|---|---|---|---|
| TE Survey | Survey Overall Roll Up | WOW Factor / Ace Award scoring by provider; DCR client reviews | Ops Reports/Survey Report.xls |
| TE Survey | Detailed Survey Report | Weekly 'Surveys Requiring Review' (BPD) | Phase 1 Report Requirements - Ops.xlsx / TE Survey |
| TE Survey | TE Detail Comment Report | Comments for Sales / Marketing | Phase 1 Report Requirements - Ops.xlsx / TE Survey |

### Sheet `Open Questions`, rows 7 and 8

| # | Report | Question | Owner | Answer |
|---|---|---|---|---|
| 3 | TE Survey | Which survey format does Anna use? | Karen Meisel | Blank |
| 4 | TE Survey / Survey Follow Up / Workload | Provide SE sample data and screenshots so the SE-based report formats can be designed. | Ops / SE team | Blank |

---

## 4. Business Owners report list

**Location:** `Reports/Business Owners List Reports- BO vs SE  data fields.xlsx`
**Near copy:** `Sharepoint/Business Owners List Reports- BO vs SE  data fields.xlsx` (same survey text)
**Other version:** `Reports/Building Report Views/Ops Reports/Reports- BO vs SE  data fields.xlsx` (has `Transferee survey` at `SM Reports!H9`, not H7)
**CSV of `Report List by RB`:** `Ops_data/Queries & Data Points/Business Owners List Reports- BO vs SE  data fields(Report List by RB).csv`, lines 32 and 33

### Sheet `Operations`, BO fields and sort options (rows 27 to 37)

| Cell | Text |
|---|---|
| A27 | TE survey |
| A28 | We are changing to a 5 star format |
| B27 | Ratings for each question in the survey: |
| B28 to B32 | Very Dissatisfied, Dissatisfied, Somewhat Satisfied, Satisfied, Very Satisfied |
| B34 | Percentage of service satisfation: |
| B35 | Top Box (# of Very Satisfied / total # of responses) |
| B36 | Top 2 Box (# of Satisfied & Very Satisfied / total # of responses) |
| B37 | Top 3 Box (# of Somewhat Satisfied, Satisfied and Very Satisfied / total # of responses) |
| C27 | ? |
| E27 | Sort by all clients or individual clients including parent company rollup |
| E28 | Sort by Consultant, profit center and report format (overall rollup or individual transferee |
| E29 | Offer to group by client or by policy |
| E30 | Offer to sort by Top box, Top 2 box or top 3 box |
| E31 | Offer a date range to pull survey results |
| E32 | Offer to sort by transferee permissiion |
| E33 | Offer to sort by International or Domestic |
| E34 | Offer to preview, print or email as a pdf or excel |

### Ranks

| Location | Report | Rank | Phase | Prepared by |
|---|---|---|---|---|
| `Operations!F4:I4` | TE survey | 3 | 1 | Bert |
| `SM Reports!H7:J7` | Transferee survey | 8 | 1 | Blank |

### Sheet `Report List by RB`, row 6

| Cell | Text |
|---|---|
| B6 | Transferee Survey |
| C6 | Transferee Survey, Transferee Survey Comments |
| D6 | Client, Date Range, Service?, Show metric box |
| E6 | Need screeshots, sample data from SE. Ops and SM both have this report. I put screenshot in the Report Samples spreadsheet from business |
| F6 | 1 |
| G6 | SE only data source |

Row 2 (Survey by Supplier) adds a rule that applies here too. Cell E2 says:

> As confirmed earlier, we will build survey reports based on SE data.I put Screenshot of new questions and answers in the in another tab. The filters are applicable to all survey reports.
> Depending on the report, Profit center may refer to NCM divisions in BO. In SE we won't have profit centers. So we can remove this filter

### Sheet `Final Reports List 5.29.26 RB`

A1 says: "Final list reveiwed and approved by the business 5.29.26 - Pending reports needed for Accounting and Dave."

| Row | Report | Rank | Phase | K column |
|---|---|---|---|---|
| G15:K15 | TE survey | 3 | 1 | Data will come from SE, For BO data, ops will generate in BO and compare manually |
| G30:K30 | Transferee survey | 8 | 1 | Data will come from SE, For BO data, ops will generate in BO and compare manually |

The same names appear in `Contents!C9`, `Contents!K43`, `Contents!K44`, `KM Working Doc!A41:B42` (marked Y), and `KM Working Doc!H54` and `H72` ("TE Survey Reports").

### Screenshots on sheet `Screen Shots `

A87 says "TE Survey (Our current state process)" and J87 says "Report Sample:".

![Report dialog: Overall Rollup, eMail as Attachment](Transferee_Survey_Report_Screenshots/11_bo_list_dialog_overall_rollup_email.png)

![Rollup sample, Overall Performance rows](Transferee_Survey_Report_Screenshots/12_bo_list_rollup_sample.png)

---

## 5. Trackers and report lists

### `Test/Tracker.xlsx`

**Identical copy:** `Test/final_solution/cube/Tracker.xlsx`

Sheet `Tracker`, row 50:

| Column | Value |
|---|---|
| ID / Domain / Owner Team | 48 / Supplier / Supplier Mgt / Ops |
| Business Owner | Bert |
| Report Family / Variant | Transferee Survey / Transferee Survey + Comments |
| Phase 1 List Name | Transfee Survey / TE Survey |
| Legacy Artifact | BO TE Survey (Overall Rollup / Detailed) |
| Source System / In Scope | SE / Yes |
| SE Data Needed / SE Mapping Status | Yes / Not Started |
| SE Mapping Notes | Need screenshots and sample data from SE. Ops and Supplier Mgt both use this report. |
| Fact Loaded in DW? | No fact yet |
| DW Query / Txn Query | No / No |
| Filters | Client, Date range, Service?, Show metric box |
| Data Definitions Doc / Sample Provided | No / Yes |
| Build Status | Not Started |
| Notes | Added from Phase 1 business list — no query in inventory. |
| Last Updated | 2026-10-22 |

Other cells:

- `Decisions Log!B8:F8`: "Survey reports will be built on SE data. SE has no profit centers — drop that filter." Decided by Business (Supplier Mgt), affects tracker IDs 47, 48, 49, 50.
- `Dashboard!B29`: "• 5 in-scope sub-reports have no DW query (mostly SE-based survey/workload reports) — IDs 47, 48, 49, 50, 51."
- `How To Use!C8`: SE Data Needed is Yes "when the report must read SE data (surveys, workload, diversity field, SE file ledger)."

### `Ops_data/Queries & Data Points/currentTracker.xlsx`

| Location | Text |
|---|---|
| `Tracker (RB list)!A82:B82` | 46, Transferee Survey (incl. Comments) |
| `Tracker (RB list)!E82:M82` | All gates Not Started |
| `Tracker (RB list)!Q82` | RB: 1 report (Survey + Survey Comments). Need SE sample data |
| `Detail_Sheet!H76` | Client; Date Range; Service?; Show metric box |
| `Detail_Sheet!L76` | Supplier management - Data point definitions.csv |
| `Detail_Sheet!R76` | NO QUERY YET. Need SE screenshots + sample data (see Report Samples spreadsheet) |

### `Ops_data/Queries & Data Points/Reporting Work Tracker (Report Wise)(OPS Report Data Tracker).xlsx`

Sheet `OPS Report Data Tracker`, row 85: ID 68, Supplier, Transferee Survey (incl. Comments), in scope Yes. H85 says "RB Report List: added - RB: 1 report (Survey + Survey Comments). Need SE sample data". A CSV of this sheet is next to the workbook (line 85).

### `Sharepoint/Phase 1 Report List as of 7.17.26.xlsx`

**Identical copy:** `Ops_data/sharepoint/Phase 1 Report List as of 7.17.26.xlsx`

| Cell | Report | Primary User |
|---|---|---|
| A29 / B29 | TE Survey | Ops |
| A30 / B30 | Transfee Survey | Supplier Mgt |

### `Reports/Report Improvement/SE Reports for CR 4.03.25.xlsx`

**Identical copy:** `Sharepoint/Report Improvement/SE Reports for CR 4.03.25.xlsx`

Sheet `Reports to Replicate in SE`:

| Row | Report | Menu | Status |
|---|---|---|---|
| A97:C97 | Transferee Survey | Navigator | NEEDED |
| A96:C96 | Centralized Survey Distribution Report | Navigator | NOT NEEDED |

### `Test/Ops Reports Details.xlsx`

**Identical copy:** `Test/final_solution/cube/Ops Reports Details.xlsx`

Sheet `Updated Report List`, B6:C6 and I7:J7, list Transferee Survey with sub-reports Transferee Survey and Transferee Survey Comments.

### `Reports/NCM Profile Information View for Approval 10.14.26.xlsx`

Sheet `Survey Data`: A1 says "Survey Follow Up Data" and A2 says "Survey Report". The rest of the sheet is empty. The same sheet is in `Reports/Archive/NCM Profile Information View Approved 3.31.26.xlsx`.

---

## 6. Data definitions

**Location:** `Reports/Ops Reports_Data def and sample/Supplier/SupplierDataDefinitions.xlsx`, sheet `SupplierManagement`, rows 65 to 68
**Identical copy:** `Sharepoint/Ops Reports/Supplier/SupplierDataDefinitions.xlsx`
**CSV, lines 65 to 68:** `Queries to generate sample reports/Data Definitions/Supplier management - Data point definitions.csv` (also in `Sharepoint/`, `Extra docs/` and `Ops_data/`)
**Same rows:** `Test/Ops Reports Details.xlsx`, sheet `Data Defination Index`, rows 517 to 520

| Data point | Definition | Primary source | Notes |
|---|---|---|---|
| ResponseType filter | Contact-response filter: All Yes Maybe or No. | Report parameter | |
| SurveysSent | Count of distinct TEs with a survey request email sent in the date range. | Derived | DW fact TBD. Survey send tracking |
| SurveysReceived | Count of distinct TEs who returned a survey in the date range. | Derived | DW fact TBD. Survey receive tracking |
| Request1SentDate | First automated survey request send date. | Derived | DW fact TBD. OLTP lineage: ROL.dbo.tblTETracking.Request1SentDate |

Rows 53 to 64 define the related Survey by Supplier points (TESurveyID, ResponseDate, SectionOrder, QuestionText, VendorSelect, Response, ResponseText, ResponseType and supplier fields).

---

## 7. Sample reports and screenshots

### DE team screenshot document

**Location:** `dbt/transfree-servey-ops-reports-screenshots.docx`
**Taken from:** `Extra docs/Queries to generate sample reports/DW queries/Supplier/Vendor Usage/ops-reports-screenshots.docx`, the section headed "Report- Transferee Survey"

| Field | Text |
|---|---|
| Heading | Domain- Supplier Mgmt, Report- Transferee Survey, Sub report count=1 |
| No. | 46 |
| Sub Report | Transferee Survey (incl. Comments) |
| DE Team Note | No comment option but mentioned in ruchika’s doc |

The Report Format list has four options: Detailed Survey Report, Overall Rollup, Surveys Requiring Action, TE Detail Comments Report.

![Report dialog: Detailed Survey Report for one Service Provider](Transferee_Survey_Report_Screenshots/13_doc_dialog_detailed_survey.png)

![Report Format dropdown showing four options](Transferee_Survey_Report_Screenshots/14_doc_report_format_dropdown.png)

![Department dropdown showing profit centers](Transferee_Survey_Report_Screenshots/15_doc_department_dropdown.png)

![Survey ID 44,749 page 1](Transferee_Survey_Report_Screenshots/16_doc_detailed_44749_page1.png)

![Survey ID 44,749 page 2, with Other Comments and Follow Up Permission](Transferee_Survey_Report_Screenshots/17_doc_detailed_44749_page2.png)

![Survey ID 44,867 page 1](Transferee_Survey_Report_Screenshots/18_doc_detailed_44867_page1.png)

![File ABBE250217, Other Comments](Transferee_Survey_Report_Screenshots/19_doc_detailed_abbe250217_comments.png)

![Survey ID 45,532 page 2](Transferee_Survey_Report_Screenshots/20_doc_detailed_45532_page2.png)

### What the dialog offers

Taken from the screenshots above. Title: "ROL Survey".

| Control | Options seen |
|---|---|
| Corporate Client | (All Clients) or one client, with Parent Company Rollup |
| Service Provider | (All Providers) or one consultant |
| Department | (All Profit Centers) or one profit center |
| Division Selection | (All Divisions) or listed divisions |
| Report Format | Detailed Survey Report, Overall Rollup, Surveys Requiring Action, TE Detail Comments Report |
| Select Transferees | Shown for Detailed Survey Report |
| Group options | Group By Corp Client, Group by Policy (Overall Rollup) |
| Show Metric Box | Top Box, Top 2 Box, Top 3 Box (Overall Rollup) |
| Date Range | Start Date, End Date |
| Select Transferee Permission | All, Contact Me, Willing to be contacted, Prefer no contact |
| Select Move Type | Domestic, International, Both |
| Report Output | Preview, Print, eMail as Attachment, Report in Excel Format |
| Post Report Online | Check box, disabled in most samples |

### What each format shows

| Format | Content |
|---|---|
| Overall Rollup | Header lines ("Surveys Created between..."), count per answer (Strongly Disagree to Strongly Agree), Top Box, Top 2 Box, Top 3 Box, "Number of Surveys Returned", "Total Over all Responses", "*Return Rate" |
| Detailed Survey Report | One block per survey: Survey ID, Created On, Company, Primary Contact, Transferee, file number, Profit Center, then each section with question and answer |
| TE Detail Comments Report | The same header, then only the Other Comments questions and text |
| Surveys Requiring Action | No sample found in any file |

### Back Office question sections

From the Detailed Survey Report samples: Overall Performance, NuCompass Mobility Representative Performance, NuCompass Supplier Performance, Household Goods Movers Performance, Temporary Accommodations Provider Performance, Expense Reimbursement Service, NuCompass Mobility's Platform, Other Comments, Follow Up Permission.

### `Survey Report.xls`

**Location:** `Reports/Building Report Views/Ops Reports/Survey Report.xls`
**Identical copy:** `Sharepoint/Building Report Views/Ops Reports/Survey Report.xls`

Sheet `Sheet1`, 918 rows. It holds Detailed Survey Report output for Survey IDs 45,173 to 45,180. Example from A1 to F18:

| Cell | Text |
|---|---|
| A1 / D1 / F1 | Survey ID: 45,173 / Created On: 3/24/2026  12:25:44PM / Page 1 of 2 |
| A3 / D3 | Company: ACCX / Primary Contact: Henry Dietter |
| A5 / D5 | Transferee: Aimee Stevens / Profit Center: 90 |
| A10 | Overall Performance |
| B14 / F14 | NuCompass Mobility provided valuable services to me / Strongly Agree |
| B18 / F18 | I would recommend my NuCompass Mobility Representative to others / Agree |

---

## 8. NCM Satisfaction Survey View spec and test files

### Spec

**Location:** `Reports/NCM Satisfaction Survey View spec Approved 6.11.26.xlsx`
**Identical copy:** `Sharepoint/NCM Satisfaction Survey View spec Approved 6.11.26.xlsx`

#### Sheet `General`

| Field | Text |
|---|---|
| Component Name | Satisfaction Survey Detail View |
| UDV | udv_satisfaction_survey_view_34 |
| Development Type | New Dynamic Report View |
| Description | This view contains data related a Transferee Profile |
| Overall Requirements | 1. Pull 1 row per Survey Line Item/per form: Customer Satisfaction Survey (0.0.164) |
| | 2. Only include form data if the associated Action is at least Started |

#### Sheet `Spec History`

A1 to C1: 2026-06-05, Spec Created, PBI 37970.

#### Sheet `View Mapping`

51 columns.

| Report Column Header | Form | Section | Field | Calculation |
|---|---|---|---|---|
| Client | NuCompass Profile (34.99.3400) | Program Details | Client | |
| Client Name | Source Organization / Company Level | Organization Details | Name | |
| File # | NuCompass Profile (34.99.3400) | Key Information | File Number | |
| Name | NuCompass Profile (34.99.3400) | General Information | Last Name, First Name | |
| Consultant | NuCompass Profile (34.99.3400) | Key Information | Consultant | |
| Domestic or International | NuCompass Profile (34.99.3400) | Locations | Domestic or International | |
| Status | NuCompass Profile (34.99.3400) | Key Information | Status | |
| Division | Program Master Fields | | Field Alias = Division | 1. If Source is a division or department, then use the Source Name. 2. Otherwise, use the Program Master Field Division |
| Employment Type | NuCompass Profile (34.99.3400) | Professional Information | Employment Status | |
| Policy | NuCompass Profile (34.99.3400) | Program Details | Policy | |
| Approver | NuCompass Profile (34.99.3400) | Program Details | Approver | |
| Auth Date | NuCompass Profile (34.99.3400) | Key Information | Date Authorized | |
| Benefit Expires | NuCompass Profile (34.99.3400) | Key Information | Benefits Expiration Date | |
| Move Complete Date | NuCompass Profile (34.99.3400) | Key Information | Move Complete Date | |
| Move Type | NuCompass Profile (34.99.3400) | Program Details | Domestic Move Type name or International Move Type name | If "Domestic or International" = "International", then International Move Type name, otherwise, Domestic Move Type name |
| Dept. Owner/Renter | NuCompass Profile (34.99.3400) | Program Details | Departure Homeowner Status | |
| Corp Code | Program Master Fields | | Corp Code | |
| Client VIP | NuCompass Profile (34.99.3400) | Professional Information | Client VIP | |
| NCM VIP | NuCompass Profile (34.99.3400) | Professional Information | NCM VIP | |
| Director, Client Relations | NuCompass Profile (34.99.3400) | Key Information | Director, Client Relations | |
| Capped Move Indicator | Program Master Fields | | Cap Move Indicator | |
| Client Descriptor 1 to 5 | Program Master Fields | | Client Descriptor 1 to 5 | |
| Client Descriptor 1 to 5 Drop List | Program Master Fields | | Client Descriptor 1 to 5 Drop List | |
| Survey Sent Date | Customer Satisfaction Survey (0.0.164) | | Action Sent Date | |
| Survey Complete Date | Customer Satisfaction Survey (0.0.164) | | | Date that the Survey Complete checkbox was checked |
| Survey Recipient Email | Customer Satisfaction Survey (0.0.164) | | Action Sent to Email Address | |
| Survey Section Number | Customer Satisfaction Survey (0.0.164) | | Section Number | |
| Survey Section Name | Customer Satisfaction Survey (0.0.164) | | Section Name | |
| Survey Section Question Number | Customer Satisfaction Survey (0.0.164) | | S+Section Number, Q+Question Number | ex. S1 Q1 |
| Survey Question | Customer Satisfaction Survey (0.0.164) | | Question Name | |
| Rating Points | Customer Satisfaction Survey (0.0.164) | | Points | |
| Rating | Customer Satisfaction Survey (0.0.164) | | Rating | ex. Very Satisfied |
| Question Contact | Customer Satisfaction Survey (0.0.164) | | Question Contact Name | |
| Question Contact Role | Customer Satisfaction Survey (0.0.164) | | Question Contact Role | Role Name, or "Service Manager", or "File Manager" |
| Service | Customer Satisfaction Survey (0.0.164) | | | Service associated with the Question, or "All Services" |
| Total Points Earned | Customer Satisfaction Survey (0.0.164) | | Total Points Earned | |
| Total Points Possible | Customer Satisfaction Survey (0.0.164) | | Total Points Possible | |
| Administration Complete Date | Customer Satisfaction Survey (0.0.164) | | Administration Complete Date | |
| Administration Completed By | Customer Satisfaction Survey (0.0.164) | | Administration Completed By | |
| Counselor Response | Customer Satisfaction Survey (0.0.164) | | Counselor Response | |
| Remove From Report | Customer Satisfaction Survey (0.0.164) | | Remove From Report | |
| Remove From Calc | Customer Satisfaction Survey (0.0.164) | | Remove From Calc | |
| Display Response | Customer Satisfaction Survey (0.0.164) | | Display Response | |

#### Sheet `Example Completed Survey`

A completed Service Engine form for a test file, with 8 sections and Total Points Earned 40 of 55. Here "Very Satisfied" is worth 5 points.

![Example completed survey form](Transferee_Survey_Report_Screenshots/21_spec_example_completed_survey.png)

### Test files

**Location:** `Sharepoint/Test Files for Recurring Payment and Survey Views.xlsx`
**Other version:** `Reports/Test Files for Recurring Payment and Survey Views.xlsx` (not identical. It has the same text, lower-quality images and an extra `RP View Results` image. Screenshots here come from the Sharepoint copy.)

#### Sheet `Notes for Kim`

> I used the same 4 files for recurring payments and surveys.

> The work was done in Dev.

> Test Files (green tab) provides you the TE name, file number and details related to both the survey (columns D - M) and the Recurring Payments (columns N - U)

> Each TE has a link in column M that will take you to the screenshot of their specific survey.  

> You may notice a typo on the survey.  There is a question at the end that says "Other comments or feed bac".  I have updated this on the survey template so it will show properly on any new survey.

#### Sheet `Test Files`, survey columns

Row 12 maps the columns: D = section 1, E = section 2 a, F = section 2 b, G = section 3, H = section 4 - copilot, J = section 5 a, K = section 5 b.

| Row | TE / File # | Services | 1 NCM | 2 Cons. | 3 Cons | 4 Exp | 5 CPE | Administration |
|---|---|---|---|---|---|---|---|---|
| 3 | Charles Leclerc / 278-0031 | ERP, HHG, HFR, POL, TLV | Somewhat Satisfied | Very Satisfied | Very Satisfied | Satisfied | Dissatisfied | Administration |
| 5 | Lewis Hamilton / 278-0032 | Auto, ERP, HFP, HHG, POL, TLV | Very Satisfied | Very Satisfied | Very Satisfied | Dissatisfied | Dissatisfied | No changes |
| 8 | George Russel II / 278-0034 | Auto,ERP, HFP, HHG, POL, TLV | Very Satisfied | Very Satisfied | Very Satisfied | Dissatisfied | Dissatisfied | Flagged comments to "Display Response" |
| 10 | Kimi Antonelli / 278-0029 | ERP, HHG, POL, TLV | Somewhat Satisfied | Somewhat Satisfied | Somewhat Satisfied | Somewhat Satisfied | Somewhat Satisfied | Flagged first comment to display. |

Column I, Ratings: I3 "All questions = Very Satisfied"; I5 "Very Satisfied with NCM and NCM Consultant, Dissatisfied with Expense and CoPilot"; I8 "All questions = Satisfield".

#### Sheet `Survey`

Here "Very Satisfied" is worth 1 point and "Very Dissatisfied" 5.

| Cell | TE | Administration flags (D column) |
|---|---|---|
| A1 | George Russell | Display Other Comments or Feedback questions1 and  2 |
| A50 | Kimi Antoneli | Display  Other Comments or Feedback question 1 |
| A100 | Charles Leclerc | |
| A139 | Lewis Hamilton | No flags for Lewis |

![George Russell: flags, 10 of 25 points](Transferee_Survey_Report_Screenshots/22_test_russell_flags.png)

![Kimi Antonelli survey](Transferee_Survey_Report_Screenshots/23_test_antonelli_survey.png)

![Kimi Antonelli: flags, 15 of 25 points](Transferee_Survey_Report_Screenshots/24_test_antonelli_flags.png)

![Charles Leclerc survey, 11 of 25 points](Transferee_Survey_Report_Screenshots/25_test_leclerc_survey.png)

![Lewis Hamilton survey](Transferee_Survey_Report_Screenshots/26_test_hamilton_survey.png)

### New SE survey questions and answers

**Location:** `Sharepoint/Phase 1 Report Requirements - Supplier Mgt1.xlsx`, sheet `Survey by Supplier`, A256 ("RB: Screenshot of SE survey questions and answers"), images at A258 and A293.

![SE questions and answers, part 1](Transferee_Survey_Report_Screenshots/27_se_questions_and_answers_part1.png)

![SE questions and answers, part 2](Transferee_Survey_Report_Screenshots/28_se_questions_and_answers_part2.png)

---

## 9. Service Engine objects

### View `udv_transferee_survey_view_34`

**Location:** `CPC_data/SP/allReportView.txt`, lines 14502 to about 14715

This copy is dated 2026-07-06. It is the only copy of the view text in the folder. Its header says:

```text
*  Description: Custom Adhoc report view for NUCOMPASS
*  06/23/2026 - RP - 38312 - NCM - Transferee Survey View
```

Survey fields, lines 14633 to 14635:

```sql
'Survey Sent Date' =  (select act_dateactive from action a with (nolock) where a.act_uid = css.act_uid and a.act_subject = 'Your Satisfaction Survey'),
'Survey Complete Date' = css.dt_admin_complete_date,
'Survey Recipient Email' = ISNULL((select ct.cont_email from contact ct with (nolock) join action a  with (nolock) on ct.cont_uid = a.act_to_uid where a.act_uid = css.act_uid and a.act_subject = 'Your Satisfaction Survey'),c.cust_email),
```

Rating logic:

```sql
'Rating' = case when csssd.chk_excellent = 'Y' Then 'Very Satisfied'
                when csssd.chk_good = 'Y' Then 'Satisfied'
                when csssd.chk_satisfactory = 'Y' Then 'Somewhat Satisfied'
                when csssd.chk_poor = 'Y' Then 'Dissatisfied'
                when csssd.chk_unsatisfactory = 'Y' Then 'Very Dissatisfied'
           else ''
           end,
```

Main joins:

```sql
join form_0164_customer_satisfaction_survey css with (nolock) on s.serv_uid = css.serv_uid
join form_0164_customer_satisfaction_survey_section csss with (nolock) on css.form_uid = csss.form_uid
join form_0164_customer_satisfaction_survey_section_detail csssd with (nolock) on csss.form_uid = csssd.form_uid and csss.seq = csssd.seq_section
left join form_0164_customer_satisfaction_survey_section_detail_template csssdt with (nolock) on csssd.c2000_question = csssdt.c2000_question
left join form_0164_customer_satisfaction_survey_section_template cssst with (nolock) on csssdt.section_template_uid = cssst.section_template_uid
```

The view has no `WHERE` clause.

### Survey tables

**Extracts:** `dbt/Only SE Reports/NewTables/`, with columns in `schema.csv`
**Older extracts:** `Test/SE_DEV(main)/dbo.form_0164_*.csv` (also holds `..._rating_template`)
**Object list:** `dbt/xtra_doc/mapping/alltableviewsall.txt`, lines 4278 to 4284

| Table | Holds | Rows in `NewTables` |
|---|---|---|
| `form_0164_customer_satisfaction_survey` | One survey per form: `form_uid`, `serv_uid`, `act_uid`, `nbr_total_score`, `nbr_max_possible_score`, `chk_survey_completed`, `admin_complete_cont_uid`, `dt_admin_complete_date` | 1 |
| `..._section` | Sections on a form: `seq`, `section_name` | 5 |
| `..._section_detail` | One question: `c2000_question`, `question_type`, `chk_*` answer flags, `*_weight`, `c2000_verbatim`, `question_cont_uid`, `chk_remove_rpt`, `chk_remove_calc`, `chk_display_response`, `c2000_counselor_response` | 8 |
| `..._template` | `survey_template_uid`, `form_type_uid`, `org_uid`, `rating_scale`, `chk_display_points` | 1 |
| `..._section_template` | Sections and `allowed_service_types` | 12 |
| `..._section_detail_template` | Question library, `contact_role`, `chk_all_services`, `chk_inactive_question` | 297 |

`NewTables` also holds `action_form.csv`, `form.csv` and `file_type.csv`.

`Test/SE_DEV(main)/dbo.form_0164_customer_satisfaction_survey_rating_template.csv` lists the labels for template 1: 1 Very Satisfied, 2 Satisfied, 3 Somewhat Satisfied, 4 Dissatisfied, 5 Very Dissatisfied.

### Current template questions

From `form_0164_customer_satisfaction_survey_section_template.csv` and `..._section_detail_template.csv`, section templates 213 to 224. Inactive questions are left out. Weights run from Very Satisfied to Very Dissatisfied.

| Section | Question (decoded) | Type | Weights | Contact role |
|---|---|---|---|---|
| 1 NuCompass Mobility Inc. | How satisfied were you with the services provided by NuCompass? | RATING | 1 2 3 4 5 | File Manager |
| 2 NuCompass Consultant | How likely are you to recommend your NuCompass Consultant to a friend or colleague? | RATING | 1 2 3 4 5 | 1 |
| 2 NuCompass Consultant | How satisfied are you with your Consultant’s knowledge of your policy and services provided? | RATING | 1 2 3 4 5 | File Manager |
| 2 NuCompass Consultant | How satisfied are you with your Consultant’s responsiveness? | RATING | 1 2 2 4 5 | File Manager |
| 3 Household Goods | How satisfied were you with the overall quality of the moving services provided? | RATING | 1 2 3 4 5 | Household Goods Provider |
| 4 Auto Shipment | How satisfied were you with the overall quality of your automobile transportation experience? | RATING | 1 2 3 4 5 | Auto Shipper |
| 5 Temporary Living | How satisfied were you with your corporate housing experience? | RATING | 1 2 3 4 5 | File Manager |
| 6 Cross-Cultural Training | How satisfied were you with the Cultural Training provider? | RATING | 1 2 3 4 5 | 0 |
| 7 Language Training | How satisfied were you with the Language training provider? | RATING | 1 2 3 4 5 | 0 |
| 8 Destination Services | How satisfied were you with the local service provider who helped you at your destination? | RATING | 1 3 3 4 5 | 0 |
| 10 Expense Management | How satisfied were you with the overall quality of your automobile How satisfied were you with the way your expenses were processed in accordance with your employer’s policy? | RATING | 1 2 3 4 5 | Expense Analyst |
| 11 CoPilot | How satisfied are you with our technology platform for ease of use and as a valuable resource? | RATING | 1 2 3 4 5 | File Manager |
| 12 Other Comments or Feed Bak | Please make any comments about your overall experience. | VERBAT | None | 1 |
| 12 Other Comments or Feed Bak | Please provide feedback about your employer’s policy. | VERBAT | None | 1 |
| 12 Other Comments or Feed Bak | Is there someone, or a group of people, that you would like to recognize for their service? | VERBAT | None | 1 |

Section 9 (Furniture Rental) has only an inactive question.

### Sending the survey

| Location | Point |
|---|---|
| `dbt/Only SE Reports/NewDump/code.csv`, line 7934 | Service type `C244` is "Survey" |
| `dbt/Only SE Reports/NewDump/code.csv`, line 1799 | Code type `NCMSST`, "NuCompass - Survey Status" |
| `dbt/Only SE Reports/NewDump/code.csv`, line 3763 | Field code `C311`, "Survey Trigger Date" |
| `Ops_data/workflow_template.csv`, lines 25 and 238 | Workflow templates 331 and 408, "Survey", service `C244`, "Internal Only Service" |
| `Test/SE_DEV(main)/dbo.action_template.csv` | Workflow 331, process 568 has three actions: "Relocation Service Evaluation", "Relocation Service Evaluation – 2nd Request", "Final Request – I need your help please" |
| `Ops_data/action.csv` | Process 568 has 6 actions with subject "Your Satisfaction Survey" and 5 with subject "Survey Not Completed" |
| `dbt/xtra_doc/mapping/alltableviewsall.txt`, lines 1283, 1285, 2042, 2043 | Procedures `ap_sel_ncm_vmt_create_survey_34`, `ap_sel_ncm_vmt_survey_complete_check_34`, `ap_upd_ncm_vmt_create_survey_34`, `ap_upd_ncm_vmt_survey_complete_check_34`. Their code is not in the folder |

### Report metadata

**Location:** `Test/SE_DEV(main)/dbo.report_hdr.csv`, lines 23 and 26
**Identical copy:** `Test/final_solution/cube/SE_DEV(main)/dbo.report_hdr.csv`

| report_hdr_uid | Name | Source | Created |
|---|---|---|---|
| 225 | Sample Survey View | `udv_transferee_survey_view_34` | 07/08/2026 |
| 228 | DEV TEST SURVEY | `udv_transferee_survey_view_34` | 07/15/2026 |

`Test/SE_DEV(main)/dbo.report_execution_tracking.csv` shows three completed XLS runs: 268 (07/08/2026), 271 (07/15/2026) and 272 (07/20/2026).

---

## 10. Legacy Back Office objects

The survey data sits in a separate database. `CPC_data/SP/AllReloViews.csv`, lines 23 and 25, define `tblSurveyTypes` and `tblTESurveyControl` as views over `HROServiceEval.dbo`. The `.rpt` report and the form behind the ROL Survey dialog were not found.

### Tables and columns

**Location:** `CPC_data/SP/2ReloSCHEMA.csv`

| Table | Columns |
|---|---|
| `tblTESurveyControl` | TESurveyID, TEFileNo, CreatedOn |
| `tblTEResponses` | TEResponseID, TESurveyID, QuestionID, Response, ResponseComments, GenericVendorID, CreatedOn, ModifiedOn, VendorType, CommentsExist |
| `tblQuestions` | QuestionID, SectionID, QuestionOrder, SubQuestionOrder, QuestionText, EffectiveDate, ResponseType, VendorSelect, VndrSrvcID, Active, CommentsAssociated, CommentLabel, ConditionalOnQuestionID, ConditionalInfo |
| `tblSections` | SectionID, SurveyTypeID, SectionOrder, Description, ServiceCode, CreatedOn, CreatedBy, ModifiedOn, ModifiedBy |
| `tblSurveyTypes` | SurveyTypeID, SurveyName, SurveyDescription, CreatedOn, ModifiedOn, ModifiedBy |
| `tblCorpStatsSurveyCount` | CorpStatsSurveyCountID, CorpCode, DomesticIntl, DivisionName, SortOrder, Statistic, DateType, NumeratorCount, DenominatorCount, LastRunDate |

`tblTETracking` and `vwTESurveySuppliers` are named in the data definitions but are not in this schema file.

### Return rate, `pr_CL_SurveyReturnRate`

**Location:** `CPC_data/SP/allReloSP.csv`, line 26790

```sql
ReturnRate= case when (SurveysRecd<>0 and SurveysSent<>0) then ((SurveysRecd/SurveysSent)*100) else 0 end
```

`SurveysRecd` is `NumeratorCount` and `SurveysSent` is `DenominatorCount` from `tblCorpStatsSurveyCount`.

### Positive responses, `pr_CL_SurveyPosResponse`

**Location:** `CPC_data/SP/allReloSP.csv`, line 26247

```sql
PositiveResponse= case when (TotalCount<>0 and PosResp<>0) then ((PosResp/TotalCount)*100) else 0 end
```

### Other objects

| Object | Location |
|---|---|
| `pr_CL_SurveyPosResponse_Detail` | `CPC_data/SP/allReloSP.csv`, line 16528 |
| `pr_getsurveyparticipants` | `CPC_data/SP/allReloSP.csv`, line 11846 |
| `tblTEMain1.ExcludeFromSurvey` | `CPC_data/SP/Questions_for_NCM_Report_Makers.txt`, line 100, and `CPC_data/SP/Questions_ReloAction_MainTables.txt`, line 70 |

### DimCorpClient survey columns

| Location | Point |
|---|---|
| `dbt/dbt/models/intermediate/SE/service_engine/dim/int_se_dim_CorpClient.sql`, lines 139 to 141 | `ROLSurveyQuestion`, `TESurveyDomestic`, `TESurveyInternational` are `cast(null ...)` for SE |
| `dbt/xtra_doc/mapping/Mapping(CPC_Column_Mapping_List).csv`, lines 376 to 378 | The same three columns are `NO_MAPPING_OK` |

---

## 11. dbt models

These models were created on 2026-11-04 while this file was being compiled, so check them again if they have changed.

### `dbt/dbt/models/marts/Facts/FactTransfereeSurvey.sql`

```sql
-- Gold FactTransfereeSurvey: Service Engine rows only (int_se_fact_TransfereeSurvey), one per survey question.
-- Replaces udv_transferee_survey_view_34 (NCM Transferee Survey adhoc report): same columns, same names, same order.
-- No NCM counterpart, so no union model and no KeyMap IDs. The view has no unique key, so no unique index.
```

It has 53 report columns plus `udv_cust_uid`.

### `dbt/dbt/models/intermediate/SE/service_engine/fact/int_se_fact_TransfereeSurvey.sql`

Its header says:

```text
FactTransfereeSurvey -- grain: one row per survey question (survey x section x question),
made distinct like the view. Port of Service Engine's udv_transferee_survey_view_34
(NCM Transferee Survey adhoc report, tickets 38312 / 39063).
```

Differences it lists from the view:

```text
- the supplier_names and supplier_names_designations CTEs are dropped: the view declares them
  but selects nothing from them. So file_type and x_org_designations are not needed.
- master_fields reads only the labels the report uses (no Employee Number, no Cost Center).
```

Behaviour it says it keeps:

```text
- the n2 join filters on n1.name_object_class (not n2's). Director, Client Relations can
  therefore match a name of any class, and is NULL when the file has no consultant.
- Rating Points is 0, not blank, for an unanswered question: the view's else '' converts to
  0 in a numeric case.
```

How it finds the template and the sending action:

```sql
-- The most specific survey template for the file: its org, division or company, else the default (0).
cross apply (
    select top 1 t.survey_template_uid, t.form_type_uid
    from {{ ref('stg_se__form_0164_customer_satisfaction_survey_template') }} t
    where t.org_uid in (c.cust_org_uid, c.cust_div_uid, c.cust_company_uid, 0)
    order by t.org_uid desc
) template

-- The first action that sent this survey form on the service.
cross apply (
    select top 1 a.act_uid, a.act_dateactive
    from {{ ref('stg_se__action') }} a
    join {{ ref('stg_se__action_form') }} af
      on af.act_dup_uid = a.act_uid
    join {{ ref('stg_se__form') }} sf
      on sf.form_uid = af.form_uid
     and sf.form_type_uid = template.form_type_uid
    where a.act_serv_uid = css.serv_uid
      and a.act_dateactive is not null
    order by a.act_dateactive
) survey_action
```

### Staging models

**Folder:** `dbt/dbt/models/staging/service_engine/snapshot/`

`stg_se__action_form.sql`, `stg_se__form.sql`, and `stg_se__form_0164_customer_satisfaction_survey.sql` with its `_section`, `_section_detail`, `_template`, `_section_template` and `_section_detail_template` versions.

### `dbt/dbt/models/_sources.yml`, lines 92 to 99

Adds `action_form` and the six `form_0164` tables.

### `dbt/dbt/models/marts/_gold.yml`, line 894

```yaml
- name: FactTransfereeSurvey
  description: >
    Service Engine only (no NCM rows, no KeyMap IDs): port of udv_transferee_survey_view_34,
    one row per survey question. Column names match the legacy report view.
  columns:
    - name: "File #"
      quote: true
      data_tests: [not_null]
```

### Run log

**Location:** `dbt/dbt/logs/dbt.log`

| Time | Result |
|---|---|
| 16:42:56 | `FactTransfereeSurvey` table built. The `not_null` test on `File #` failed with `Invalid column name 'File'` |
| 16:42:58 | `Done. PASS=16 WARN=0 ERROR=1 SKIP=0 NO-OP=0 TOTAL=17` |
| 16:43:32 | `int_se_fact_TransfereeSurvey` and `FactTransfereeSurvey` rebuilt. `not_null` test passed after `"File #"` was quoted in `_gold.yml` |
| 16:43:34 | `Done. PASS=7 WARN=0 ERROR=0 SKIP=0 NO-OP=0 TOTAL=7` |

The log does not give a row count.

---

## 12. Related reports and items searched but not quoted

### Survey Follow Up Report

**Location:** `Sharepoint/Phase 1 Report Requirements - Ops.xlsx`, sheet `Survey Follow Up`
**Menu:** Reports > Navigator > Transferee Survey > Survey Follow Up Report. Tracker ID 49, Ops rank 4.

> BD: I run this report after the first week of each month and send it out to the Consultants with a requeest for them to follow up with all TEs that have received 2 surveys. I run by individual Consultant by date range and select email as an attachment. 

> LK - same

`Operations!B40:B45` in the Business Owners list gives the fields: File #, TE Name, Employee Number (dont think we need this), Consultant, Date last survey sent, Total # of surveys sent. Sample: `Reports/Building Report Views/Ops Reports/Survey Follow Up.pdf` (identical copy in `Sharepoint/`).

![Follow-up Survey Request dialog](Transferee_Survey_Report_Screenshots/29_followup_dialog.png)

![Follow-up Survey Report](Transferee_Survey_Report_Screenshots/30_followup_report.png)

![Survey Follow Up.pdf](Transferee_Survey_Report_Screenshots/31_followup_pdf.png)

![Follow-up dialog from the Business Owners list](Transferee_Survey_Report_Screenshots/32_bo_list_followup_dialog.png)

![Follow-up sample from the Business Owners list](Transferee_Survey_Report_Screenshots/33_bo_list_followup_sample.png)

### Survey by Supplier

**Location:** `Sharepoint/Phase 1 Report Requirements - Supplier Mgt1.xlsx`, sheet `Survey by Supplier`. Tracker ID 47.

This is the report that Transferee Survey data "pulls to" (section 2). A2 says "Description: The report captures the supplier performance rating for any given time period. " and A3 says "How it is used: This report is used for supplier performance management and score card reviews. ". Sample: `Reports/Building Report Views/Supplier Mgt Reports/Supplier Survey Report.xls`.

![ROL Survey by Supplier dialog](Transferee_Survey_Report_Screenshots/34_supplier_dialog.png)

![Supplier Survey Detail Results](Transferee_Survey_Report_Screenshots/35_supplier_detail_report.png)

### Not quoted

| Item | Why it is not quoted |
|---|---|
| `Reports/Ops Reports_Data def and sample/REM/REMSampleData.xlsx` | False match: "satisfaction" and "survey" in expense and policy text |
| `Reports/Ops Reports_Data def and sample/Finance/FinanceDetailSamples.xlsx`, `TaxNonTaxDetail!AF3361` | False match: "home purchase - survey" |
| `Reports/Zip Code Table from Back Office/` workbooks | False match: "Survey" and "Surveyor" supplier types |
| `Reports/NCM Service Information View for Approval 10.14.26.xlsx`, `supplier reports!G1:G3` | Supplier Survey Results, "no requirements for Supplier Surveys" |
| `Final Reports List 5.29.26 RB!C17`, "Employee Survey Results Report" | A CPC report, not this one |
| Household goods survey items (`form_0015_hhg_survey`, Video Survey, "Virtual Survey Request") | A different kind of survey |
| `form_0137_customer_satisfaction_survey` tables | An older form. The view does not use them |
| `Survey Audit Report` | Named on the Back Office menu only, with no requirement or sample |
| `dbt/dbt/target/` | Generated copies of the dbt models in section 11 |
| `*.zip` files | Not opened |
| `*.mp4` files | Video content could not be searched |
| `*.msg` email files (8) | Searched as plain text only, with no survey match. Text stored in compressed form would not have been searched |
| `Reports/Building Report Views/Expense Mgt Reports/DNU Client Expense Payment Example 1.xlsx` | Could not be opened: the file is not a valid xlsx |

---

## 13. Observations (mine, not from the source files)

These are my own notes on where the sources disagree or leave gaps. Nothing here was checked against a database. Items are ordered with the ones most likely to affect report numbers first.

1. **The points scale runs in opposite directions.** The spec example gives Very Satisfied 5 points, but the test surveys and the current template give it 1. A lower total is better under the current template, so any calculation built on Rating Points or Total Points could read backwards. Top Box should count the `Rating` label, not the points. The business should confirm which scale is intended.
2. **Two current questions have odd weights.** "Consultant's responsiveness" is 1 2 2 4 5 and "local service provider" is 1 3 3 4 5. Each looks like a typing error for 1 2 3 4 5. They would change Total Points on new surveys.
3. **The fact is a detail table, and the Back Office formats are not built yet.** `FactTransfereeSurvey` matches the Detail View spec. The Overall Rollup needs Top Box, Top 2 Box, Top 3 Box, Number of Surveys Returned and Return Rate, and none of these exist as columns. Remove From Calc and Remove From Report also still need to be applied wherever these numbers are calculated.
4. **Return Rate has no denominator in the fact.** It needs surveys sent, including surveys never returned. The inner joins may keep unanswered surveys, because form rows exist before a reply. I would confirm that before relying on it, and decide how the 2nd and final requests count.
5. **The Transferee Permission filter has no SE source that I can find.** Back Office has "Follow Up Permission" and the filter All, Contact Me, Willing to be contacted, Prefer no contact. The SE template has no such section or question, and the data definitions call it the "ResponseType filter". The business needs to decide whether it is dropped.
6. **The Back Office and SE surveys are different instruments.** Back Office uses a six-point Agree scale and many more questions. SE uses a five-point Satisfied scale and far fewer. `Operations!A28` confirms the move ("We are changing to a 5 star format"). The plan to "compare manually" in `Final Reports List` can't match question for question, and WOW Factor and Ace Award scores may not carry across.
7. **WOW Factor and Ace Award are never defined.** Bert uses the report to calculate them, but no file gives the formula.
8. **The view text in this folder is older than the dbt model.** The dbt header cites ticket 39063, and it finds the template and sending action in ways the 7/6 dump does not. Its comment says "Same joins and inner/left choices as the view", which is not true of that dump. I could not find the 39063 version here, so I could not check the port. Please get the current view text from SE.
9. **The 7/6 view has two problems the dbt model appears to avoid.** It joins templates on question text alone, and 25 of the 29 distinct question texts repeat across template rows, up to 20 times. Some repeats have different roles or services, so `DISTINCT` alone would not remove the duplicates. It also hard-codes the subject 'Your Satisfaction Survey', while the workflow template subject in the SE_DEV extract is "Relocation Service Evaluation".
10. **Older forms may not match the template.** The dbt model matches on section name and exact question text. The test forms use older wording ("o How satisfied..." in the screenshots), and the current template has the version without "o". On a mismatch, Service would be blank and Question Contact Role would fall back to the contact's role. A count of blank Service values would show this quickly.
11. **Spec requirement 2 is only partly clear.** "Only include form data if the associated Action is at least Started". The 7/6 view has no such filter. The dbt model needs `act_dateactive` to be present, which may be the same rule, but this needs confirming.
12. **`Survey Complete Date` is the admin date.** The spec says it is the date the Survey Complete box was checked, but both the view and dbt use `dt_admin_complete_date`, the same as Administration Complete Date. The schema has no separate date. A survey completed but not administered, which appears to be the case for Leclerc in the test screenshot, would show no complete date.
13. **Spec and view differ.** The spec names `udv_satisfaction_survey_view_34`, while the actual view is `udv_transferee_survey_view_34`. The view and dbt have `Yes or No Response` and `Text Response`, which the spec does not list. All 51 spec columns are present, in the same order. The spec description ("data related a Transferee Profile") looks copied from another spec.
14. **The DE note on comments needs resolving.** It says "No comment option", but the Back Office dropdown has TE Detail Comments Report and both report lists expect Transferee Survey Comments. The fact has `Text Response` and `Display Response`, so the data is available.
15. **"Surveys Requiring Action" has no sample or definition.** Section 1 calls the weekly process both "Surveys Requiring Review" and "surveys requireing action", with Karen sending it. Whether it is in Phase 1 is unclear. `Report Variants` leaves it out.
16. **The trackers are out of date against dbt.** `Test/Tracker.xlsx` row 50 says "No fact yet" and "Not Started" (last updated 2026-10-22), but `FactTransfereeSurvey` now exists. "KM to confirm which format Anna uses" is still unanswered. It may no longer matter, since `Transferee Survey!A10` says SM does not use this report.
17. **One tracker row may be covering two reports.** `Phase 1 Report List` has TE Survey (Ops) and Transfee Survey (Supplier Mgt) on separate rows, with ranks 3 and 8. The Back Office menu and identical dialogs show they are the same report, and `Report List by RB` counts it as 1. The file treats them as one on that basis, and you confirmed the TE Survey requirement is for this report.
18. **The path differs between sheets.** The Ops sheet says Reports/Navigator/Survey Reports. The Supplier Mgt sheet says Reports/Navigator/Transferee Survey. The menu screenshot matches the Supplier Mgt path, then TE Survey.
19. **`Report Variants` points to the wrong sample.** It lists `Survey Report.xls` for Overall Roll Up, but that file holds Detailed Survey Report output.
20. **The test workbook has errors, so check it before using it for reconciliation.** George Russell's main screenshot (`Survey!A3`) is the same image as Lewis Hamilton's (`Survey!A141`), so I left it out. His ratings in `Test Files!D8:H8` copy Hamilton's, but his 10 points fit the note "All questions = Satisfield". Charles Leclerc's I3 says "All questions = Very Satisfied", which disagrees with D3:H3 and with his 11 points. Links M5 and M8 point to the `Test Files` sheet, not `Survey`.
21. **The data definitions don't fully match the schema.** They cite `tblTEResponses.ResponseText`, but the schema column is `ResponseComments`. They use the name `ResponseType` for two different things.
22. **The sample data is very small.** `NewTables` has 1 survey, which is unanswered. `Test/SE_DEV(main)` has 6 surveys, of which 4 are answered. Neither is enough to test the rollup figures.
23. **This file contains real names.** The source screenshots and comments show transferee and employee names, so take care if you share it outside the team.
