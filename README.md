### Project Background

* Sparkify provides music streaming to end users. Data of song details and user activities is captured as JSON files.

* AWS Redshift is selected as the data warehousing platform, enabling persistent data storage and ad hoc queries. 

* Apache Airflow is designated as the data pipeline solution, supporting automation and monitoring of the ETL process. 


### Redshift Setup
 
* Create Redshift IAM role with S3FullAccess. 

* Create Redshift cluster.

* Attach Redshift IAM role to the cluster. 

* create empty staging tables, dimension tables, and fact table as groundwork. 


### Airflow Setup

* Start Airflow with `/opt/airflow/start.sh` in command line

* Create connection to S3

* Create connection to Redshift


### Data Sources
* Log data: `s3://udacity-dend/log_data`

* Song data: `s3://udacity-dend/song_data`


### Final Tables
* Songplay Fact Table 

* Users Dimension Table

* Songs Dimension Table

* Artists Dimension Table

* Time Dimension Table


### Data Pipelines
![DAG Flow](dag-flow.png)


### ETL Scripts

* `create_tables.sql` : DDLs for 2 staging tables, 4 dimension tables, and 1 fact table for the project

* `udac_example_dag.py` : DAG file for Apache Airflow

* `stage_redshift.py` : custom operator to load data from S3 to Redshift

* `load_fact.py` : custom operator to populate fact table in Redshift

* `load_dimension.py` : custom operator to load dimension tables in Redshift

* `data_quality.py` : custom operator to check data quality in all tables. e.g. at least one record in the table

