# AWS Cloud CI/CD Automation

A hands-on Cloud and DevOps project using AWS, Jenkins, Docker, Terraform, and Python Flask.

## Technologies

* AWS
* Jenkins CI/CD
* Docker
* Terraform
* Python and Flask
* pytest
* Git and GitHub

## Application Endpoints

* `/` — Application status
* `/health` — Health check
* `/info` — Application information

## CI/CD Pipeline

1. Install dependencies.
2. Run automated tests.
3. Build the Docker image.
4. Push the image to Amazon ECR.

## AWS Infrastructure

Terraform configuration for AWS networking, EC2, IAM, Amazon ECR, Application Load Balancer, and CloudWatch monitoring.

## Run Locally

Activate the virtual environment and install dependencies:

`source .venv/bin/activate`

`pip install -r requirements.txt`

Run tests:

`pytest -v`

Build the Docker image:

`docker build -t cloud-cicd-app .`

## Security

* Never commit AWS credentials or secrets.
* Store credentials securely in Jenkins.
* Check AWS resources regularly to avoid unneces
