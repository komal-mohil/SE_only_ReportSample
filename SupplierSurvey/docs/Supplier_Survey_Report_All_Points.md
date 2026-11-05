# Supplier Survey Report: All Points Found, With File Locations

Compiled 2026-11-05 from the files in the `dwh` folder. No database was connected to or queried. The dbt run results in section 11 come from reading the existing log file only.

**How to read this file**

- Text in quote blocks and code blocks is copied **exactly as written in the source**, including its spelling mistakes (for example "Suvey", "Authoorized", "fo example", "Feed Bak").
- Every point has a **Location**. Paths are relative to the `dwh` folder. Excel locations are given as sheet and cell.
- Where a file exists in several folders, the copies are listed once. They were checked as identical unless stated otherwise.
- Screenshots are stored in `Supplier_Survey_Report_Screenshots/`, next to this file. Keep the two together so the images display.
- Section 13 is the only part that is not source text. It holds my own observations and is labelled as such.

**Names used for this report**

| Name in the source | Where it is used |
|---|---|
| Survey by Supplier | Requirements sheet, Back Office menu item, report lists, trackers, DE team screenshot document |
| Suvey by Supplier | Path in `Survey by Supplier!C4` (misspelled in the source) |
| ROL Survey by Supplier | Title of the Back Office report dialog |
| Supplier Survey Results | Report title for Summary by Section, and the sample `.xls` |
| Supplier Survey Detail Results | Report title for Summary by Supplier and Summary by Supplier with Detail |
| Customer Satisfaction Survey (form 0164) | Service Engine form that holds the answers |
| FactSupplierSurvey | dbt gold table |

**Contents**

1. [Survey by Supplier requirements](#1-survey-by-supplier-requirements)
2. [Back Office data fields and sort options](#2-back-office-data-fields-and-sort-options)
3. [Related requirements](#3-related-requirements)
4. [Business Owners report list](#4-business-owners-report-list)
5. [Trackers and report lists](#5-trackers-and-report-lists)
6. [Data definitions](#6-data-definitions)
7. [Sample reports and screenshots](#7-sample-reports-and-screenshots)
8. [View specs](#8-view-specs)
9. [Service Engine objects](#9-service-engine-objects)
10. [Legacy Back Office objects](#10-legacy-back-office-objects)
11. [dbt models](#11-dbt-models)
12. [Searched but not quoted](#12-searched-but-not-quoted)
13. [Observations (mine, not from the source files)](#13-observations-mine-not-from-the-source-files)

---

## 1. Survey by Supplier requirements

**Location:** `Sharepoint/Phase 1 Report Requirements - Supplier Mgt1.xlsx`, sheet `Survey by Supplier`
**Identical copy:** `Ops_data/sharepoint/Phase 1 Report Requirements - Supplier Mgt1.xlsx`
**Text-only CSV export of the same sheet:** `dbt/Phase 1 Report Requirements - Supplier Mgt1(Survey by Supplier).csv`

| Cell | Text |
|---|---|
| A1 / C1 | Backoffice Report / Survey by Supplier |
| A2 | Description: The report captures the supplier performance rating for any given time period. |
| A3 | How it is used: This report is used for supplier performance management and score card reviews. |
| A4 / C4 | Path to Report / Reports/Supplier Reports/Suvey by Supplier |
| A5 / C5 | Report selections / Note, there are three report format options, Summary by Section, Summary by Supplier, and Summary by Supplier with Detail. |
| A6 | We use : Summary by Supplier with Detail. |
| K7 | Questions for Anna: |
| M7 | Do you typically use one of the formats or do you use all three?- No we use "summary by Supplier with Detail only |
| M8 | I tried running a report with the "Show Comments box checked.  I did not see that the report actually pulled comments.  Should it? - If there are no comments to show none will appear, but we use the check box for the format we pull and comments are always shown. |
| K9 | AW:If there are no comments to show none will appear, but we use the check box for the format we pull and comments are always shown. |
| A31 | Summary by Supplier with Detail - "show comments" box is always checked |
| A32 | We need to be able to run the report by individual supplier. |
| A256 | RB: Screenshot of SE survey questions and answers |

**Location:** same workbook, sheet `BO Data Fields by Report`, cells H1:J2

| SM- Back Office Reports | Rank | Phase 1/2 |
|---|---|---|
| Survey by Supplier | 1 | 1 |

The sheet `Notes and Decisions` in this workbook has headers only (Date, Subject, Summary, Link) and no entries.

### Screenshots on the Survey by Supplier sheet

**A12, Back Office menu.** The menu path is Reports > Supplier Reports > Survey by Supplier. The source images also show a second monitor with a Teams chat list, which I cropped out of this image and the next.

![Back Office menu: Reports, Supplier Reports](Supplier_Survey_Report_Screenshots/01_bo_menu_supplier_reports.png)

**J15, Report Format dropdown.** An arrow shape at row 24 sits next to this image in the source.

![Report dialog with the Report Format dropdown open](Supplier_Survey_Report_Screenshots/02_req_dialog_report_format_dropdown.png)

**A34, dialog for Summary by Supplier with Detail.** The Show Comments box is unchecked in this image.

![Report dialog: Summary by Supplier with Detail](Supplier_Survey_Report_Screenshots/03_req_dialog_supplier_with_detail.png)

**A60, A104, A141, A163, A207: the report, pages 1 to 5.** Printed 7/1/26, "Surveys Created between 06/30/26 and 07/01/26", All Clients, All Service Providers, All Profit Centers. This is the format the business uses.

![Supplier Survey Detail Results page 1](Supplier_Survey_Report_Screenshots/04_req_detail_results_page1.png)

![Supplier Survey Detail Results page 2](Supplier_Survey_Report_Screenshots/05_req_detail_results_page2.png)

![Supplier Survey Detail Results page 3](Supplier_Survey_Report_Screenshots/06_req_detail_results_page3.png)

![Supplier Survey Detail Results page 4](Supplier_Survey_Report_Screenshots/07_req_detail_results_page4.png)

![Supplier Survey Detail Results page 5](Supplier_Survey_Report_Screenshots/08_req_detail_results_page5.png)

**A258 and A293: SE survey questions and answers** (under A256). These are the same two images as in the Transferee Survey folder. Section 4 of the form is not shown in either image.

![SE survey form, sections 1 to 3](Supplier_Survey_Report_Screenshots/09_se_questions_and_answers_part1.png)

![SE survey form, section 5 and totals](Supplier_Survey_Report_Screenshots/10_se_questions_and_answers_part2.png)

---

## 2. Back Office data fields and sort options

**Location:** `Sharepoint/Phase 1 Report Requirements - Supplier Mgt1.xlsx`, sheet `BO Data Fields by Report`, rows 51 to 63
**Same text in:** `Reports/Business Owners List Reports- BO vs SE  data fields.xlsx`, sheet `SM Reports`, rows 51 to 63

| Cell | BO Data Fields | SE Data Fields |
|---|---|---|
| A52 (BO Report Name) | Survey by Supplier | |
| B52 / C52 | TE File No | File Number |
| B53 / C53 | TE Name | Transferee Name |
| B54 / C54 | Service Provider | Supplier Authoorized? |
| B55 / C55 | Service Type | Service Type |
| B56 | Strongly Disagree | |
| B57 | Disagree | |
| B58 | Slightly Disagree | |
| B59 | Slightly Agree | |
| B60 | Agree | |
| B61 | Strongly Agree | |
| B62 | Comments Section | |
| B63 | Total by Supplier Provider | |

**BO Reporting Sort Options, E52 and E53**

> Supplier Types = All, Auto, Mortgage, HHG, HFP Agent, Home Sale Agent, Rental Assistance, Property Management, Temp Housing
> Report Format Options = Summary by Section, Summary by Supplier, Summary by Supplier with Detail

> **survey questions differ by service line

---

## 3. Related requirements

**Location:** `Sharepoint/Phase 1 Report Requirements - Supplier Mgt1.xlsx`, sheet `Transferee Survey`, cell A10

> SM does not use this particular report but the data from this report is required and  pulls to the "Survey by Supplier" report that we use to manage performance.

**Location:** `Sharepoint/Phase 1 Ops Reports.xlsx`, sheet `Ops Phase 1 Reports`, cells L8 and M8 (the TE Survey row)

> Report output depends on which services the TE received. Supplier Mgt has a related Transferee Survey / Survey by Supplier report.

> KM to confirm which format Anna uses. Need screenshots / sample data from SE.

Sheet `Survey by Supplier!A6` and `M7` above answer the second point.

The full Transferee Survey material is in `Transferee_Survey_Report_All_Points.md`, next to this file. Its section 12 has a short Survey by Supplier entry.

---

## 4. Business Owners report list

**Location:** `Reports/Business Owners List Reports- BO vs SE  data fields.xlsx`
**Same cell values for these rows:** `Sharepoint/Business Owners List Reports- BO vs SE  data fields.xlsx`
**Earlier version without the "Report List by RB" and "Final Reports List" sheets:** `Reports/Building Report Views/Ops Reports/Reports- BO vs SE  data fields.xlsx`

### Sheet `Report List by RB`, row 2

Also exported to CSV, line 2 of `Extra docs/Business Owners List Reports- BO vs SE  data fields(Report List by RB).csv` and `Ops_data/Queries & Data Points/Business Owners List Reports- BO vs SE  data fields(Report List by RB).csv`.

| Cell | Column (row 1 header) | Text |
|---|---|---|
| A2 | Business Category | Supplier Mgmt |
| B2 | Report category | Survey by Supplier |
| C2 | Reports | Survey by Supplier<br>Survey grouped by Service provider<br>Survey grouped by client<br>Supplier Type  fo example HHG |
| D2 | Slicers/Filters/Grouping | Run by individual supplier<br>Run by all suppliers<br>Date range<br>ServiceProvider<br>Client<br>SupplierType<br>Profit center |
| F2 | No of Reports | 1 |
| G2 | NCM schema status | SE only data source |

Cell E2 (no header):

> As confirmed earlier, we will build survey reports based on SE data.I put Screenshot of new questions and answers in the in another tab. The filters are applicable to all survey reports.
> Depending on the report, Profit center may refer to NCM divisions in BO. In SE we won't have profit centers. So we can remove this filter

### Sheet `Final Reports List 5.29.26 RB`, row 25

| Cell | Text |
|---|---|
| G25 | Survey by Supplier |
| H25 / I25 | 1 / 1 |
| K25 | Data will come from SE, For BO data, ops will generate in BO and compare manually |

The title in A1 of that sheet and of `Final Reports List 5.29.26` reads:

> Final list reveiwed and approved by the business 5.29.26 - Pending reports needed for Accounting and Dave.

### Other cells in this workbook

| Sheet | Cell | Text |
|---|---|---|
| `Contents` | C14 to F14 | Survey by Supplier / Anna / SM / 1 (columns: Report List, Assigned to, Team, Phase) |
| `Contents` | K41 | Survey by Supplier (under Consolidated List) |
| `Final Reports List 5.29.26` | A15 to D15 | Survey by Supplier / Survey by Supplier / 1 / 1 |
| `Final Reports List 5.29.26 RB` | A15 | Survey by Supplier |
| `KM Working Doc` | A39 / B39 | Survey by Supplier / Y (columns: Consolidated List, Posted to Teams) |
| `Screen Shots ` | A241 | Survey by Supplier – Note: Questions differ per service line |
| `Screen Shots ` | A242 / A252 | Data Fields: / Sort Options |

### Screenshots on sheet `Screen Shots `

**A244, under Data Fields.** This sample shows a response of "NA" that is counted in none of the columns.

![Report sample with an NA response](Supplier_Survey_Report_Screenshots/11_bo_list_report_sample_na_response.png)

**A254, under Sort Options.**

![Report dialog: Summary by Section](Supplier_Survey_Report_Screenshots/12_bo_list_dialog_summary_by_section.png)

---

## 5. Trackers and report lists

### `Test/Tracker.xlsx`

**Identical copy:** `Test/final_solution/cube/Tracker.xlsx`

**Sheet `Tracker`, row 49** (header in row 2; last updated 2026-10-22). Blank columns are left out.

| Column | Value |
|---|---|
| ID | 47 |
| Domain | Supplier |
| Owner Team | Supplier Mgt |
| Report Family | Survey by Supplier |
| Sub-report / Variant | Survey by Supplier / by Service Provider / by Client / by Supplier Type |
| Phase 1 List Name | Survey by Supplier |
| Legacy Artifact (.rpt / PBI) | BO survey report |
| Source System(s) | SE |
| In Scope (Ph 1) | Yes |
| Scope Decision / Reason | Build survey reports from SE data (confirmed). |
| SE Data Needed? | Yes |
| SE Mapping Status | Not Started |
| SE Mapping Notes / SE Objects | New SE survey questions/answers screenshot provided; SE has no profit centers — drop that filter. |
| Fact Loaded in DW? | No fact yet |
| DW Query Exists? | No |
| DW Query Result | N/A |
| Txn Query Exists? | No |
| DW vs Txn Reconciled? | N/A |
| Filters / Parameters | Supplier (one/all), Date range, Service Provider, Client, Supplier Type |
| Data Definitions Doc | No |
| Business Sample Provided | Yes |
| Build Status | Not Started |
| Notes | Added from Phase 1 business list — no query in inventory. |

**Sheet `Decisions Log`, row 8**

| Topic | Decision / Summary | Decided By | Affects Tracker ID(s) | Source |
|---|---|---|---|---|
| Survey reports source | Survey reports will be built on SE data. SE has no profit centers — drop that filter. | Business (Supplier Mgt) | 47, 48, 49, 50 | Ops Reports Details.xlsx — Updated Report List |

**Sheet `Dashboard`, cell B29**

> • 5 in-scope sub-reports have no DW query (mostly SE-based survey/workload reports) — IDs 47, 48, 49, 50, 51.

### `Ops_data/Queries & Data Points/currentTracker.xlsx`

**Sheet `Tracker (RB list)`, row 66**

| Cell | Value |
|---|---|
| A66 / B66 / C66 / D66 | 40 / Survey by Supplier / Supplier / TBC |
| E66 to K66, M66 | Not Started |
| O66 / P66 | New (from RB list) / SE only data source |
| Q66 | RB: 1 report; grouped by Service Provider / Client / Supplier Type |

**Sheet `Detail_Sheet`, row 60**

| Cell | Value |
|---|---|
| E60 | Not Started |
| F60 | Survey by Supplier (1) |
| G60 | Survey by Supplier; Survey grouped by Service provider; Survey grouped by client; Supplier Type fo example HHG |
| H60 | Run by individual supplier; Run by all suppliers; Date range; ServiceProvider; Client; SupplierType; Profit center |
| J60 | SE only data source |
| L60 | Supplier management - Data point definitions.csv |
| M60 / P60 | None / None |
| R60 | NO QUERY YET. Get SE survey questions/answers screenshot (other tab) + sample data; drop Profit Center filter |

Cell I60 repeats `Report List by RB!E2` from section 4.

### `Ops_data/Queries & Data Points/Reporting Work Tracker (Report Wise)(OPS Report Data Tracker).xlsx`

**Sheet `OPS Report Data Tracker`, row 69.** Also exported to CSV, line 69 of the `.csv` with the same name.

| No | Domain | Report Family | Sub-report / Variant | In Scope (Ph 1) | DW Query Exists? | Txn Query Exists? | Scope Decision / Reason |
|---|---|---|---|---|---|---|---|
| 52 | Supplier | Survey by Supplier | Survey by Supplier | Yes | No | No | RB Report List: added - RB: 1 report; grouped by Service Provider / Client / Supplier Type |

RB List Change (AC69) is "New (from RB list)".

### `Test/Ops Reports Details.xlsx`

**Identical copy:** `Test/final_solution/cube/Ops Reports Details.xlsx`

**Sheet `Updated Report List`.** Row 2 repeats `Report List by RB` row 2, with the same text in C2, D2 and E2 and a count of 1 in F2. H3 to K3 repeat it under "List of RB vs Ops_reports_46_inventory": Supplier / Survey by Supplier / the same four report lines / 1.

### `Sharepoint/Phase 1 Report List as of 7.17.26.xlsx`

**Identical copy:** `Ops_data/sharepoint/Phase 1 Report List as of 7.17.26.xlsx`

Sheet `Sheet1`, title in A1: "Phase 1 Report List Summary based on Business Owners  (July 17, 2026)"

| Cell | Text |
|---|---|
| A26 / B26 | Survey by Supplier / Supplier Mgt |

### `Reports/Report Improvement/SE Reports for CR 4.03.25.xlsx`

Sheet `Reports to Replicate in SE`, title in A1: "Reports Client Relations Needs in SE"

| Cell | Report | Path | Need |
|---|---|---|---|
| A89:C89 | Survey by Supplier | Supplier Reports | NEEDED |

---

## 6. Data definitions

**Location:** `Reports/Ops Reports_Data def and sample/Supplier/SupplierDataDefinitions.xlsx`, sheet `SupplierManagement`, rows 53 to 64
**Identical copy:** `Sharepoint/Ops Reports/Supplier/SupplierDataDefinitions.xlsx`
**CSV, lines 53 to 64:** `Queries to generate sample reports/Data Definitions/Supplier management - Data point definitions.csv` (also in `Sharepoint/`, `Extra docs/` and `Ops_data/`)
**Also indexed in:** `Test/Ops Reports Details.xlsx` and `CPC_data/SP/Ops Reports details.xlsx`, sheet `Data Defination Index`, rows 505 to 516

Every row has Primary source "Derived", and every note starts "DW fact TBD. OLTP lineage:".

| Data point | Definition | Synonyms | OLTP lineage |
|---|---|---|---|
| TESurveyID | Unique survey instance for a TE. | survey ID; TE survey | tblTESurveyControl.TESurveyID |
| ResponseDate | Date/time the survey answer was submitted. | response date; answered on; survey date | tblTEResponses.CreatedOn |
| SectionOrder | Survey section sequence; section 3 contains supplier questions. | section; section order; survey section | tblSections.SectionOrder |
| QuestionText | Survey question wording. | question; survey question | tblQuestions.QuestionText |
| VendorSelect / SupplierTypeCode | Service code linking a question to a supplier category (HHG RENT MRTG etc.). | supplier type; vendor select; question supplier code | tblQuestions.VendorSelect |
| Response | Numeric or coded survey answer. | response; answer; score | tblTEResponses.Response |
| ResponseText | Open-text survey answer. | response text; open text; comment answer | tblTEResponses.ResponseText |
| ResponseType | Question type (Range Text etc.). | response type; question type | tblQuestions.ResponseType |
| SupplierCompanyName | Supplier name tied to the TE for survey scoring. | supplier name; vendor name | vwTESurveySuppliers.CompanyName |
| SupplierServiceCode | Supplier service category on the TE (HHG DEST MRTG etc.). | supplier service; service category | vwTESurveySuppliers.Service |
| VendorType | Supplier classification: Vendor Broker or Mortgage. | vendor type; broker; mortgage supplier | vwTESurveySuppliers.VendorType |
| LocationName | Supplier location (city or branch) to disambiguate duplicate names. | location; branch; city | vwTESurveySuppliers.LocationName |

---

## 7. Sample reports and screenshots

### DE team screenshot document

**Location:** `dbt/supplier-survery-ops-reports-screenshots.docx`
**Same text and images, inside a larger document:** `Extra docs/Queries to generate sample reports/DW queries/Supplier/Vendor Usage/ops-reports-screenshots.docx`, identical copy under `Ops_data/Queries & Data Points/Queries to generate sample reports/DW queries/Supplier/Vendor Usage/`

| Item | Text |
|---|---|
| Heading | Domain- Supplier Mgmt   - SE ONLY |
| Heading | Report- Survey by Supplier |
| Heading | Sub report count=1 |
| Heading | Sub reports name available- No |
| Table: No / Sub Report / Screenshot Status | 40 / Survey by Supplier / Yes |
| Table: Notes | Report Format  and Report Type were also added |

The rest of the document is images under the three headings below, in this order. All runs are for Company ABBE, with All Service Providers, All Profit Centers and All Suppliers.

#### First run, before the heading "Report Format  : By section"

The dialog's start date shows as "0/30/24" because the first digit is hidden. The report header says 10/30/24.

![Dialog: Summary by Section, Company ABBE](Supplier_Survey_Report_Screenshots/13_de_dialog_section_abbe.png)

![Supplier Survey Results page 1, surveys created 10/30/24 to 10/30/26](Supplier_Survey_Report_Screenshots/14_de_section_oct2026_page1.png)

![Supplier Survey Results page 5, surveys created 11/01/25 to 11/01/26](Supplier_Survey_Report_Screenshots/15_de_section_nov01_page5.png)

#### "Report Format  : By section"

Printed 11/02/26 1:04AM, surveys created between 11/02/25 and 11/02/26. The document has these pages in the order 1, 4, 3, 5. They are placed here by page number.

![Dialog with the Report Format dropdown open](Supplier_Survey_Report_Screenshots/16_de_dialog_format_dropdown.png)

![By section page 1](Supplier_Survey_Report_Screenshots/17_de_section_page1.png)

![By section page 3](Supplier_Survey_Report_Screenshots/18_de_section_page3.png)

![By section page 4](Supplier_Survey_Report_Screenshots/19_de_section_page4.png)

![By section page 5, Total Over all Response](Supplier_Survey_Report_Screenshots/20_de_section_page5.png)

#### "Report Format: By supplier"

Printed 11/2/26 1:05AM, same date range. The report title is "Supplier Survey Detail Results".

![Dialog: Summary by Supplier](Supplier_Survey_Report_Screenshots/21_de_dialog_by_supplier.png)

![By supplier page 1](Supplier_Survey_Report_Screenshots/22_de_by_supplier_page1.png)

![By supplier page 5](Supplier_Survey_Report_Screenshots/23_de_by_supplier_page5.png)

![By supplier page 26](Supplier_Survey_Report_Screenshots/24_de_by_supplier_page26.png)

![By supplier page 27, Total Over all Response](Supplier_Survey_Report_Screenshots/25_de_by_supplier_page27.png)

#### "By supplier with detail:"

Printed 11/2/26 1:07AM, same date range. Show Comments is unchecked in the dialog. The last image is page 30, so the Total Over all Response for this format is not shown.

![Dialog: Summary by Supplier with Detail](Supplier_Survey_Report_Screenshots/26_de_dialog_with_detail.png)

![With detail page 1](Supplier_Survey_Report_Screenshots/27_de_with_detail_page1.png)

![With detail page 2](Supplier_Survey_Report_Screenshots/28_de_with_detail_page2.png)

![With detail page 3](Supplier_Survey_Report_Screenshots/29_de_with_detail_page3.png)

![With detail page 28](Supplier_Survey_Report_Screenshots/30_de_with_detail_page28.png)

![With detail page 29](Supplier_Survey_Report_Screenshots/31_de_with_detail_page29.png)

![With detail page 30](Supplier_Survey_Report_Screenshots/32_de_with_detail_page30.png)

### What the dialog offers

Labels read from the screenshots above:

| Group | Options |
|---|---|
| Title | ROL Survey by Supplier |
| Top selections | Corporate Client, Service Provider, Department (shows "All Profit Centers"), Supplier Type, Supplier |
| Report Format | Summary by Section, Summary by Supplier, Summary by Supplier with Detail |
| Check box | Show Comments |
| Date Range | Start Date, End Date |
| Report Output | Preview, Print, eMail as Attachment, Excel Format |
| Other | Post Report Online (greyed out in the requirements screenshots) |

### What each format shows

Read from the screenshots above:

| Format | Title | Grouping | Rows |
|---|---|---|---|
| Summary by Section | Supplier Survey Results | Survey section, question, then supplier | One count row per supplier |
| Summary by Supplier | Supplier Survey Detail Results | Supplier, survey section, then question | TE rows, with the question label under them |
| Summary by Supplier with Detail | Supplier Survey Detail Results | Supplier, survey section, then question | TE rows, with the question label above them and a "Totals For" row |

**Header lines:** "Surveys Created between [start] and [end]", client ("All Clients" or "For: Company ABBE"), "All Service Providers", "All Profit Centers", "Results for Service Supplier: (All Suppliers)".

**Columns:** Strongly Disagree, Disagree, Slightly Disagree, Slightly Agree, Agree, Strongly Agree, Top Box, Top 2 Box, Top 3 Box.

**TE rows:** file number, name, response. A "(VIP)" marker appears to the left of some TE rows on page 4 of the requirements sample.

**Totals:** per question ("Totals For ..."), per section ("Totals for ... Performance"), and "Total Over all Response" at the end.

**Footnote on each page with a Yes or No question:**

> **Question with a Yes or No response, Yes noted in the "Agree" column and No in the "Disagree" column.

### Survey sections and questions in the Back Office samples

| Section | Question | Sub-item or type |
|---|---|---|
| NuCompass Supplier Performance | I would recommend the following service providers to others. | Automobile transportation provider |
| | | Home mortgage lender |
| | | Household goods movers |
| | | Local service provider who helped you at your destination |
| | | Real estate agent assisting in the purchase of your new home |
| | | Real estate agent assisting in the sale of your former home |
| | | Rental agent assisting with locating rental housing in your new location |
| | | Temporary Accommodations provider |
| Household Goods Movers Performance | `<HHGMover>` accurately explained the claims process to me | Rating |
| | `<HHGMover>` kept me appropriately informed on the status of the claim | Rating |
| | Did you have damage to your household goods for which you submitted a claim? | Yes or No |
| | The `<HHGMover>` representatives were always courteous and professional | Rating |
| | Were your household goods delivered when promised by `<HHGMover>`? | Yes or No |
| Temporary Accommodations Provider Performance | My temporary accommodations consultant addressed my needs in a timely manner | Rating |
| | My temporary accommodations consultant appropriately set expectations regarding which housing preferences could not be met and explained why | Rating |
| | My temporary accommodations consultant was always courteous and professional | Rating |
| | Was `<TLVProvider>` able to accommodate your most important personal preferences? | Yes or No |

### `Supplier Survey Report.xls`

**Location:** `Reports/Building Report Views/Supplier Mgt Reports/Supplier Survey Report.xls`
**Identical copy:** `Sharepoint/Building Report Views/Supplier Mgt Reports/Supplier Survey Report.xls`

Sheet `Sheet1`, 170 rows, printed 03/26/26 11:24AM. Title "Supplier Survey Results" with "Surveys Created between 03/12/26 and 03/26/26", All Clients, All Service Providers, All Profit Centers, "Results for Service Supplier: (All Suppliers)". This is Summary by Section output.

| Row | Label | Str. Disagree | Disagree | Sl. Disagree | Sl. Agree | Agree | Str. Agree | Top Box | Top 2 | Top 3 |
|---|---|---|---|---|---|---|---|---|---|---|
| 67 | Totals for NuCompass Supplier Performance | 0 | 0 | 2 | 3 | 7 | 36 | 75.0 | 89.6 | 95.8 |
| 135 | Totals for Household Goods Movers Performance | 0 | 0 | 0 | 0 | 19 | 0 | 0.0 | 100.0 | 100.0 |
| 162 | Totals for Temporary Accommodations Provider Performance | 0 | 2 | 0 | 0 | 12 | 20 | 58.8 | 94.1 | 94.1 |
| 166 | Total Over all Response | 0 | 18 | 2 | 3 | 48 | 78 | 52.3 | 84.6 | 86.6 |

---

## 8. View specs

No NCM view spec was found for this report. The Workload and Transferee Survey reports each have one.

**Location:** `Reports/NCM Service Information View for Approval 10.14.26.xlsx`, sheet `supplier reports`
**Same cells in:** `Reports/Archive/NCM Service Information View Approved 5.13.26.xlsx`

| Cell | Text |
|---|---|
| G1 | Supplier Survey Results |
| G3 | no requirements for Supplier Surveys |

---

## 9. Service Engine objects

The survey form is the same Customer Satisfaction Survey (form 0164) used by the Transferee Survey report. Its view, tables and sending process are in section 9 of `Transferee_Survey_Report_All_Points.md`. This section covers only the supplier side.

### Supplier sections in the survey template

**Location:** `dbt/Only SE Reports/NewTables/form_0164_customer_satisfaction_survey_section_template.csv` and `form_0164_customer_satisfaction_survey_section_detail_template.csv`, survey template 1. Question text is URL-decoded. Role names are from `role.csv`, and service names are from `dbt/Only SE Reports/NewDump/code.csv`.

| Section (seq) | Question | Type | Allowed service | Contact role | Inactive | Weights |
|---|---|---|---|---|---|---|
| Household Goods (3) | How satisfied were you with the overall quality of the moving services provided? | RATING | C217 Household Goods | 219 Household Goods Provider | | 1 2 3 4 5 |
| Household Goods (3) | Was your destination Rental Agent referred by OneSource Relocation? | YESNO | C254 Home Finding Renting | 1, no description | Y | |
| Auto Shipment (4) | How satisfied were you with the overall quality of your automobile transportation experience? | RATING | C236 Automobiile Shipment | 220 Auto Shipper | | 1 2 3 4 5 |
| Temporary Living (5) | How satisfied were you with your corporate housing experience? | RATING | C228 Temp Living | 1, File Manager | | 1 2 3 4 5 |
| Cross-Cultural Training (6) | How satisfied were you with the Cultural Training provider? | RATING | C238 Cross-Cultural Training | 0, empty | | 1 2 3 4 5 |
| Language Training (7) | How satisfied were you with the Language training provider? | RATING | C240 Eval Language Training | 0, empty | | 1 2 3 4 5 |
| Destination Services (8) | How satisfied were you with the local service provider who helped you at your destination? | RATING | C213 Career and Family | 0, empty | | 1 3 3 4 5 |
| Furniture Rental (9) | Please rate your furniture rental experience. | RATING | none | 0, empty | Y | 1 2 3 4 5 |

The other sections are NuCompass Mobility Inc., NuCompass Consultant, Expense Management, CoPilot and Other Comments or Feed Bak. The three free-text questions are all in the last one.

**Rating labels:** `form_0164_customer_satisfaction_survey_rating_template.csv` lists Very Satisfied, Satisfied, Somewhat Satisfied, Dissatisfied, Very Dissatisfied.

### How SE identifies a supplier

**Location:** `CPC_data/SP/allReportView.txt`, lines 14577 to 14586, in `udv_transferee_survey_view_34`. The same CTE is at line 13468 of `udv_service_detail_view_34`, which selects it as `'Supplier Name'` at line 13546.

```sql
supplier_names (serv_uid, supplier_names) as
(
	select csr.serv_uid, STRING_AGG(o.org_name, ',')
	from cust_serv_roles csr with (nolock)
	join contact c with (nolock) on c.cont_uid = csr.cont_uid
	join organization o with (nolock) on o.org_uid = c.cont_org_uid
	join file_type ft with (nolock) on ft.file_type = o.org_class
	where ft.serv_class = 'EVAL  '
	group by csr.serv_uid
),
```

### Supplier tables

| Table | Location | Notes |
|---|---|---|
| `file_type` | `dbt/Only SE Reports/NewTables/file_type.csv` | `serv_class` EVAL has two rows: ORG203 Supplier and ORG206 zAuthorization Folder (test) |
| `org_type` | `dbt/Only SE Reports/NewTables/org_type.csv` | 106 rows, 99 organizations, 7 of them with more than one type |
| `organization` | `dbt/Only SE Reports/NewDump/organization.csv` | 93 of 158 rows are class ORG203. None are ORG206 |
| `code`, type ORGTYP | `dbt/Only SE Reports/NewDump/code.csv` | 28 types, for example Van Line, Temporary Accommodations, Auto Shipment, Mortgage, Real Estate, Rental Agent |
| `form_3415_supplier_service_order` | `dbt/Only SE Reports/NewTables/form_3415_supplier_service_order.csv` | 154 rows. Added to `_sources.yml`, but no model reads it |

### Survey sections in the data extracts

| Extract | Location | Sections found |
|---|---|---|
| NewTables | `dbt/Only SE Reports/NewTables/form_0164_customer_satisfaction_survey_section.csv` | 1 survey, form 19043: NuCompass Mobility Inc., NuCompass Consultant, Expense Management, CoPilot, Other Comments or Feed Bak |
| SE_DEV | `Test/SE_DEV(main)/dbo.form_0164_customer_satisfaction_survey_section.csv` | 6 surveys, 29 rows: the same five sections, plus the spelling "Other Comments or Feed Back" |

Neither extract has a Household Goods, Auto Shipment, Temporary Living, Cross-Cultural Training, Language Training or Destination Services section.

---

## 10. Legacy Back Office objects

The survey database and tables are in section 10 of `Transferee_Survey_Report_All_Points.md`. The columns that matter for suppliers are listed here.

**Location:** `CPC_data/SP/2ReloSCHEMA.csv`

| Table | Supplier-related columns |
|---|---|
| `tblTEResponses` | GenericVendorID, VendorType, ResponseComments, CommentsExist |
| `tblQuestions` | VendorSelect (line 4197), VndrSrvcID, CommentsAssociated, CommentLabel |

### Table `tblTmpSurveySupplier`

**Location:** `CPC_data/SP/ReloSchema.csv:9530-9549`, also `CPC_data/SP/2ReloSCHEMA.csv:10404-10423`
**Data:** `CPC_data/SP/Allrelo.csv:663` holds the table name with NULL sample data.

```text
RecordID, TEFileNo, CorpCode, ProfitCenter, Initials, QuestionID, QuestionHelp, DateCreated,
QuestionText, ResponseNumeric_a, SurveyTitle, ResponseSeqID, ResponseText_a, SupplierID,
CompanyName, SupplierType, ServiceCode, ContactName, OrderDate, PrimaryContact
```

No stored procedure in `CPC_data/SP/allReloSP.csv` mentions this table or `vwTESurveySuppliers`. The `.rpt` report and the code behind the ROL Survey by Supplier dialog are not in the folder, and `vwTESurveySuppliers` is not in the schema files. So the Back Office logic for Top Box, NA handling and supplier selection could only be read from the sample output.

---

## 11. dbt models

All files below were last changed on 2026-11-05 at 11:09 unless stated otherwise.

### `dbt/dbt/models/marts/Facts/FactSupplierSurvey.sql`

Lines 1 to 4:

```sql
-- Gold FactSupplierSurvey: Service Engine rows only (int_se_fact_SupplierSurvey), one per survey question per supplier.
-- Feeds the Survey by Supplier report. Column names match FactTransfereeSurvey where they overlap.
-- No NCM counterpart, so no union model and no KeyMap IDs.
-- The NCM index post-hook finds no rows for this table and does nothing.
```

The 28 columns, in order:

```text
Client, Client Name, File #, Name, Consultant, Division, Policy, Move Type, Survey ID,
Survey Sent Date, Survey Section Number, Survey Section Name, Survey Section Question Number,
Survey Question, Rating Points, Yes or No Response, Text Response, Rating, Remove From Report,
Remove From Calc, Display Response, Supplier ID, Supplier, Supplier Type, Supplier Role,
Supplier Match, Suppliers On Question, udv_cust_uid
```

### `dbt/dbt/models/intermediate/SE/service_engine/fact/int_se_fact_SupplierSurvey.sql`

Lines 1 to 15:

```text
{# FactSupplierSurvey -- grain: one row per survey question per supplier.
   The SE replacement for the Back Office Survey by Supplier report (tracker ID 47). The survey
   tables have no supplier column, so each answer in a supplier section is credited to:
     1. the question's contact, when that contact belongs to a supplier organization;
     2. otherwise the supplier filling the section's role on a service of the same program.
   Route 2 can find more than one supplier (a program with two auto shippers): each gets a row,
   and suppliers_on_question shows the answer is shared.

   supplier_sections is ours, not SE's: the template can't give the supplier for these sections.
   Its contact_role is 'File Manager' on Temporary Living and empty on the training and destination
   sections, and allowed_service_types holds codes that real services don't use (Household Goods
   lists C217 and C254; household goods shipments are C250). To confirm with Supplier Mgt.
   Furniture Rental is left out: its one question is inactive and no role matches it.

   The answers come from int_se_fact_TransfereeSurvey, so both reports read the same responses. #}
```

Lines 17 to 27:

```sql
with supplier_sections as (
    select section_name, role_uid
    from (values
        ('Household Goods',         219),   -- Household Goods Provider
        ('Auto Shipment',           220),   -- Auto Shipper
        ('Temporary Living',        234),   -- Temp Living Provider
        ('Cross-Cultural Training', 309),   -- Cultural Training Provider
        ('Language Training',       312),   -- Language Training Provider
        ('Destination Services',    333)    -- Destination & Settling in and Repat
    ) as v (section_name, role_uid)
),
```

Line 100:

```sql
    count(*) over (partition by c.form_uid, c.survey_section_question_number) as suppliers_on_question
```

### `dbt/dbt/models/intermediate/SE/service_engine/fact/int_se_fact_TransfereeSurvey.sql`

Lines 166 to 169 add the keys the supplier model needs. Line 108 builds the question number as `concat('S', csss.seq, ' Q', csssd.seq_section_detail)`, so it is unique across sections.

```sql
    -- Not in gold FactTransfereeSurvey: the keys int_se_fact_SupplierSurvey needs.
    p.program_uid,
    css.form_uid,
    csssd.question_cont_uid
```

### `dbt/dbt/models/marts/_gold.yml`, lines 894 to 904

```yaml
  - name: FactSupplierSurvey
    description: >
      Service Engine only (no NCM rows, no KeyMap IDs): one row per survey question per
      supplier, for the Survey by Supplier report. Supplier sections of the survey only.
    columns:
      - name: "File #"
        quote: true
        data_tests: [not_null]
      - name: Supplier ID
        quote: true
        data_tests: [not_null]
```

### `dbt/dbt/models/_sources.yml`, lines 100 to 106

```yaml
      # Added for FactSupplierSurvey: which organizations are suppliers, and their type.
      # No ct_* change tables exist for these, so they are snapshot-only.
      - name: file_type                       # organization class -> serv_class (EVAL = supplier)
      - name: org_type                        # organization -> ORGTYP code (Van Line, Mortgage, ...)
      - name: form_type                       # form type names
      - name: form_0164_customer_satisfaction_survey_rating_template  # rating labels per template
      - name: form_3415_supplier_service_order  # supplier service orders
```

### Staging models

`dbt/dbt/models/staging/service_engine/snapshot/stg_se__org_type.sql`:

```text
  The ORGTYP code(s) of an organization (Van Line, Mortgage, ...). An
  organization can have more than one row.
```

`dbt/dbt/models/staging/service_engine/snapshot/stg_se__file_type.sql`:

```text
  Organization classes. serv_class 'EVAL' marks the supplier classes
  (organization.org_class = file_type.file_type).
```

`stg_se__cust_serv_roles.sql` and `stg_se__role.sql` in the same folder were already there, dated 2026-11-04.

### Run log

**Location:** `dbt/dbt/logs/dbt.log`, lines 169370 to 169844. Colour codes are removed.

```text
11:09:34.515796 [info ] [Thread-2 (]: 5 of 9 OK created sql view model intermediate.int_se_fact_SupplierSurvey ....... [OK in 0.25s]
11:09:36.037666 [info ] [Thread-2 (]: 6 of 9 OK created sql table model dbo.FactSupplierSurvey ....................... [OK in 1.51s]
11:09:36.118165 [info ] [Thread-1 (]: 8 of 9 PASS not_null_FactSupplierSurvey__File_ ................................. [PASS in 0.07s]
11:09:36.128882 [info ] [Thread-2 (]: 9 of 9 PASS not_null_FactSupplierSurvey__Supplier_ID_ .......................... [PASS in 0.08s]
11:09:36.783309 [info ] [MainThread]: Done. PASS=13 WARN=0 ERROR=0 SKIP=0 NO-OP=0 TOTAL=13
```

The log gives no row count for the table.

### Not built yet

- No cube: `dbt/cubes/` has `supplier_diversity_spend.yml` only for supplier reports.
- No sample report page: `dbt/Only SE Reports/` has HTML pages for Workload and Transferee Survey only.
- `SE_Reports_Summary.md` does not mention this report.

---

## 12. Searched but not quoted

| Item | Why it is not quoted |
|---|---|
| `Reports/Ops Reports_Data def and sample/Supplier/SupplierSampleData.xlsx` | Sheets cover Supplier Usage, Diversity Spend and Mortgage Referrals only. It has no survey sheet |
| `Queries to generate sample reports/DW queries/Supplier/` | Folders for Mortgage Referrals, Diversity Spend and Vendor Usage. There are no survey queries |
| `Reports/Business Owners List Reports- BO vs SE  data fields.xlsx`, `Screen Shots !E247` | An image of the LOC Interest Calculation Report sits in the Survey by Supplier block, apparently placed there by mistake |
| `Reports/Ops Reports_Data def and sample/REM/REMSampleData.xlsx` | False match: expense text about a household goods survey |
| `dbt/xtra_doc/mapping/AlldevView.txt:482` | False match: a replication sync view |
| `Sharepoint/Client Note Explained - Supplier Usage and Active TE.txt`, `Sharepoint/Supplier Usage and Active TE - Summary.txt` | No survey mention |
| `dbt/dbt/target/` | Generated copies of the dbt models in section 11 |
| `*.zip` files | Not opened |
| `*.mp4` files | Not searched: video content can't be read this way |
| `*.msg` email files | Not searched for this report |
| `Reports/Building Report Views/Expense Mgt Reports/DNU Client Expense Payment Example 1.xlsx` | Could not be opened: the file is not a valid xlsx |

---

## 13. Observations (mine, not from the source files)

These are my own notes on where the sources disagree or leave gaps. Nothing here was checked against a database. Items are ordered with the ones most likely to affect the report first.

1. **`FactSupplierSurvey` is probably empty today.** It keeps only six supplier sections, and neither data extract has a survey with any of them (section 9). `SE_Reports_Summary.md` says the live survey table has 1 survey with 8 rows, which matches the NewTables extract of 5 non-supplier sections. The two passing `not_null` tests would also pass on an empty table. A row count would settle this, and the supplier logic has not been tested on real data until supplier sections exist.
2. **Comments can't come from this table as built.** The business says Show Comments is always checked. In SE the free-text questions are in "Other Comments or Feed Bak", which the fact leaves out, and no supplier question has a verbatim in the template. `Text Response` will therefore usually be blank. Those comments are also not tied to a supplier, so the business needs to say how they should appear.
3. **Most Back Office supplier types have no SE survey question.** Mortgage, HFP Agent, Home Sale Agent, Rental Assistance and Property Management have no section. Household goods, auto and temporary housing do, and SE adds cultural training, language training and destination services. Agents and lenders appear in the samples, so scorecards for those suppliers would stop. Supplier Mgt should confirm this is intended.
4. **The SE survey has far less to report.** Back Office has several questions per service line, plus a "would recommend" question per supplier type. SE has one rating question per supplier section. The plan to "compare manually" can't match question for question.
5. **The report's columns need redefining.** Back Office uses a six-point Agree scale and SE uses a five-point Satisfied scale, so the six columns and the Top Box, Top 2 Box and Top 3 Box meanings need a decision. None of these exist in the fact. In the samples, Top Box is Strongly Agree divided by counted responses, Top 2 adds Agree, and Top 3 adds Slightly Agree. For example, row 64 of the `.xls` gives 9 of 12 = 75%. SE's points also run backwards, with Very Satisfied at 1, so calculations should use the `Rating` label (see observation 1 in the Transferee file).
6. **Supplier credit is inferred, not recorded.** Back Office stored `GenericVendorID` on each response. SE has no such column, so the model uses the question contact, then the role on any service in the program. That can credit a supplier who wasn't the one being rated. The six `role_uid` values are hard-coded and the model itself marks them "To confirm with Supplier Mgt".
7. **Shared answers will inflate totals.** When two suppliers share a question, the answer gets two rows. That is right for each supplier's own score, but a "Total Over all Response" would count it twice. The report needs to count distinct `Survey ID` + question for overall totals.
8. **Answers with no supplier disappear silently.** The joins are inner, so a supplier-section answer with no matching supplier is dropped. The `Supplier ID` test can't catch this. A count against `FactTransfereeSurvey` for the same sections would show it.
9. **The fact is missing some report fields.** Gold has no VIP flag (the samples show "(VIP)", and the intermediate model has `client_vip` and `ncm_vip`). It also lacks Service or Service Type (`BO Data Fields!B55`) and a response or complete date. Remove From Report and Remove From Calc are carried but must still be applied by the report.
10. **The date filter needs confirming.** Back Office filters on "Surveys Created". The fact has `Survey Sent Date`, the first date the sending action became active, which seems the closest match. `ResponseDate` in the data definitions is a different date.
11. **The Supplier Type filter won't work directly.** The business expects values like HHG, while `Supplier Type` holds ORGTYP descriptions like Van Line, joined with commas when an organization has several (7 of 99 in `org_type.csv`). `Survey Section Name` or `Supplier Role` looks like a better filter.
12. **"Service Provider" means two things.** In the dialog it is the NuCompass consultant, so the filter maps to `Consultant`. `BO Data Fields!B54:C54` maps it to "Supplier Authoorized?", and B63 says "Total by Supplier Provider".
13. **One Yes or No question distorts Back Office scores.** "Did you have damage..." counts No under Disagree, so a good outcome lowers the score and a claim raises it. All 23 Disagree responses in the ABBE By section run (page 3 and page 5) come from this question, and 16 of the 18 in the `.xls`. Without it, ABBE's Top 2 Box would be about 97% instead of 89%. This matters when comparing old scores with SE scores. Yes answers also can never reach Top Box.
14. **NA is shown but not counted.** "NA" rows appear in the detail with no count in any column, which may explain the suppliers with all zeros. SE has no NA rating, and an unanswered question has Rating Points 0, so the report must leave out rows where `Rating` and `Yes or No Response` are both blank.
15. **Summary by Section totals look wrong in Back Office.** The section total restarts when the section heading repeats. In the `.xls`, row 135 shows 19 for Household Goods, but the questions add up to 16 Disagree, 29 Agree and 22 Strongly Agree. ABBE page 4 shows the same pattern, leaving out the page 3 questions. Total Over all Response is correct. This format isn't used, but don't reconcile against those section totals.
16. **Two formats give different totals for the same dates.** By section has 283 counted responses (0, 23, 4, 3, 112, 141), and By supplier has 279 (0, 23, 4, 2, 111, 139). The runs were a minute apart with the same filters. I could not tell why, and the With Detail total isn't in the document.
17. **The report count is unclear.** `Report List by RB` lists four report lines but counts 1, and the DE document says "Sub report count=1". The business says it uses only Summary by Supplier with Detail. Summary by Supplier looks almost the same, apart from where the question label sits. The DE note says formats were added, so confirm whether the "grouped by" versions are separate outputs or just filters.
18. **The model comment on service codes overstates the case.** It says C217 and C254 are codes "real services don't use", but `NewDump/service.csv` has 7 services on C217 and 220 on C254. C250 does have the most, at 432. C254 is Home Finding Renting and is only on the inactive question. Destination Services allows C213, which is Career and Family and has no services in the extract. Since the model doesn't use these codes, this affects only the comment.
19. **The Destination Services weights look like a typing error.** They are 1 3 3 4 5, as noted in the Transferee file. This changes Rating Points on that supplier question.
20. **No approved spec exists.** Workload and Transferee Survey have NCM view specs, but this report has none, and the Service Information spec says "no requirements for Supplier Surveys". The fact's design hasn't been signed off by the business, which is more of a risk here because the supplier link is our own logic.
21. **The trackers are out of date against dbt.** `Test/Tracker.xlsx` row 49 says "No fact yet" and "Not Started", but `FactSupplierSurvey` built successfully on 2026-11-05. It also says Data Definitions Doc "No", though section 6 has them. The Business Owner is blank or TBC, while `Contents!D14` says Anna.
22. **The tracker numbers differ.** This report is ID 47 in `Tracker.xlsx`, 40 in `currentTracker.xlsx` and the DE document, and 52 in the Reporting Work Tracker.
23. **The screenshots have small inconsistencies.** No sample shows a comment, so the comment layout is unknown, and the dialogs in the DE document and at `A34` have Show Comments unchecked. The dialog at `A34` shows 06/29/26 to 06/30/26, while the report under it says 06/30/26 to 07/01/26, so they may be different runs. The DE document's first run pairs page 1 (10/30/24 to 10/30/26) with a page 5 from a different date range (11/01/25 to 11/01/26).
24. **This file contains real names.** The requirements screenshots show transferee names, and supplier performance scores are commercially sensitive, so take care if you share it outside the team.
