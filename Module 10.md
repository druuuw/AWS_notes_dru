# Module 10: Automatic Scaling and Monitoring

### Section 1: Elastic Load Balancing

- Distributes incoming application or network traffic across multiple targets in single or across multiple availability zones
- scales your load balancer as traffic to your app changes over time

### Types of load balancers

![Untitled](Images/Module%2010%20Automatic%20Scaling%20and%20Monitoring%20ea2bd449370f462eaf8de3391919d37a/Untitled.png)

- Application Load Balancer
- Network Load Balancer
- Classic Load Balancer

### How Elastic Load Balancing works

![Untitled](Images/Module%2010%20Automatic%20Scaling%20and%20Monitoring%20ea2bd449370f462eaf8de3391919d37a/Untitled%201.png)

— load balancer accepts incoming traffic from clients and routes requests to registered targets (i.e. EC2) in 1 or more AZs

— configure ELB to accept incoming traffic by specifying one or more listeners. A listener is a process that checks for connection requests. configured with protocol and port no. for connections from clients to load balancer. Similarly, it is configured with a protocol and port no. for connections from ELB to targets

— configure ELB to perform health checks, which are used to monitor health of registered targets so that ELB only sends requests to healthy instances. When ELB detects unhealthy target, stops routing traffic. It then resumes routing traffic to that target when it detects that target is healthy again

— key diff in how ELB types are configured. with Application and Network Load Balancer, you register targets in target groups, and route traffic to targt groups. With Classic, you register instances with the load balancer

### Elastic Load Balancing use cases

- Highly available and fault-tolerant applications
    - ELB balances traffic across healthy targets in multiple AZs.
- Containerized applications
    - with enhanced container support for ELB, can load balance across multiple ports on the same EC2 instance.
    - also can take advantage of deep integration with Amazon Elastic Container Service (Amazon ECS), which provides fully managed container offering.
    - register service with load balancer and ECS will manage the docker containers
- Elasticity and scalability
    - works with CloudWatch and EC2 Auto Scaling to help scale app to demands. CloudWatch alarms trigger auto scaling for ec2
    - load balancer will then register the ec2 instance and direct traffic as needed
- VPC
    - Use ELB to create public entry point into VPC, or to route request traffic btwn tiers.
- Hybrid environments
    - ELB enables you to load balance acrossAWS and on-premises resources by using same load balancer
    - i.e. register all resources on premises and on AWS to same target group
- Invoke Lambda functions over HTTP(S)
    - enables users to access serverless apps from any HTTP client, including web browsers.
    - can register Lambda functions as targets and use the support for content-based routing rules in Application Load Balancer to route requests to different Lambda functions.
    - use application load balancer as common HTTP endpoint for apps that use servers and serverless computing
    - can build entire website by using Lambda functions, or combine EC2 instances, containers, on-premises servers, and Lambda functions to build apps.

### Load balancer monitoring

- Amazon CloudWatch metrics
    - used to verify system is performing as expected ad creates an alarm to initiate an action if metric goes outside an acceptable range
- Access logs
    - capture detailed info abt requests send to load balancer
    - store them in Amazon S3
- AWS CloudTrail
    - capture who, what, when and where of API interactions in AWS services
    - store detail info about calls made to ELB API and store log in S3

## Section 2: Amazon CloudWatch

### Monitoring AWS resources

![Untitled](Images/Module%2010%20Automatic%20Scaling%20and%20Monitoring%20ea2bd449370f462eaf8de3391919d37a/Untitled%202.png)

### Amazon CloudWatch

- Monitors —
    - AWS resources
    - apps that run on aws
- Collect and tracks —
    - standard metrics
    - custom metrics
- alarms —
    - sends notifs to an amazon Simple Notification Service (SNS)
    - perform EC2 auto scaling or ec2 actions
- events —
    - define rules to match changes in aws environment and route these events to one or more target functions or streams for processing
- pay for what you use, charged at the end of the month

### CloudWatch alarms

- Create alarms based on —
    - static threshold
    - anomaly detection
    - metric math expression
- Specify — (specify when based on static threshold)
    - Namespace
    - Metric
    - Statistic
    - Period
    - Conditions
    - Additional Config
    - Actions

## Section 3: Amazon EC2 Auto Scaling

### Why is scaling impt

- scaling is ability to inc/dec compute capacity of app
- varying resource requirements with one day alot more than the rest. so need to scale

### EC2 Auto Scaling

- help maintain app availability
- enable to auto add or remove ec2 instances according to conditions we define
- detects impaired ec2 instances and unhealthy apps, and replaced instances w/o our intervention
- provide several scaling options — manual, scheduled, dynamic or on-demand, and predictive
- best meet needs of your app

### Auto Scaling groups

- a collection of ec2 instances that are treated as logical grouping for purposes of auto scaling and management
- size of group depend on no set as DESIRED CAPACITY. you can adjust its size to meet demand, either manually or auto scaled

### Scaling out vs Scaling In

- Base Config
- Scaling out (launch instance)
- Scale in (terminate instance)

### How EC2 auto scaling works

- Uses a laugh config, which is an instance config template. think of it as what you are scaling.
- need specify AMI, instance type, IAM roles, Security grp, EBS volumes
- define min n max number instance and desired
- launch into subnet within VPC of auto scaling grp
- attach load balancer
- finally specify wen scaling event occurs

### Implementing dynamic scaling

a common config for implementing dynamic scaling is create CloudWatch alarm that is based on performance info from your EC2 instances or load balancer. When a performance threshold is breached, CloudWatch alarm triggers auto scale event that either scale out or in ec2 instance

i.e. Cloudwatch alarm monitor CPU util and run auto scale policies if avg CPU util across fleet >60 for 5mins

### AWS Auto Scaling

- Monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost
- Provides simple, powerful user interface that enables you to build scaling plans for resources including —
    - EC2 instances and Spot Fleets
    - Elastic Container Service (ECS)
    - Amazon DynamoDB tables
    - Aurora Replicas
- So far, we learned about scaling EC2 instances with EC2 Auto Scaling. You also learned that you can use EC2 Auto Scaling w AWS Auto Scaling to perform predictive scaling
- AWS Auto Scaling is a separate service that monitors your applications. It automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost. The service provides a simple, powerful user interface that enables you build scaling plans for resources, including:
    - EC2 instances and Spot Fleets
    - Elastic Container Service (Amazon ECS) tasks
    - Amazon DynamoDB tables and indexes
    - Aurora Replicas
- If you are already using EC2 auto scaling to dynamically scale your ec2 instances, you can now use it with AWS Auto Scaling to scale additional resources for other AWS services.