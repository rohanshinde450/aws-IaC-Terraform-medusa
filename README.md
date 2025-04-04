# aws-IaC-Terraform-medusa
This is the designed IaC (Terraform, Aws ECS/Fargate) for Medusa open source headless commerce platform backend (https://docs.medusajs.com/deployments/server/general-guide), CD pipeline using GitHub Actions

## Prerequisites for Setting Up Medusa Deployment Using Terraform and GitHub Actions on AWS ECS/Fargate:
Before you start deploying the Medusa platform using Terraform, AWS ECS/Fargate, and GitHub Actions, you’ll need to make sure you have the following prerequisites in place.

## Prerequisites:

   1. AWS Account and Access i. AWS Account: You need an active AWS account to deploy infrastructure. ii. IAM User: Create an IAM user with programmatic access (Access key ID and Secret 
      access key) iii. AWS CLI Setup: Install a AWS CLI setup locally on your terminal that you are using (Eg:Gitbash) in which
      I did this entire project. Configure your AWS using the command below and type in your aws credentials $aws configure

   2. GitHub Repository
      i. GitHub Repo: Ensure your project is hosted on GitHub. ii. GitHub Secrets: Add AWS credentials (AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY) to the GitHub repository secrets. -Go to 
      Settings > Secrets and variables > Actions > New repository secret. - Add the keys AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY with their respective values.

   3. Terraform Basics i. Install Terraform: Ensure Terraform is installed on your local machine. You will use it to define your infrastructure as code (IaC).

   4. GitHub Actions Basics GitHub Actions: Understand how GitHub Actions workflows are triggered, and how to write a YAML file for automated deployment.
