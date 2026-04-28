# aws-cloud-infra-lab

Automated AWS cloud infrastructure provisioned entirely with Terraform. This project demonstrates core cloud engineering skills including VPC networking, compute, storage, IAM security, and observability — all defined as code and deployable in minutes.

## Architecture

| Layer | Service | Purpose |
|---|---|---|
| Network | VPC, Subnet, IGW, Route Table | Isolated cloud network with internet access |
| Compute | EC2 t3.micro + Apache | Web server running in the public subnet |
| Storage | S3 + Public Access Block | Secure object storage with IAM controls |
| Security | Security Groups | Firewall rules for SSH and HTTP |
| Monitoring | CloudWatch + SNS | CPU alarm with email alerting |
| IaC | Terraform | All infrastructure defined and version controlled as code |

## What This Demonstrates

- **Infrastructure as Code** — Every AWS resource is defined in Terraform. Nothing was clicked together in the console.
- **Cloud Networking** — Custom VPC with subnets, internet gateway, and route tables configured from scratch.
- **Security Mindset** — S3 bucket public access blocked by default, security groups follow least-privilege principles.
- **Observability** — CloudWatch alarm triggers SNS email notification when EC2 CPU exceeds 80%.
- **Clean Git Workflow** — Conventional commits, .gitignore protecting sensitive state files, structured project layout.

## Project Structure

terraform/
├── main.tf        # All AWS resources
├── providers.tf   # AWS + Random provider configuration
├── variables.tf   # Input variables
└── outputs.tf     # Exposes IP, VPC ID, Subnet ID after apply

## How to Deploy

### Prerequisites
- AWS account with IAM user credentials
- Terraform >= 1.0
- AWS CLI configured via `aws configure`

### Steps

```bash
git clone https://github.com/gmarr0/aws-cloud-infra-lab.git
cd aws-cloud-infra-lab/terraform
terraform init
terraform plan
terraform apply
```

After apply completes, Terraform outputs the public IP of the web server. Navigate to `http://<public-ip>` to verify the deployment.

### Teardown

```bash
terraform destroy
```

## Author

Juan Gamarro — [LinkedIn](https://linkedin.com/in/juan-gamarro-50999a224) | [GitHub](https://github.com/gmarr0)