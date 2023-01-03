## Terraform Lambda Module


### 1. Description
Creates Lambda functions.
Some extras include:
- Creates an environment to install all the python requirements
- Installs all the requirements in the virtual environment
- Packages the virtual environment and submits it with the Lambda function.
- Cron trigger through Cloudwatch Events
- S3 trigger

### 2. Parameters - AWS Lambda

| Name                | Variable                     | Type         | Required | Default           |
|---------------------|------------------------------|--------------|----------|-------------------|
| Lambda              | **env**                      | string       | Yes      |                   |
|                     | **lambda_name**              | string       | Yes      |                   |
|                     | **lambda_path**              | string       | Yes      |                   |
|                     | **lambda_runtime**           | string       | Yes      | python3.9         | 
|                     | **root_path**                | string       | Yes      |                   |
|                     | **memory_size**              | string       | Yes      |                   |
|                     | **timeout**                  | number       | Yes      |                   |
|                     | **log_retention_days         | number       | Yes      |                   |
|                     | **env_vars**                 | map(string)  | Yes      |                   |
|                     | **iam_role_name**            | string       | Yes      ||
|                     | **iam_logging_policy_name**  | string       | Yes      |                   |
|                     | **tags**                     | map(string)  | Yes      || 
| SNS Policy          | **sns_alert_enabled**        | string       | No       | ""                |
|                     | **iam_alerting_policy_name** | string       | No       | ""                |
|                     | **sns_topic_name**           | string       | No       | ""                |
| S3 Policy           | **s3_policy_enabled**        | number       | No       | 0                 |
|                     | **bucket_id**                | string       | No       | ""                |
|                     | **iam_s3_policy_name**       | string       | No       | "remove-me"       |
|                     | **iam_s3_actions**           | list(string) | No       | ["s3:ListBucket"] |


### 3. Parameters - AWS Lambda - Cron Trigger

| Variable                 | Type              | Required | Default |
|--------------------------|-------------------|----------|---------|
| **env**                  | string            | Yes      |         |
| **lambda_name**          | string            | Yes      |         |
| **lambda_arn**           | string            | Yes      |         |
| **lambda_cron_schedule** | string            | Yes      |         |
| **lambda_cron_count**    | number            | Yes      |         |
| **lambda_cron_input**    | list(map(string)) | Yes      |         |
| **tags**                 | map(string)       | Yes      |         | 


### 4. Parameters - AWS Lambda - S3 Trigger
| Variable          | Type     | Required | Default |
|-------------------|----------|----------|---------|
| **env**           | string   | Yes      |         |
| **lambda_name**   | string   | Yes      |         |
| **lambda_arn**    | string   | Yes      |         |
| **bucket_name**   | string   | Yes      |         |
| **bucket_id**     | string   | Yes      |         |
| **filter_prefix** | string   | Yes      |         |
| **filter_suffix** | string   | Yes      |         | 
