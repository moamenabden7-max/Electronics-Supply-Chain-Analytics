# Electronics Supply Chain Analytics

A graduation project covering electronics procurement, inbound quality, inventory, production and customer fulfillment, using SQL Server and Power BI.

## Open the final dashboard

1. Download **SupplyChain_Final.zip** from this repository, extract it completely, and open its SupplyChain_Final folder.
2. Install a current Power BI Desktop version with PBIP/PBIR support.
3. Run `OPEN_POWERBI.cmd` on Windows. It updates the `DataFolder` parameter to the extracted `data_gold` folder and opens `SupplyChain_Updated.pbip`.
4. Select **Refresh** to import the prepared CSV data.

Alternatively, open `SupplyChain_Updated.pbip` manually and set **Transform data > Manage parameters > DataFolder** to the absolute path of `data_gold`, then Close & Apply.

Keep the PBIP file and its Report and SemanticModel folders together. The project uses **Import** mode. The prepared CSV files allow reviewing the dashboard without SQL Server.

## Final report pages

- Warehouse & Customer Fulfillment
- Supply Chain Overview
- Vendor & Purchase Order Performance
- Goods Receipt & Quality Control

The final report and semantic model were supplied by Moamen after Desktop edits. This repository preserves those report definitions. The model contains 36 tables and 88 measures, including hidden display and chart helper measures.

## Data and SQL

- `data_gold/` contains prepared analytical extracts used by the Power BI model.
- `SQL/raw_data/` contains 31 synthetic source tables with 200,000 business rows.
- `SQL/INSTALL_ALL.sql` installs the Bronze, Silver and Gold definitions in `ElectronicsSupplyChainDB_v2`.
- `SQL/scripts/07_Run_Pipeline.sql` loads the source files. Update its source folder path before running.
- `SQL/tests/verify_package.py` runs the offline source-data and relational checks with Python.
- `SQL/MODEL_GUIDE_AR.md` explains grains, relationships and metric definitions.

SQL follows **Bronze → Silver → Gold**. The Power BI model imports the prepared extracts. Refreshing these CSV partitions does not execute the SQL ETL or regenerate the extracts from raw files.

## Interpretation

Sales values use reference selling prices, and estimated profit uses standard costs. Inventory is a current snapshot and does not become historical inventory when the report year changes. Date filters use the active date role of each fact. Product filters affect product-linked facts, while procurement without a product key remains outside that scope.

## Validation

The SQL package passed 342 offline Python Decimal / SQLite checks. Final report files were checked for valid JSON, linked paths and byte-for-byte preservation against the supplied final archive. SQL Server execution and full DAX validation were not performed in the build environment. Desktop rendering is based on the author's final saved files.

## Author

Moamen Taha Abuzied  
[LinkedIn](https://www.linkedin.com/in/moamen-taha-data-analyst/) · [GitHub](https://github.com/moamenabden7-max)

## Repository packaging

The complete editable project, SQL scripts, raw and prepared data are bundled in `SupplyChain_Final.zip` to preserve the project folder structure. Extract the archive before opening the PBIP file.
