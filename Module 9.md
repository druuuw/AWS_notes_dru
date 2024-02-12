# Module 9: Cloud Architecture

## Section 1: AWS Well-Architected Framework

Cloud architects 

- Engage with decision makers to identify business goal and the capabilities that need improvement
- Ensure alignment  between technology  deliverables of a solution and the business goals
- Work with delivery teams that are implementing the solution to ensure that the technology features are appropriate

### What is the AWS Well-Architected Framework

- Guide for designing infrastructures that are:
    - Secure
    - High-performing
    - Resilient
    - Efficient
- A consistent approach to evaluating and implementing cloud architectures
- A way to provide best practices that were developed through lessons learned by reviewing customer architectures

### Pillars of the AWS Well-Architected Framework

Six Pillars:

- Operational excellence,
- Security,
- Reliability,
- Performance efficiency,
- Cost optimization,
- and Sustainability.

![Untitled](Images/Module%209%20Cloud%20Architecture%200f7737a97a8448049972233fd2d1003b/Untitled.png)

### Operational Excellence - deliver business value

- Focus
    - Run & monitor systems to deliver business value, and to continually improve supporting processes and procedures.
- Key topics
    - Automating changes
    - Responding to events
    - Defining standards to manage daily operations
- Design principles
    - perform operations as code
        - define entire workload as code and update as code
        - limit human error
        - and enable consistent responses to events
    - make frequent, small, reversible changes
        - design workloads to enable components to be updated regularly
        - make changes in small increments that are reversible
    - refine operations procedures frequently
        - set regular game days to review all procedures, validate effectiveness, ensure team is familiar
    - anticipate failure
        - identify potential sources of failure to be removed or mitigated.
        - regular game days to test if effective and teams know how to run
    - learn from all operational events and failure
        - drive improvement thru lessons learned from all operational events and failures
        - share what is learned across teams and entire org
- Operational excellence questions

— operational teams must understand business and customer needs so they can efficiently support business outcome

- Organizations
    - How do you determine what your priorities are
- Operate
    - How do you understand the health of your workload
- Prepare
    - How do you mitigate  deployment risks
- Evolve
    - How do you evolve operations?

### Security Pillar - protect and monitor systems

- Focus
    - Protect information, systems, and assets while delivering
    business value through risk assessments and mitigation
    strategies
- Key topics
    - Protecting confidentiality and integrity of data
    - Identify and manage who can do it
    - protect systems
    - establishing controls to detect security events

**Security design principles**

- Implement strong identify foundation
    - implement principle of least privileged and enforce separation of duties
    - centralize privilege management and reduce/eliminate reliance on long-term credential
- Enable traceability
    - monitor, alert, and audit actions and changes to your environment in real time
    - integrate logs & metrics w systems to automatically respond & take action
- Apply security at all layers
    - apply defense in depth and apply security controls to all layers of architecture
    - i.e. edge network, vpc, subnet
- Automate security best practices
    - improve ability to securely scale more rapidly and cost effectively.
    - create secure architectures and implement controls that are defined and managed as code in version-controlled templates
- Protect data in transit and at rest
    - classify data into sensitivity levels and use mechanisms (encryption, tokenization, and access control) where appropriate
- Keep people away from data
    - to reduce risk of loss or modification of sensitive data due to human error, create mechanisms and tools to reduce or eliminate need for direct access/manual processing
- Prepare for security events
    - run incident response simulations and use tools w automation to increase speed of detection, investigation and recovery

**Security questions**

- Security
    - How do you securely operate your workload
- Identity and access management
    - How do I manage identities for people and machines
- Detection
    - How do you detect and investigate security events
- Infrastructure protection
    - How do you protect your network resources
- Data protection
    - How do you classify your data?
- Incident response
    - How do you anticipate, respond to and recover from your incidents?

### Reliability pillar — recover from failure and mitigate disruption

- Focus
    - Ensure workload performs its intended function correctly and consistently when it’s expected to
- Key topics
    - Designing distributed systems
    - Recovery planning
    - Handling change

**Design principles**

- Automatically recover from failure
    - monitor systems for key performance indicators and configure systems to trigger automated recovery when threshold is breached.
- Test recovery procedures
    - test how systems fail and validate recovery procedures
    - use automation to simulate diff failures/recreate scenarios that led to failures
    - this exposes failure pathways and help us rectify b4 it happens
- Scale horizontally to increase aggregate workload availability
    - replace 1 large resource w multiple small resources to reduce impact of a single point of failure
- Stop guessing capacity
    - monitor depend and system usage, automate addition or removal of resources to maintain optimal lvl for satisfying demand
- Manage change in automation
    - Use automation to make changes to infrastructure and manage changes in automation

![Untitled](Images/Module%209%20Cloud%20Architecture%200f7737a97a8448049972233fd2d1003b/Untitled%201.png)

— system must have both well-planned foundation and monitoring in place. must have mechanisms for handling change in demand/requirements. should be designed to detect failure and automatically heal itself

### Performance Efficiency Pillar

- Focus
    - Use IT and computing resources to efficiently to meet system requirements and to maintain efficiency as demand changes and technologies evolve
- Key topics
    - Selecting right resource type/sizes based on workload requirements
    - Monitoring performance
    - Making informed decisions to maintain efficiency as business evovle

**Design principles**

- Democratize advanced technologies
    - consume technologies as a service
    - i.e. technologies such as NoSQL dbs, media transcoding and machine learning are sought for skills
    - so these skills become a service that teams use to allow them to focus on development
- Go global in minutes
    - deploy systems in multiple AWS regions to provide lower latency and a better customer experience at minimal cost
- Use serverless architectures
    - remove operations burden of running and maintaining servers.
    - lower transactional costs coz managed services operate at cloud scale
- Experiment more often
    - perform comparative testing of different type of instances, storage, or configs
- Consider mechanical sympathy
    - use technology approach that aligns best to what you are trying to achieve.
    - i.e. consider data access patterns when selecting approaches for db/storage

![Untitled](Images/Module%209%20Cloud%20Architecture%200f7737a97a8448049972233fd2d1003b/Untitled%202.png)

— use data to design n build high performance architecture. gather data on all aspects of architecture, from high lvl design to selection and config of resource types. review choice periodically ensuring you take advantage of AWS service. use tradeoffs in architecture to improve performance such as using compression, using caching, or relaxing consistency

### Cost Optimization pillar - eliminate unneeded expense

- Focus
    - Avoid unnecessary costs
- Key topics
    - Understanding and controlling where money is being spent
    - Selecting most appropriate and right number of resource types
    - Analyzing spend over time
    - Scaling to meeting business needs without overspending

**Design principles**

- Implement Cloud Financial Management
    - to achieve financial success and accelerate business value realization in the cloud, need to invest in cloud financial management and cost optimization
    - build capability thru knowledge building, programs, resources, and processes to become cost-efficient
- Adopt a consumption model
    - Pay only for what compute resources you use
    - Increase/decrease usage depending on business requirements, not by using forecasdting
- Measure overall efficiency
    - measure business output of workload and costs of delivering it
    - use this to know the gains you make frm inc/dec costs
- Stop spending money on undifferentiated heavy lifting
    - AWS does the heavy lifting of handling servers
    - can focus on customers and business project
- Analyze and attribute expenditure
    - cloud makes it easier to accurately identify system usage and costs, and attribute IT costs to individual workload owners.
    - helps to measure return on investment (ROI) and gives workload owners an opportunity to optimize and reduce resources cost

![Untitled](Images/Module%209%20Cloud%20Architecture%200f7737a97a8448049972233fd2d1003b/Untitled%203.png)

![Untitled](Images/Module%209%20Cloud%20Architecture%200f7737a97a8448049972233fd2d1003b/Untitled%204.png)

## Section 2: Reliability and availability

### Reliability

- measure of system’s ability to provide functionality when desired by the user
- system includes all system components: hardware, firmware, and software
- probability that entire system will function as intended for specified period
- Mean time btwn failures (MTBF) = total time in service/number of failures

### Understanding reliability metrics

![Untitled](Images/Module%209%20Cloud%20Architecture%200f7737a97a8448049972233fd2d1003b/Untitled%205.png)

![Untitled](Images/Module%209%20Cloud%20Architecture%200f7737a97a8448049972233fd2d1003b/Untitled%206.png)

### Availability

- Normal operation time / total time
- percentage of update (i.e. 99.9%) over time (i.e. 1 year)
- Number of 9s — Five 9s means 99.999% availability

### High availability

- System can withstand some measure of degradation while still remaining available
- downtime is minimized
- minimal human intervention is required

### Availability tiers

![Untitled](Images/Module%209%20Cloud%20Architecture%200f7737a97a8448049972233fd2d1003b/Untitled%207.png)

### Factors that influence availability

- Fault tolerance
    - built-in redundancy of an application’s components and ability to remain operational
    - relies on specialized hardware to detect failure in system components (i.e. processor, memory)
- Recoverability
    - process, policies, and procedures that related to restoring service after catastrophic event.
    - ability to accommodate increases in capacity needs
- Scalability
    - ability of an app to accommodate increases in capacity needs without changing design
    - ability to restore service quickly and without lost data if disaster makes components unavailable

## Section 3: AWS Trusted Advisor

- Online tool that provides real-time guidance to help provision resources follow AWS best practices
- Look at entire AWS environment and gives real-time reccos to 5 categories:
- Cost Optimization
    - trusted advisor looks at resource use and makes reccos to help you optimize cost by eliminating unused/idle resources, or by mking commitments to reserved capacity
- Performance
    - Improve the performance of service by checking service limits, ensures take advantage of provisioned throughput, and monitoring for overutilized instances
- Security
    - improve security of app by closing gaps, enabling various AWS security features, and examine permissions
- Fault Tolerance
    - increase availability and redundancy of AWS app by taking advantage of auto scaling, health checks
- Service Limits
    - trusted advisor checks for service usage that is more than 80% of service limit. Values based on snapshot, so current usage might differ. Limit and usage data can take up to 24 hours to reflect any checks