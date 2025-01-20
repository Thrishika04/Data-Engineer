# **Bank Project Flow:**

The goal of this project was to build a centralized platform to process and analyze large volumes of transactional data for a leading bank.

My role involved developing ETL pipelines in Azure Data Factory (ADF) to ingest raw data from SQL Server and Oracle databases into Azure Data Lake Storage Gen2 (Bronze layer). This raw data was stored in its original form to maintain an audit trail and ensure traceability, and I handled scenarios like schema changes dynamically while validating data completeness.

In the Silver layer, I used PySpark in Azure Databricks to transform the raw data into analytics-ready datasets by cleaning it, standardizing formats, and applying business logic for use cases such as fraud detection and customer segmentation. 

The refined and aggregated data was then stored in the Gold layer, optimized for deriving insights and generating reports. These reports were then used by a dedicated Power BI team.

To ensure smooth operations, I automated monitoring using Azure Monitor, setting up alerts for failures and performance issues while analyzing logs to proactively address recurring problems. Additionally, I actively participated in Agile ceremonies, supported sprint-end activities, and ensured stability during production deployments.


### **Source Tables in the project:**
**Customers Table:**
Stores customer-specific information such as names, contact details, and demographic data. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Eg: customer_id, first_name, last_name, email, phone_number

**Accounts Table:**
Contains data on customer accounts, including account types, balances, and status.
	
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Eg: account_id, customer_id, account_type, balance, branch_id


**Transactions Table:**
Records the details of financial transactions, including amounts, types (credit/debit), and dates. 
	
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Eg: transaction_id, account_id, transaction_type, amount, transaction_date 


**Loans Table:**
Includes data on loans provided to customers, such as loan types, amounts, and repayment details. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Eg: loan_id, customer_id, loan_type, loan_amount, interest_rate

**Cards Table:**
Stores data related to customer cards (credit or debit), including card numbers, expiry dates, credit limits, and statuses. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Eg: card_id, customer_id, card_type, card_number, expiry_date

**Branches Table:**
Contains information about bank branches, including branch names, locations, and contact details. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Eg: branch_id, branch_name, city, country, phone_number

**Employees Table:**
Holds data on bank employees, including personal details, job positions, and salary information. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Eg: employee_id, first_name, last_name, position, branch_id


**Audit Table:**
Tracks changes made to the bank's data, including operations like inserts, updates, and deletes.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Eg: audit_id, table_name, operation_type, operation_time, performed_by

## **Azure Data Factory Pipeline with Medallion Architecture**
**1. Data Ingestion (Bronze Layer)**
* Data from source tables (e.g., Customers, Accounts, Transactions) is ingested into the Bronze Layer of Azure Data Lake Storage gen2 (ADLS).
* The data is stored in its raw form without any transformations.
* Tools Used: Azure Data Factory (ADF) for orchestrating data ingestion.

**2. Data Cleaning and Transformation (Silver Layer)**
* The raw data from the Bronze Layer is processed to remove duplicates, handle missing values, standardize formats (e.g., dates, numbers), and mask sensitive data.
* This cleansed and standardized data is stored in the Silver Layer of ADLS.
* Tools Used: Databricks or Mapping Data Flows in ADF for transformations.

**3. Aggregation and Business Logic (Gold Layer)**
* Cleaned data from the Silver Layer is aggregated and enriched based on business requirements, such as calculating KPIs, customer segmentation, or generating reports.
* This enriched data is stored in the Gold Layer, ready for analytics and reporting.
* Tools Used: Databricks or other analytics tools.

**4. Data Consumption**
The Gold Layer data is consumed by business intelligence tools like Power BI for dashboards, reporting, and real-time analytics.
End-users can access insights for decision-making.

