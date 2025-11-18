# Team_Darwin
This is the repository for HCL_Hackathon. Here we are doing Task-2: which is "Retail Data processing Hackathon Use Cases.".

**#Team Members**: 4 Students
**#Hackathon**: HCL – Retail Data Processing Hackathon

**📌 Project Overview**
We engineered a robust preprocessing pipeline designed to transform raw, unstructured flat-file data (retail_data_Source.csv) into a normalized *Star Schema* optimized for analytics. The process focuses on data integrity, type safety, and relational mapping.

### Key Preprocessing Steps
* *Ingestion Strategy:* Implemented a "read-as-string" strategy to prevent initial type inference errors, ensuring data like phone numbers and IDs preserved leading zeros.
* *Data Sanitization:*
    * *Whitespace Removal:* Automated trimming of column names and string values to prevent key-mismatch errors.
    * *Date Parsing:* Developed a custom, fault-tolerant date parser to handle mixed formats (e.g., YYYY-MM-DD vs DD-MM-YYYY).
* *Validation & Filtering:*
    * Segregated records into *Clean* (valid keys) and *Invalid* (missing Transaction_ID or Customer_ID) datasets to maintain referential integrity.
* *Schema Normalization:*
    * Decomposed the flat CSV into relational entities: customers, products, stores, promotions, and sales.
    * *Deduplication:* Enforced unique constraints on dimension tables to ensure 3NF (Third Normal Form) compliance.
    * *Type Casting:* Converted cleaned strings into appropriate SQL types (Int64, Float, DateTime).

### ⚠ Current Status & Known Issues
*Data Persistence / Database Export*
While the Python-based transformation logic is fully functional and successfully generates the required DataFrames in memory, **we encountered issues during the final export phase (to_sql) to the custom database tables.**

Currently, the processed data resides in the ETL staging environment but has not been successfully committed to the final SQL production tables due to connection/schema validation constraints..
