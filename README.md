# Data Engineering Project Using DBT

This project is for anyone who wants to get started with **DBT (Data Build Tool)**.  I built it to learn the basics of DBT and how it works with Snowflake.

### What is DBT?  
DBT is a tool that helps you write SQL queries and organize your data transformations.  
But DBT doesn’t have its own storage—it needs a data warehouse like Snowflake to run queries.

### Goal  
The goal of this project is to learn how DBT works and practice its main features like connections, seeds, and configurations.

Tools I Used  - DBT Cloud (Trial version), Snowflake (Trial version) 

## lets start 
I have created a database and schema to store the raw data.  

```sql
CREATE DATABASE travel_db;  
CREATE SCHEMA raw;
``` 
I have added two tables to the raw schema:  

- `booking_details`  
- `customer_details`  

You can find the SQL scripts for these tables here:  
- [`Snowflake_code/customer_details.sql`](./Snowflake_code/customer_details.sql)  
- [`Snowflake_code/booking_details.sql`](./Snowflake_code/booking_details.sql)  

In DBT Cloud, I connected to Snowflake by adding:  Account ID, Database , Warehouse

### DBT Concepts File  
I created a file called `dbt_concepts` to document all the DBT concepts I’m learning while building this project.  

### `profiles.yml` -

`profiles.yml` file configures the connection between DBT and Snowflake. It defines how DBT should authenticate and connect to our Snowflake data warehouse.
When we run DBT commands, such as dbt run or dbt test, the profiles.yml file tells DBT how to connect to our Snowflake database using the specified configuration. By setting up the target as dev, DBT uses the connection details under the dev output.
This setup is flexible and allows us to add other environments like prod for production-level settings if needed.
- [`profiles.yml`](dbt/profiles.yml)


### `dbt_project.yml` -
The dbt_project.yml file is the configuration file that tells DBT how to run your project. It contains essential details about the project, including its name, version, profiles, model configuration, and more.
- [`dbt_project.yml`](dbt/dbt_project.yml)

### Seeds - 
In DBT, seeds are CSV files that we can load as tables into our database.  
I have used **4 seed files** in this project to load static data. 
- [`seeds`](dbt/seeds)

### `sources.yml` -
The sources.yml file is a configuration file to define metadata for the source data that we will use in our models. 
- [`sources.yml`](dbt/model/sources.yml)
This sources.yml file defines the metadata for two source tables in the TRAVEL_DB Snowflake database: booking_details and customer_details. It specifies the schema (raw) and provides descriptions for each table and its columns.
I have use **Freshness** parameter to ensure that the data being ingested or transformed is current and valid. 
warn_after: This parameter specifies how long after the data was last updated before a warning is triggered (e.g., if the data is older than 1 hour).
error_after: This parameter specifies the threshold at which an error should occur if the data has not been updated for the specified period (e.g., if the data is older than 24 hours).
both the booking_details and customer_details tables have freshness checks that trigger:
- A warning if the data is older than 1 hour.
- An error if the data is older than 24 hours.






