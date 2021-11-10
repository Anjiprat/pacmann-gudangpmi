# PMI Warehouse Monitoring Dashboard


# Background
Palang Merah Indonesia is a humanitarian organization based in Indonesia. During the COVID-19 pandemic, they constructed seven temporary warehouses in Jakarta to help distribute logistics for COVID-19 related aid throughout the country. The dataset refers to shipments to and from these temporary warehouses. 

# Objectives
With this dataset, I aimed to create a simple dashboard in Tableau to help PMI's central logistic managers and warehouse managers to do their their jobs, namely to assess warehouse stock and make decisions on shipments and procurement of goods. The dashboard is designed to so that users, especially central logistic managers, can easily get information about warehouse stock, the types of items needed, and predict incoming demands via the flow of goods as well as COVID-19 status per province.


# File descriptions
 In this table you'll find a short description for each file available.
| File      | Description |
| ----------- | ----------- |
| Annas-9za3-Project Lab PMI-Milestone3-24oct21.ipynb      | The Jupyter Notebook used to clean, wrangle, and otherwise prepare data for dashboard development inTableau       |
| Pacmann - PMI Warehouse Demo.twbx   | The Tableau dashboard demo. Also available here: https://public.tableau.com/app/profile/annas7867/viz/Pacmann-PMIWarehouseDemo/WarehouseDashboard?publish=yes          |
| COVID-19 di Indonesia @kawalcovid19.xlsx   | COVID-19 dataset           |
| df_item_sort.csv  | Manually categorized item names. A key dataset to be merged with the warehouse dataset.         |
| df_covid_merged.csv  | The final covid-19 cases dataset used for the Tableau dashboard        |

# Files available upon requests
The table below are for files that are crucial in the reproduction of this dashboard, buat which are confidential. They may be made available upon contact.

| File      | Description |
| ----------- | ----------- |
| Laporan Gudang Darurat PMI (s.d. 27 April 2021).csv  | The raw warehouse dataset from PMI. This dataset is not uploaded as it is confidential. Available upon clearance from Pacmann.         |
| pt_daily_merged.csv | Daily warehouse data. This is the main dataset used for Tableau development         |
| df_pmi_merged.csv  | Cleaned version of the warehouse data. Used for the detailed table in the dashboard, which functions mainly to inform faulty data.         |



# Process
Below is the general workflow of the development. All steps in these process are recored in ```Annas-9za3-Project Lab PMI-Milestone3-24oct21.ipynb```.

1. Set up 
- Load the datasets ```Laporan Gudang Darurat PMI (s.d. 27 April 2021).csv``` and ```COVID-19 di Indonesia @kawalcovid19.xlsx```.
- For COVID-19, total active cases per day, new cases per day, and recoveries per day are extracted from the excel file. 
2. PMI data cleaning and wrangling
- Inspect object types and missing data
- Fill missing data with 0 and mark them, as faulty, recorded in the column ```tag_bermasalah```. This is important as managers would want to check in with warehouses for faulty reports.
-  Extract other warehouses from the data. As the data only records emergency warehouses, transactions to and from other PMI warehouses are used to assess stocks. New warehouses are added as values to the ```gudang``` column, which denotes all warehouse IDs.
-  Create item categories. Item categories are manually added. First, I extracted unique values from item names into a sheet. Then, I assign categories to those values, and save them. The sheet is later joined to the main table, so that each row would have a category for its items, in the column ```kategori```. 
-  Finally, I create a running total table, with a row for each warehouse, category, and date, ```pt_daily_merged.csv```. The cleaned version of the raw dataset is also imported, named ```df_pmi_merged.csv```. 
3. COVID-19 data cleaning and wrangling
- Fill missing data with 0. All missing data for these tables are where there are no new cases or recoveries.
- Reshape table into long format, so that each rows represent each day for each province 
- Combine the tables for total active cases, new cases, and recoveries, into a single table. Save to ```df_covid_merged.csv```.
4. Tableau dashboard development
- The dashboard is developed in Tableau, and can be accessed in the workbook ```Pacmann - PMI Warehouse Demo.twbx```.
