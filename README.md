## Overview

Building a data pipeline in MS Fabric to monitor the KPI of the Innovation team on a Power BI dashboard. The pipeline will automatically collect, process, and update data monthly from files stored on SharePoint and MS Teams, ensuring the dashboard always reflects the latest information.

![image](https://github.com/user-attachments/assets/1557a525-642a-48d4-a4f0-cc51400b0a7e)

## Technologies Used

- **Azure Data Factory (ADF):** Orchestration and data integration.
- **Azure Databricks:** Data processing and transformation.
- **Azure Synapse Analytics:** Data warehousing and analytics.
- **Power BI:** Data visualization and reporting.
- **Azure Data Lake Storage :** Storage solution for raw and processed data.

## About datasets

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
 * **3 havent name** 

*Dataset*: https://docs.google.com/spreadsheets/d/1lLZjdCUt-r0-cNRhAVFx7YquVmgQJw2f/edit?usp=drive_link&ouid=107421613910963997740&rtpof=true&sd=true

## Ingest data

Use **Data flow gen 2** in **Microsoft Fabric** to ingest data from **.csv** file stored on SharePoint and MS Teams. The ingestion process is scheduled to run monthly, ensuring the latest KPI data is available for processing.

![image](https://github.com/user-attachments/assets/51ed5adc-fb16-4185-9a48-b9ffcdd011b8)

## 
