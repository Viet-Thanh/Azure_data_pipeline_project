# Overview

Building a data pipeline in MS Fabric to monitor the KPI of the Innovation team on a Power BI dashboard. The pipeline will automatically collect, process, and update data monthly from files stored on SharePoint and MS Teams, ensuring the dashboard always reflects the latest information.

![image](https://github.com/user-attachments/assets/1557a525-642a-48d4-a4f0-cc51400b0a7e)

# Technologies Used

- **Azure Data Factory (ADF):** Orchestration and data integration.
- **Azure Databricks:** Data processing and transformation.
- **Azure Synapse Analytics:** Data warehousing and analytics.
- **Power BI:** Data visualization and reporting.
- **Azure Data Lake Storage :** Storage solution for raw and processed data.

# About datasets

The dataset consists of 23 columns and 43 rows, capturing the KPI progress of the Innovation team. It specifically tracks the progress of each task, the responsible individual, and performance month by month.

**Columns:**
1. Department
2. KPI
3. Percent
4. Category Brearkdown
5. Task
6. Measurements
7. Type
8. Total
9. -> 20.  :  Jan -> Dec
 * **3 col haven't name** 

*Dataset*: https://docs.google.com/spreadsheets/d/1lLZjdCUt-r0-cNRhAVFx7YquVmgQJw2f/edit?usp=drive_link&ouid=107421613910963997740&rtpof=true&sd=true

# Ingest data

Use **Data flow gen 2** in **Microsoft Fabric** to ingest data from **.csv** file stored on SharePoint and MS Teams into the **Data Lake**. The ingestion process is scheduled to run monthly, ensuring the latest KPI data is available for processing.

![image](https://github.com/user-attachments/assets/51ed5adc-fb16-4185-9a48-b9ffcdd011b8)

# Processing data

The data is cleaned and organized following the star schema model, which is a widely used data modeling approach in analytics.

## Star Schema

![image](https://github.com/user-attachments/assets/d0dce870-32f2-4bf4-9435-f37b3a1dc5d0)

## Update and insert

After the data is cleaned and structured into a star schema, the next step is to update and insert data based on the Load_Date field.

**1. Ensuring the Latest Data is Always Updated**
Load_Date helps determine when the data was loaded into the system.
When new data is ingested, the system compares it with the existing data to update only what has changed, avoiding overwriting everything.  

**2. Preventing Duplicate Data**
If a KPI record already exists in the Fact Table, instead of inserting a new record, the system updates the latest value based on Load_Date.
If the KPI does not exist, the system inserts a new record.

*3. Efficiently Storing Historical Data**
If you need to track KPI changes over time, Load_Date can be used to retrieve data for each update cycle.
This is useful for analyzing KPI performance across different periods.
