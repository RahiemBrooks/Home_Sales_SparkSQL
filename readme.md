# Home Sales Project

This project involved analyzing and querying home sales data using Big Data and SparkSQL. The data analysis conducted encompassed the following processes:

1. Importing packages: The project began by importing necessary packages, including findspark to initialize Spark and pyspark.sql for working with SparkSQL.

2. Creating a SparkSession: A SparkSession was created using `SparkSession.builder.appName("SparkSQL").getOrCreate()` to establish a connection to Spark.

3. Reading data: The home sales data was read from an AWS S3 bucket into a DataFrame using the provided URL.

4. Creating a temporary view: A temporary view named "home_sales" was created for the DataFrame using the `createOrReplaceTempView()` method. This enabled running SQL queries on the DataFrame.

5. Querying the data: Several SQL queries were executed to analyze the home sales data. This included calculating the average price for a four-bedroom house sold in each year and the average price of homes based on different criteria such as bedrooms, bathrooms, and square footage.

6. Caching the data: The temporary table "home_sales_revised_df" was cached using `spark.catalog.cacheTable()` method to improve query performance by storing the data in memory.

7. Query runtime comparison: The runtime of a specific query was compared between the cached version and the version using Parquet data. The start time was recorded using `time.time()` before executing each query, and the difference in time was calculated to measure the runtime.

8. Writing Parquet data: The formatted home sales data was written to Parquet format with partitioning based on the "date_built" field using the `partitionBy().parquet()` method.

9. Reading Parquet data: The Parquet data was read into a DataFrame to perform further analysis.

10. Creating a temporary table for Parquet data: A temporary table named "parquet_table" was created for the Parquet DataFrame using the `createOrReplaceTempView()` method.

11. Querying Parquet data: SQL queries were executed on the Parquet DataFrame to filter out view ratings with an average price greater than or equal to $350,000. The runtime was measured and compared to the cached version.

12. Uncaching the temporary table: The temporary table "home_sales" was uncached using `spark.catalog.uncacheTable()` method to release memory resources.

13. Checking caching status: The caching status of the table "home_sales" was checked using `spark.catalog.isCached()` method to confirm whether it was still cached or not.

Overall, this project demonstrated the usage of SparkSQL to read, query, cache, and analyze home sales data, providing insights into average prices based on various criteria.