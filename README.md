# Bright-task
Infrastructure deployment automation script(s) using Terraform on the AWS platform. This configuration includes:

1. An Application Load Balancer (ALB) with a target group and listener. (loadbalancer.tf)
2. An EC2 instance running the Apache HTTP server on Ubuntu 22.04 (web-server-vm.tf)

### This part is not finished
3. An RDS instance with a MySQL database. (db.tf) 
I was not sure on how show easily database connection from web-server

Next step would be to figure it out, propably implementing mysql client in the webserver (updating vm-configuration.tpl - commented code)

4. An Amazon SQS queue for messaging. (sqs.tf)
5. An IAM role and policy for the EC2 instance to send logs to Amazon CloudWatch and send messages to the SQS queue.



## Prerequisites:

Terraform installed on your machine. Download it from terraform.io and follow the installation instructions for your operating system.

AWS CLI installed and configured. Download it from aws.amazon.com/cli and follow the installation instructions for your operating system.

AWS account with necessary permissions.





## Steps to run the code:

1. Clone the repository
2. Complete AWS CLI configuration
3. Run below commands

Initialize Terraform
In your local repository, run the following command:

terraform init

Validate the configuration
Run the following command to check your configuration for syntax errors:

terraform validate

Review the execution plan
Run the following command to see what changes Terraform will make to your infrastructure:

terraform plan -var-file aws.tfvars

Apply the changes
If you're satisfied with the execution plan, run the following command to apply the changes:

terraform apply -var-file aws.tfvars -auto-approve


4. Verify connection by entering url from output load_balancer_dns

## Portfolio audit recorded — 2026-11-07

[Findings and feature suggestions](docs/REPO-AUDIT-2026-11-07.md) preserve chat items 32,
with source evidence and acceptance criteria. This completed slice records documentation
only; it selects no implementation work and leaves existing tasks and owner blockers
unchanged. Documentation-push CI verification is pending; see the report.


