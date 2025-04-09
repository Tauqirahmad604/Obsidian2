
ECS(Elastic Container Service)
   
   1. How Does Fargate Handle Tasks?
   2. How you can do path based routing in ECS?
   3. How to make secure communication between ECS services?
   4. How we can add variables in ECS via secret manager?
   5. What is diff bw vpc CIDR and subnet CIDR?
   6. How does ECS handle container placement within a cluster?
   7. You are running an ECS service with Fargate and you want to run that specific task   run on a specific period how would you set that?
   8. You are tasked with scaling ECS servie up and down automatically? How would you do that?
   9. You need to deploy a service on ECS and ensure zero downtime during deployments? How would you configure this?
   10. What Are VPC Flow Logs?
   11. You are running a service on ECS fargate and your application is facing high network latencty. How would you troubleshot and optimize network performance?
   12. You need to deploy a docker application on ecs but want to minimize cost by sharing instances between multiple tasks. Which launch type you will use and why?

Lamda

1. Lambda no longer supports Node.js 14. Your team has dozens of functions still using it. What strategies would you use to upgrade them with minimal downtime?
2. You have a large Python-based Lambda function (300MB including dependencies). What are your options to deploy it effectively?
3. How would you use AWS Lambda to process millions of messages from an SQS queue without exceeding concurrency limits?
4. How do you securely connect a Lambda function to an RDS instance in a private subnet?
5. What is the impact of Lambda cold starts and how do you mitigate them in a high-throughput system?
6. Explain the role of the execution role (IAM) for a Lambda function. What’s the risk if it’s too permissive?
7. How would you reduce the latency of a Lambda function that makes external API calls?
8. Lambda is stateless by design. How would you handle session state or caching across invocations?
9. Your Lambda needs to process a 2GB file uploaded to S3. How would you design the solution given Lambda’s limitations?
10. What’s the maximum execution timeout for a Lambda function, and how would you handle longer-running workloads?