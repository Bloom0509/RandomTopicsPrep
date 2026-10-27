## EC2 
 - Virtual server 
 - Example :- Django app on EC2
## S3
 - Object Storage , Example :- images, pdfs, resume uploads
 - Architecture :- React -> API -> S3
## RDS
 - Managed databases Example :- postgreSQL , MySQL
 - Architecture :- Django-> RDS PostgreSQL
## Lambda
 - Serverless function
 - Example :- Image upload -> Lamdba triggered -> Thumbnail generated
## API gateway
 - Expose APIs
 - Example :- Client->API Gateway ->Lambda
## Cloud Front
 - CDN caches files globally
## VPC
 - Private network inside AWS
## IAM
 - Users/Roles/Permission, never hardcode AWS keys, use IAM roles
## SQS
 - Message Queues used for async processing , User uploads image->SQS -> Worker processes image
## Auto Scaling
 - Automatically adds EC2 instance during traffic spikes
## AWS Architecture
 - React -> CloudFront -> ALB -> EC2
 - Images -> S3 <- RDS postgreSQL <- Django
 - Email-> SQS-> Worker

| Title | Description |
| ----------- | ----------- |
| EC2 | for compute |
| S3 | for storage | 
| RDS | for database | 
| IAM | for security | 

