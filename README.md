# Library Management System - Data Pipeline

This project implements a data pipeline for a Library Management System using SQL Server. The pipeline consists of Bronze, Silver, and Gold layers, where data flows from raw ingestion to transformation, cleaning, and aggregation for final analysis.

# Project Structure

# 1. Bronze Layer (Data Ingestion)

Raw data is ingested from CSV files into the Bronze layer using BULK INSERT statements.

Tables: books, branch, employees, issued_status, members, return_status.

This layer stores data as-is, with no transformations or cleaning.

# 2. Silver Layer (Data Transformation)

Data from the Bronze layer is cleaned and transformed.

Transformations include:

Removing extraneous quotes.

Casting data types (e.g., converting rental_price to FLOAT).

Removing unnecessary spaces.

Establishing foreign key relationships between tables.

Procedure: silver_loaddata.

# 3. Gold Layer (Data Aggregation)

The Gold layer aggregates the transformed data into a master view (dim_masterdata).

Joins data from the Silver layer (books, issued status, return status, members, employees, and branch).

This view provides comprehensive insights for analysis and reporting.

# Stored Procedures & Views

bronze_loaddata: Loads raw data into the Bronze layer.

silver_loaddata: Cleans and transforms data in the Silver layer.

gold.dim_masterdata: A view that aggregates data from Silver for analysis.

# Setup Instructions

Clone this repository:

git clone https://github.com/AdityaK1197/Library-Management-System.git

Open SQL Server Management Studio (SSMS) and connect to your database.

Run the scripts for creating the database and tables:

Create database and schemas.

Run bronze_loaddata procedure to load raw data.

Run silver_loaddata procedure to clean and transform data.

Create the dim_masterdata view for aggregated data.

Execute the stored procedures:

EXEC bronze_loaddata;
EXEC silver_loaddata;
SELECT * FROM gold.dim_masterdata;

# Technologies Used

SQL Server

T-SQL

BULK INSERT

Stored Procedures

Views
