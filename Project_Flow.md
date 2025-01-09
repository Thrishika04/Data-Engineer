# Banking_Project_Flow

The goal of this project was to build a centralized platform to process and analyze large volumes of transactional data for a leading bank. Here's how the workflow was structured:

**1. Data Ingestion (Bronze Layer)**

**Objective:** The first step was to ingest raw transactional data from the bank's SQL Server and Oracle databases into Azure Data Lake Storage Gen2 (ADLS Gen2).

**Process:**
We used Azure Data Factory (ADF) to create ETL pipelines that extracted data from SQL Server and Oracle database.
The raw data was stored in the Bronze layer in its original form to preserve the audit trail and ensure traceability.
This included both structured data (like transaction details) and semi-structured data (like logs).

**My Role:**
I developed and optimized ETL pipelines in ADF to ensure smooth data ingestion and validated the completeness of the ingested data.
I also handled scenarios like schema changes dynamically within ADF.

**2. Data Transformation (Silver Layer)**

**Objective:** To clean and process the raw data to create structured, analytics-ready datasets.

**Process:** The raw data from the Bronze layer was processed in Azure Databricks using PySpark.

**Tasks included:**

* Cleaning the data (removing duplicates, handling missing values).
* Standardizing formats like dates and currencies.
* Applying business logic, such as grouping transactions by customer for segmentation.
  
This processed data was stored in the Silver layer, where it was refined and ready for analytics.
For Example Use Cases:

* **Fraud Detection:** Highlighting patterns like high-frequency or high-value transactions within a short time.
* **Customer Segmentation:** Classifying customers into high-value and low-value categories based on transaction behavior.
My Role here was
I wrote and optimized PySpark scripts to perform these transformations.
I also conducted validation checks to ensure data accuracy and maintained compliance with regulatory standards.

**3. Data Analytics and Insights (Gold Layer)**

**Objective:** To derive business insights and create reports for stakeholders.

**Process:** Data from the Silver layer was aggregated and stored in the Gold layer, which was optimized for analytics.

**4. Monitoring and Automation**

**Objective:** To ensure reliable and efficient pipeline operations.

**Process:**
Automated pipeline monitoring using Azure Monitor.
Configured alerts to detect failures or performance issues, ensuring minimal downtime.
Regularly analyzed logs to identify bottlenecks and improve system efficiency.
**My Role:**
I set up alert mechanisms to notify the team in case of job failures.
I also analyzed logs to proactively resolve recurring issues.

Apart from these I also invoved in Agile ceremonies such as daily standups, sprint planning, and retrospectives.
Supported sprint-end activities, including deployments and stability checks for production pipelines.

