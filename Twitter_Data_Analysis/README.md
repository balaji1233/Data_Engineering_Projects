# twitter-airflow-data-engineering-project

## Problem Statement

Many organizations struggle with:
- **Unreliable ingestion**: Cron-based scripts fail under API limits or machine restarts.
- **Lack of orchestration**: No visibility into task dependencies, retries, or failures.
- **Scalability issues**: Local deployments can’t handle high tweet volumes or parallel pipelines.

**ETL-Flow** solves these by providing:
- Modular tasks in an Airflow DAG
- Built-in retries, logging, and alerts
- AWS-backed infrastructure for nearly unlimited scale

---

## Key Features

1. **Modular DAGs**  
   - Separate tasks for extract, transform, and load  
   - Clear dependency graph and retry policies  

2. **Twitter API Extraction**  
   - Uses `tweepy` to fetch tweets, metadata, and engagement stats  
   - Configurable polling intervals and rate-limit backoff  

3. **Data Transformation**  
   - Cleans and normalizes text with `pandas`  
   - Extracts hashtags, timestamps, user info, and computes sentiment  
   - Outputs Parquet files for efficient columnar storage  

4. **S3 Data Lake Loading**  
   - Writes daily-partitioned Parquet to `s3://<your-bucket>/twitter/YYYY/MM/DD/`  
   - Lifecycle policies can archive or expire old data  

5. **Cloud Deployment**  
   - CloudFormation template to provision an EC2 instance with Airflow  
   - IAM roles, security groups, and S3 permissions configured automatically  

6. **Resilience & Monitoring**  
   - Task retries, SLA alerts, and email notifications  
   - Logs shipped to CloudWatch for centralized debugging  

---



### Prerequisites

- Python 3.7+  
- AWS account with EC2 & S3 permissions  
- Twitter Developer API key & secret  

### Usage
Airflow UI: Visit http://<EC2_PUBLIC_IP>:8080.

DAG: Trigger twitter_etl manually or let it run daily.

Monitoring: Check task logs in the UI or CloudWatch.







   
