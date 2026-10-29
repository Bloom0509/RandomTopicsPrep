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
## VPC (virtual Private Cloud)
 - Private network inside AWS
 - Provides network isolation within AWS allowing resources to be deployed securely using public and private subnets
## IAM
 - Users/Roles/Permission, never hardcode AWS keys, use IAM roles
## SQS
 - Message Queues used for async processing , User uploads image->SQS -> Worker processes image
 - decouples services used for asynchronous communication between systems
## Cloud watch
 - Aws monitoring and observability service used for collecting metrics ,logs ,alarms and dashboard
## Auto Scaling
 - Automatically adds EC2 instance during traffic spikes
## Public Subnet
 - Accessible from internet frontend or load balancer
## Private Subnet
 - Not internet accessible , example : db, redis and kafka
 - Flow: Internet-> Load Balancer -> public subnet -> EC2 App servers -> Private subnet -> RDBMS
## Suppose Deployment React+Django+postgreSQL
 - Flow: Users -> CloudFront -> S3(react build) ->ALB -> EC2(Django) -> RDS database -> Redis
## Application in down , How do you debug?
 - Identity scope: Ask all users or some affected?
 - Check Cloud Watch: CPU spike, Memory spike etc
 - Check Application logs: DB errors
 - Check EC2 health: CPU usage
 - Check DB: deadlock
 - Check Network: load balancer,DNS
 - Recent Deployment: Rollback if needed
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

