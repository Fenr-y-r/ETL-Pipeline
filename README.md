# ETL Pipeline project

Overview: Airflow Extract-Transform-Load pipeline with Postgres and API integration

This project involves creating an ETL pipeline using apache airflow, extracting data from an external API, transforming the data and then loading it into the Postgres database, the entire workflow is orchestrated by Airflow

Postgres and Airflow are hosted as services through Docker for an isolated and reproducible enviroment and Airflow hook and operators are utilized to handle the pipeline efficiently

#### Extract: The SimpleHttpOperator is used to make HTTP GET requests to NASA's APOD API and the response is in Json format 

#### Transform: The expected JSON data is processed in the transofrm task using Airflow TaskFlow API which invovles extracting the relevant fields and ensuring the correct format

#### Load: The loaded data is then loaded into a Postgres table using PostgresHook and if the table doesn't exist then it is automatically created 

I had originally planned to run this project completely in the cloud but since astronomer just refuse to work properly, i gave up on that so the astronomer container runs locally but sends the DAG output to an Azure PostgreSQL database