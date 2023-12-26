# Data Engineering Project: Stock Data Pipeline

## Infrastructure:
- **AWS EC2:** EC2 is used to create a Virtual Machine and we connect our local computer to VM by using SSH method
- **RDS (Database):** MSQL is hosted on AWS RDS as a operational database
- **PostgreSQL:** Postgres is used as a Data Warehouse
- **AWS S3:** Amazon Simple Storage Service (S3) is used as a Data Lake
- **Git (Teamwork):** Git is used for collaboration between teammates 

![image](https://github.com/DangMinhHao/glorious-data-pipeline/assets/108931204/6ffd43c6-06e7-41fb-9b55-d28e2e9614ae)

## Scenario
In this project, we are simulating a real stock platform database by using Faker library to generate stock data into MySQL. ETL pipeline is implemented to snapshot daily data and load into Data Lake, then applying Full loading and Incremental loading patterns to capture latest records and finally load into Data Warehouse.

We simulated 2 real life scenarios in this project:
1. Best Scenario: Operational database has updated_at column or created_at column. Those columns help the capture-latest-record process easily
2. Common Scenario: Operational database lacked updated_at column or created_at column. In this situation, we need compare snapshot data of d-1 to snapshot data of d-2 to determined the latest updated or inserted records.

We designed Fact table of Data Warehouse as Transactional Fact table and implemented Slowly Changing dimension type 2 to update records of dimension table.

Finally, cron is used to set job for this pipeline. We decided to used Cron instead of using other Orchestration tool like Airflow because of the simplicty of this pipeline and we did not have lots of ETL pipelines.

![Data Model](https://github.com/hoanguyen071710/glorious-data-pipeline/assets/76463109/f0c68dd3-66ca-40d6-b9d2-22b317a1c8c8)

## Data Warehouse Design

![Data Warehouse Entity Relationship Diagram (ERD)](https://github.com/hoanguyen071710/glorious-data-pipeline/assets/76463109/951c1c1f-fc49-4a05-8171-5b16f8f57a2f)

## Tasks
The project encompasses the following major tasks:
- Generate fake data using the Faker library and insert it into the RDS database.
- Design Data Model for operational database and data warehouse
- Snapshot daily data and load into Data Lake
- Capture latest records and load into Data Warehouse
- Set up cron jobs to schedule and automate data generation and ETL processes.
- Utilize SQLAlchemy and Boto3 for efficient data upload and download between different components.
