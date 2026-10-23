# Sales Order Item Display Using Module Pool Programming

## Project Overview

This project is a classic SAP ABAP dialog-programming exercise for displaying sales order item data. The main program, `ZJULY_DEMO16`, reads item-level information from the SAP standard table `VBAP` for a sales order number entered through the application flow and stores the results in an internal table for display.

The supplied source includes table-control handling routines, screen flow logic for screen `0101`, and input-processing modules for sales order entry and material validation.

## Project Objectives

- Retrieve sales order item details using ABAP Open SQL.
- Work with SAP standard sales-document tables.
- Store and process database results using an internal table and work area.
- Practice classic Module Pool Programming and screen flow processing.
- Handle table-control navigation and row operations.
- Validate material numbers against the material master table.

## Technologies and Concepts

- **Language:** SAP ABAP
- **Programming model:** Module Pool Programming
- **Database access:** ABAP Open SQL
- **SAP tables:** `VBAP`, `VBAK`, `MARA`
- **Data handling:** Internal tables and work areas
- **Screen processing:** PBO/PAI flow logic
- **Tabular UI element:** Table control `VBAP_TABLE`
- **Value request:** Sales order input help module

## Data Sources

| SAP table | Purpose in the source |
|---|---|
| `VBAP` | Sales document item data, including document number, item number, and material number |
| `VBAK` | Sales document header data; used by the sales-order value-request logic |
| `MARA` | Material master validation for the material number |

### Main item fields

| Field | SAP field | Description |
|---|---|---|
| `VBELN` | `VBAP-VBELN` | Sales document number |
| `POSNR` | `VBAP-POSNR` | Sales document item number |
| `MATNR` | `VBAP-MATNR` | Material number |

## Functional and Technical Highlights

1. **Sales order item retrieval**  
   The source contains an Open SQL query that selects `VBELN`, `POSNR`, and `MATNR` from `VBAP` for the entered sales order number (`LV_SO`).

2. **Internal-table processing**  
   Selected records are stored in `GT_VBAP`, with `WA` used as the row work area.

3. **Table-control processing**  
   The source declares table control `VBAP_TABLE` for screen `0101` and includes routines for scrolling, inserting rows, deleting marked rows, and marking or demarking rows.

4. **Material validation**  
   The `CHECK_MAT` input module contains a query against `MARA` to check whether the material number exists.

5. **Sales order value request**  
   The screen flow logic assigns a value-request event to `LV_SO`, handled by `SALES_ORDER_VAL`. The supplied source includes a query that reads recent sales-document header data from `VBAK`.

6. **Screen event handling**  
   The screen flow source defines Process Before Output (PBO), Process After Input (PAI), and Process On Value-Request event flow.

## Repository Structure

```text
.
├── Sales_Order_Item_Display_Using_Module_Pool_Programming.abap
├── screen_painter_Display_screen_101_code.abap
├── README.md
└── screenshots/
    ├── sales-order-item-screen.png
    └── sales-order-item-output.png
```

The screenshot filenames above are placeholders. Create the `screenshots` folder and add your own screenshots from SAP GUI, using the same filenames or updating the Markdown links below.

## Output Screenshots

### 1. Application Screen



<img width="1862" height="947" alt="image" src="https://github.com/user-attachments/assets/0de1c96d-bdc6-43cc-84a1-bb80c4a4c30b" />


### 2. Sales Order Item Display

<img width="1870" height="941" alt="image" src="https://github.com/user-attachments/assets/f1bade8f-fe84-4436-bdae-a5909b20bbd8" />



## How to Set Up and Test

This repository contains ABAP source files, not a standalone executable application. To test it, use an SAP development system with suitable access.

1. Create or open the module pool program `ZJULY_DEMO16`.
2. Configure screen `0101` and its table control `VBAP_TABLE` in the SAP development environment.
3. Maintain the screen layout and ensure the screen fields correspond to the names used in the ABAP source.
4. Add or verify the included programs:
   - `ZJULY_DEMO16_PBO`
   - `ZJULY_DEMO16_PAI`
5. Maintain the supplied screen flow logic for screen `0101`.
6. Verify that the referenced modules are implemented and that the program, screen, and includes activate successfully.
7. Execute the application through the transaction or development launch method configured in your SAP system.
8. Test with an authorized sales order number and verify the displayed item data.

The exact setup depends on the SAP system and on the implementations of the referenced includes and modules.

## Current Scope and Notes

The supplied source files demonstrate the main program structure, database queries, table-control routines, and screen flow logic. The main program references the `ZJULY_DEMO16_PBO` and `ZJULY_DEMO16_PAI` includes, whose full contents were not part of the supplied files. Review those includes and test the complete application before claiming end-to-end validation.

The source also contains a `SELECT` query against `VBAK` that uses an internal table named `IT_VBAK`; confirm that this table is declared in the relevant implementation before activation.

## Learning Outcomes

- Practicing ABAP Open SQL for sales document data retrieval.
- Understanding the relationship between sales document headers (`VBAK`) and items (`VBAP`).
- Using internal tables and work areas to process database results.
- Implementing input validation against the material master (`MARA`).
- Understanding PBO/PAI event flow and value-request processing.
- Working with table-control operations in classic SAP GUI applications.

## Author

**Omkar Shirsath**

SAP ABAP learning project focused on sales order item data retrieval and classic dialog-programming concepts.

---

*For learning and portfolio demonstration purposes. Use appropriate authorizations and test data when working with SAP business data.*
