# Module 8

## Section 1: Amazon Relation Database Service (RDS)

### AWS solutions typically falls into 2 categories

- Unmanaged
    - Scaling, fault tolerance, and availability managed by user
    - typically provisioned in discrete portions specified by user
    - more fine-tuned control over how solution handles changes in load, errors, and when resources being unavailable
- Managed
    - Scaling, fault tolerance, and availability typically built into service
    - require less configuration
    - database administrator responsible for everything
    - 

### Challenges of relational databases

When you run your own relational database, you are responsible for several administrative tasks

- Server maintenance and energy footprint
- Software installation and patches
- Database backups and high availability
- Limits on scalability
- Data security
- OS installation and patches

### Amazon RDS

Managed service that sets up and operates relational database in cloud

![Untitled](Module%208%20fbdfb187681f42728d6cf087e52996e2/Untitled.png)

- Provides cost-efficient and resizable capacity, while automating time-consuming administrative tasks to address
- Sets ups, operates, and scales relational dbs without ongoing administration to tackle challenge of running unmanaged, standalone relational db
- With Amazon RDS, primary focus is data and optimizing application

### From on-premises db to RDS

![Untitled](Module%208%20fbdfb187681f42728d6cf087e52996e2/Untitled%201.png)

honestly i dont understand what this means

### Managed services responsibilities

User Manages:

- Application optimization

AWS Manages:

- OS installation and patches
- db software installation and patches
- db backups
- high availability
- scaling
- power and racking and stacking servers
- server maintenance

### RDS database instances

- basic building block of RDS
- isolated db environment that can contain multiple user-created dbs
- can be accessed with same tools and applications with standalone db
- resources determined by db instance class,
- and type of storage dictated by type of disks
- DB engine to run on instance (MySQL etc.)

### RDS in VPC

![Untitled](Module%208%20fbdfb187681f42728d6cf087e52996e2/Untitled%202.png)

### High availability with Multi-AZ deployment

- most powerful feature of RDS is ability to configure db instance for high availability with Multi-AZ deployment.
- auto generates standby copy of db instance in another availability zone within same VPC
- Enhance availability during planned system maintenance
- protect db against db instance failure and AV zone disruption
- If failure, the standby will become main instance
- Applications will reference the database by using the same RDS DNS
endpoint, user no need change code to let services access standby
instance

### Amazon RDS read replicas

- RDS supports creation of read replicas for
    - MySQL,
    - MariaDB,
    - PostgreSQL, and
    - Amazon Aurora
- Features
    - Offers async replication
    - can be promoted to primary if needed
- Functionality
    - use for read-heavy database workloads
    - offload read queries
- How it works
    - Updates made to source db are async copied to read replica instance
    - reduce load on source db instance by routing read queries to read replica
- Use cases
    
    ![Untitled](Module%208%20fbdfb187681f42728d6cf087e52996e2/Untitled%203.png)
    

### When to use RDS

**Use**

- Complex transactions or complex queries
- Medium to high query or write rate up to 30k IOPS (15k reads + 15k writes)
- No more than a single worker node or shard
- High durability

**Don’t use**

- Massive read/write rates (150k writes per second)
- Sharding due to high data size or throughput demands
- Simple GET or PUT requests and queries that NoSQL database can handle
- Or, relational database management system (RDBMS) customization

— For circumstances when you should not use RDS, consider NoSQL db solution (such as DynamoDB)

— OR running relational database engine on EC2 instead of RDS

### RDS Billing

- Clock-hour billing —
    - Resources incur charges when running
- DB characteristics
    - Physical capacity of db
        - Engine
        - Size
        - Memory
- DB purchase type —
    - on-demand instances
        - compute capacity by hour
    - reserved instances
        - low, one-time, upfront payment for db instance that are reserved w 1 year or 3 year term
- No. of DB instances
    - provision multiple DB instances to handle peak loads

### Storage

- Provisioned storage:
    - No charge
        - backup storage of up to 100% of db storage for active db
    - Charge (GB/month)
        - Backup storage for terminated db instances
- Additional storage
    - Charge (GB/month)
        - backup storage in addition to provisioned storage

### Deployment type and data transfer

Requests:

- The number of input and output requests that are made to the database

Deployment type

- Single AZ
- Multiple AZ

Data transfer

- No changer for inbound
- Tiered charges for outbound data transfer

## Section 2: Amazon DynamoDB

### Relational vs non-relational db

![Untitled](Module%208%20fbdfb187681f42728d6cf087e52996e2/Untitled%204.png)

- Relational -
    - works w structured data organized by tables, records, and columns.
    - Uses SQL
    - might have difficulties scaling out horizontally or working w semi structured data, and might also require many joins for normalized data
- Non relational -
    - does not follow relational model
    - designed to overcome limitations of RDBs for handling demands of variable structured data
    - scale our horizontally, and they can work w unstructured and semi structured data.

### What is DynamoDB

Fast and flexible NoSQL db service for any scale

- Features
    - automatically partitions your data
    - and has table storage to meet workload requirements
    - no practical limit on no. of items you can store in a table
    - same table can have diff attributes — flexibility to add attributes as app evolves
    - grow with application’s needs
    - low-latency queries
    - scaling storage
    - ability to provision of read/write throughput (can also be auto scaled)
    - automatically replicate across AWS regions, encryption at rest, and item Time-to-live (TTL)

### DynamoDB core components

Tables, items, and attributes

- A table is a collection of data
- Items are a group of attributes uniquely identifiable among all other items
- Attributes are a fundamental data element

Dynamo supports 2 different kinds of primary keys:

- Partition key
    - simple primary key
    - composed of 1 attribute called, sort key
- Composite primary key
    - composed of 2 attributes

### Partitioning

As data grows, table data is partitioned and indexed by primary key

You can retrieve data from a DynamoDB table in 2 diff ways:

- QUERY operation takes advantage of partitioning to effectively locate items by using primary key
- via SCAN, enables you to locate items in table by matching conditions on non-key attributes.
    - this method give flexibility to locate items by other attributes.
    - however is less efficient bcoz dynamoDB will scan through all items in table

### Items in a table must have a key

![Untitled](Module%208%20fbdfb187681f42728d6cf087e52996e2/Untitled%205.png)

To take full advantage of query operations and DynamoDB, important to think about key that you use to uniquely identify items in table. You can set up a simple primary key based on single attribute of data values with a uniform distribution such as the Globally Unique Identifier (GUID) or other random identifiers

E.g. If you wanted to model a table with products, you would use attributes like product ID. Alternatively, you can specify a compound key, composed of a partition and a secondary key. For example, a table with books. We would use a combination of author and title to uniquely identify table items.

## Section 3: Amazon Redshift

A fast, fully managed data warehouse that makes it simple and cost-effective to analyze all your data by using standard SQL and your existing business intelligence (BI) tools.

### Introduction to Redshift

- Data warehouses are complex and expensive and can take months and significant financial resources to set up
- Redshift is a
    - fast and powerful
    - fully managed data warehouse
    - simple and cost-effective to set up, use and scale
    - enables you to run complex analytic queries against petabytes of data
    - Query optimization, parallel data processing, columnar storage on high performing disks
    - Encryption is optional

### Parallel processing architecture

![Untitled](Module%208%20fbdfb187681f42728d6cf087e52996e2/Untitled%206.png)

Leader Node:

- Manages communications w client programs and all communication with compute nodes
- Parses and develops plans to carry out database operations specifically for complex queries
- Compiles code of individual elements of the plan & assigns code to individual compute nodes
- Compute nodes run their assigned code and sends intermediate results to leader (Processing)

### Automation and scaling

- straightforward to automate most of common administrative tasks to manage, monitor, and scale Redshift cluster
- Scalability is intrinsic in Amazon Redshift. Cluster can be scaled up and down along your needs
- Security is built in and designed to provide strong encryption

### Compatibility

- Supports standard SQL
- Provides high-performance Java Database Connectivity (JDBC) and Open Database Connectivity (ODBC) which enables you to use SQL clients and BI tools of your choice

### Redshift use cases

- Enterprise data warehouse (EDW)
    - Migrate at a pace the customers are comfortable with
    - Experiment without large upfront cost or commitment
    - Respond faster to business needs
- Big data
    - Low price point
    - Managed service for ease of deployment and maintenance
    - Focus more on data and less on database management
- Software as a Service (SaaS)
    - Scale the data warehouse capacity as demand grows
    - Add analytic functionality to applications
    - Reduce hardware and software cost

## Section 4: Amazon Aurora

MySQL- and PostgreSQL compatible relational database built for cloud. 

- Combines performance and availability of high-end commercial databases with simplicity and cost-effectiveness of open-source dbs
- reduce db costs
- while improving reliability and availability of db
- automate time-consuming tasks (i.e provisioning, patching, backup, recovery etc.)

### Benefits

- Highly available and offer fast distributed storage subsystem
- Easy to setup and uses SQL queries
- designed to have drop-in compatibility with MySQL and PostgreSQL db engines
- pay as you go service
- integrates features such as AWS Database Migration Service (AWS DMS) and AWS Schema conversion Tool.

### High availability

- stores multiple copies of data across multiple Availability Zones with continuous backups to S3.
- Can use up to 15 read replicas to reduce possibility of losing data
- Instant crash recovery

### Resilient Design

- After db crash, Aurora does not need to reply redo log from last db checkpoint. Instead, performs this on every read operation
    - reduces restart time aft db crash to less than 60s
- buffer cache moved out of db process, making it available immediately at restart
    - reduces need to throttle access until cache is repopulated