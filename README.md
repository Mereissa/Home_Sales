# Spark Data Analysis with Home Sales Dataset

This repository contains a script for performing data analysis using Apache Spark on a home sales dataset. The script demonstrates various Spark operations, including reading data, querying with SQL, caching, and working with Parquet files. 

## Prerequisites

- Apache Spark (version 3.4.3)
- Java OpenJDK 11
- Python 3
- Pip (Python package installer)
- Requests (Python library for HTTP requests)
- Findspark (Python library for Spark initialization)

## Setup

1. **Install Java OpenJDK and Spark**:
   - The script automatically installs Java OpenJDK 11 and downloads Spark 3.4.3.
   - Make sure the necessary packages and Spark version are available.

2. **Install Python Packages**:
   - The script uses `findspark` to initialize Spark within Python.
   - It also uses `requests` to download the dataset.
   - Install these packages using pip:
     ```bash
     pip install findspark requests
     ```

## Script Overview

The script performs the following steps:

1. **Download and Extract Spark**:
   - Downloads Spark 3.4.3 and extracts it.
   - Sets up environment variables for Spark and Java.

2. **Create a Spark Session**:
   - Initializes a SparkSession named "SparkSQL".

3. **Load Data**:
   - Downloads a CSV dataset from AWS S3.
   - Loads the data into a Spark DataFrame.

4. **Data Analysis**:
   - Creates temporary views for SQL queries.
   - Performs various SQL queries to analyze home sales data:
     1. Average price for four-bedroom houses per year.
     2. Average price of homes built each year with 3 bedrooms and 3 bathrooms.
     3. Average price of homes built each year with specific criteria (3 bedrooms, 3 bathrooms, 2 floors, and ≥ 2000 sqft).
     4. Average price per view rating with a price ≥ $350,000.

5. **Caching and Performance**:
   - Caches the temporary table and measures query performance before and after caching.
   - Saves the DataFrame as a partitioned Parquet file.
   - Reads the Parquet file and performs the same analysis.

6. **Uncache and Cleanup**:
   - Uncaches the temporary table and verifies it is no longer cached.
   - Stops the SparkSession.