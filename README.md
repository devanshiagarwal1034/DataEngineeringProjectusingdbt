# DataEngineeringProjectusingdbt
dbt project
I have build this project to get the idea of core concepts of  dbt .

In this project I have use trial version of dbt cloud and Snowflake. dbt don’t have its own memory, it needs to use some Datawarehouse to able to execute the queries.

I have created the database and schema named as raw in Snowflake

--sql code --
create database travel_db ;
create Schema raw;


 I have added the two tables -booking_details and customer_details in raw schema , in below path you can see its create
 and insert statement -

 Snowflake_code/customer_details.sql
 Snowflake_code/booking_details.sql


then , I have created the connection with Snowflake ,I have added account_id  , database and warehouse to make the connection.
I have first started with creating the profile.yml file and add the configuration related to Snowflake , then I have created the dbt_project.yml 


creating the seeds  ,I have created the below file , I created the dbt_concepts file to jott down all the concepts
I have use in this project , you can refer here dbt_concepts

I have use 4 seeds in this project.





