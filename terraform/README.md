Here’s a detailed breakdown of the steps we followed to complete the Medusa deployment project using Terraform, AWS ECS/Fargate, and GitHub Actions:

Step 1: Prepare the AWS Environment

1. Create an AWS Account:
   - Sign up for an AWS account if you don't have one.
   - Configure access by creating an IAM user with AdministratorAccess for 
     deployment purposes.

2. Create IAM Credentials:
   - Generate the AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY for the IAM user.
   - These credentials will be used in GitHub Actions to authenticate Terraform when 
     deploying to AWS.
     
Step 2: Create the Terraform Files

1. Set Up main.tf:
   - Write the main.tf file to define all AWS resources needed to run Medusa on ECS/Fargate.
   - Define the following resources:
     - *VPC and Subnets*: For networking, define public and private subnets.
     - *Security Groups*: To allow inbound traffic to the Medusa service (port 9000).
     - *ECS Cluster*: Set up an ECS cluster with Fargate as the launch type.
     - *IAM Role*: Create an IAM role for ECS task execution to pull Docker images 
        and handle logging.
     - *Task Definition*: Define the Medusa container settings (CPU, memory, ports).
     - *ECS Service*: Create an ECS service to run the Medusa container on Fargate.
   
2. Validate the Configuration:
   - Validate the Terraform configuration using terraform validate to ensure everything is correct.

Step 3: Configure GitHub Actions for CI/CD*

1. Create a Workflow File (medusa-deployment.yml):
   - Add a GitHub Actions YAML file under .github/workflows/medusa-deployment.yml.
   - The workflow should:
     - Checkout the repository.
     - Set up Terraform.
     - Use AWS credentials stored in GitHub secrets to authenticate.
     - Run Terraform commands (init, plan, apply) to deploy the infrastructure 
       automatically.

# The .github file is always hidden

2. Add AWS Credentials to GitHub Secrets:
   - Go to the GitHub repository and navigate to Settings > Secrets and variables > Actions.
   - Add AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY as secrets so GitHub Actions can use them for AWS authentication.

Step 4: Initialize and Apply Terraform Locally 

1. Install Terraform:
   - If you want to run Terraform locally, install it on your machine 
   - 
2. Run Terraform Commands:
   - Run the following commands to deploy the infrastructure locally :
     Gitbash
     
     terraform init
     terraform plan
     terraform apply  

   - This will provision the VPC, ECS Cluster, IAM roles, and other resources on AWS.

Step 5: Automate Deployment via GitHub Actions

1. Push to main Branch:
   - Once the GitHub Actions workflow is set up, push your code to the main branch. This will trigger the workflow and begin the automated deployment process.
   
2. GitHub Actions Workflow Execution*:
   - The workflow runs the following steps:
     - *Checkout*: Pulls the latest code from your GitHub repository.
     - *Set up Terraform*: Installs Terraform.
     - *AWS Credentials*: Authenticates to AWS using your stored secrets.
     - *Terraform Commands*: Initializes, plans, and applies the Terraform 
       configuration to deploy the infrastructure.

3. *Verify Successful Deployment*:
   - Check the GitHub Actions logs to ensure the workflow completed successfully without errors.
   - You can also check your AWS account to verify that the ECS cluster, services, and tasks were created and are running.


### Summary of Steps:
1. *AWS Setup*: Create IAM user and configure credentials.
2. *Medusa Setup*: Prepare Medusa Docker image for deployment.
3. *Terraform Configuration*: Write main.tf to define AWS infrastructure (VPC, ECS, IAM, etc.).
4. *GitHub Actions Setup*: Create a CI/CD workflow to automate deployment using Terraform.
5. *AWS Secrets in GitHub*: Add AWS credentials to GitHub secrets.
6. *Deploy via GitHub Actions*: Push to main to trigger deployment via GitHub Actions.
7. *Access Medusa*: Retrieve the public IP and verify the app is running.
8. *Maintain and Scale*: Update infrastructure via Terraform and GitHub Actions as needed.

#The detailings to the step 2,7,8 are not given as we have not worked on that.
---

These steps outline the process we followed to deploy the Medusa platform on AWS ECS/Fargate using Terraform and GitHub Actions. This automated workflow ensures that each change to the codebase is automatically reflected in the infrastructure without manual intervention
