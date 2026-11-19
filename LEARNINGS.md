# Learning Outcomes

This practical provided experience deploying a multi-tier web application on AWS.

## Skills practiced

- Designing a VPC with public and private subnets.
- Configuring an Internet Gateway and route table.
- Launching and connecting to an Ubuntu EC2 instance.
- Installing and configuring Apache2 and PHP.
- Transferring and deploying application files using ZIP and SCP.
- Connecting a PHP application to Amazon RDS for MySQL.
- Creating database tables for student registration records.
- Storing uploaded documents in Amazon S3.
- Granting EC2-to-S3 access through an IAM role and policy.
- Configuring a domain with DuckDNS and testing HTTPS.
- Validating application behavior through registration, database queries, uploads, and file retrieval.
- Reviewing EC2, EBS, RDS, and CloudWatch monitoring information.

## Key concepts learned

### Network separation
The web server was placed in a public subnet while the RDS database was placed in private subnets. This separates the public-facing application tier from the database tier.

### IAM roles instead of embedded credentials
The EC2 instance used an attached IAM role to obtain temporary AWS credentials for S3 access. This avoids storing long-lived access keys in application code.

### Database and object storage integration
Student information was stored in RDS, while uploaded files were stored in S3. The database record kept the S3 object key and original filename so the application could associate each registration with its document.

### End-to-end testing
The project was tested from the browser through the application, database, and S3 storage, including uploading and retrieving documents.

## Challenges and troubleshooting

Use the full technical report as the source for the exact deployment steps, command output, screenshots, and troubleshooting details. Add any additional personal notes here as you recall them.

## Possible next improvements

- Enable S3 versioning and encryption.
- Enable RDS Multi-AZ and automated backups.
- Configure CloudWatch alarms.
- Enable EBS encryption.
- Use a stable public endpoint for DNS.
