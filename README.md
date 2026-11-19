# Student Registration Portal on AWS

A cloud-hosted student registration application deployed on **Amazon Web Services (AWS)**. The application accepts student details and an uploaded document, stores the registration data in **Amazon RDS for MySQL**, and stores uploaded files in a private **Amazon S3** bucket.

> **Project documentation:** The accompanying technical report is available in [`documentation/`](documentation/).

## Project overview

This project demonstrates how compute, networking, managed database, object storage, identity and access management, DNS, HTTPS, and monitoring services can work together to host a web application.

## Architecture

1. A user opens the portal through its DuckDNS domain.
2. The domain directs the request to an Ubuntu-based Amazon EC2 web server in a public subnet.
3. Apache2 and PHP serve the Student Registration Portal.
4. The application writes student details to an Amazon RDS for MySQL database located in private subnets.
5. Uploaded documents are stored in a private Amazon S3 bucket.
6. The EC2 instance accesses S3 using an attached IAM role and temporary credentials rather than hard-coded access keys.

## AWS services and technologies

| Service / technology | Role in the project |
|---|---|
| Amazon VPC | Isolated network for the application |
| Public and private subnets | Separate the web tier from the database tier |
| Internet Gateway and route table | Provide internet routing for the public subnet |
| Amazon EC2 | Hosts the web application |
| Ubuntu Linux | EC2 operating system |
| Apache2 and PHP | Web server and application runtime |
| Amazon RDS for MySQL | Stores student registration records |
| Amazon S3 | Stores uploaded documents privately |
| AWS IAM role and policy | Grants the EC2 instance access to S3 |
| DuckDNS | Provides a domain name for the web server |
| HTTPS | Encrypts browser-to-server traffic |
| Amazon CloudWatch | Provides infrastructure monitoring metrics |
| Composer and AWS SDK for PHP | PHP dependency management and AWS integration |

## Implementation summary

- Created a custom VPC with one public subnet and two private subnets.
- Attached an Internet Gateway and configured a public route table.
- Launched an Ubuntu EC2 instance for the web/application tier.
- Installed and configured Apache2 and PHP.
- Transferred the application as a ZIP archive and extracted it on the server.
- Configured an RDS MySQL database in private subnets.
- Created the database and student table.
- Created an S3 bucket for uploaded student documents.
- Configured an IAM policy and EC2 instance role for S3 access.
- Configured DuckDNS and enabled HTTPS for the domain.
- Tested student registration, database writes, S3 uploads, and file retrieval.
- Reviewed EC2, EBS, and RDS monitoring information.

## Validation and demonstrated results

The technical report records these tests:

- The portal loaded through its domain over HTTPS.
- The application reported a successful database connection.
- A student registration was inserted into the MySQL database.
- Uploaded JPG and PDF documents were stored in S3.
- The portal displayed registration records with links to retrieve files.
- File retrieval used temporary download links; the report states these links expire after 10 minutes.
- The EC2 instance assumed its IAM role for AWS access.

See the technical report for screenshots and detailed test evidence.

## Repository contents

```text
aws-student-registration-portal/
├── README.md
├── LEARNINGS.md
├── .gitignore
└── documentation/
    └── Core-Task-3-AWS-Technical-Report.pdf
```

## Security notes

- Do not commit AWS access keys, secret keys, passwords, private SSH keys (`.pem`), database credentials, or DNS update tokens.
- Keep the S3 bucket private and grant only the permissions the application requires.
- Keep the database in private subnets and restrict database access to the application tier.
- Before making this repository public, review the attached PDF and remove or mask account identifiers, public IP addresses, and any other information you do not want publicly visible.
- The report describes the deployed environment at the time of the practical. The live endpoint or cloud resources may no longer be available.

## Further improvements

The report identifies possible future improvements:

- Use an Elastic IP or another stable endpoint for DNS.
- Enable S3 versioning and encryption.
- Enable RDS Multi-AZ and automated backups.
- Configure CloudWatch alarms.
- Enable EBS encryption.

## Project report

Open [`documentation/Core-Task-3-AWS-Technical-Report.pdf`](documentation/Core-Task-3-AWS-Technical-Report.pdf) for the full technical report and screenshot evidence.
