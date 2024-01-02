# Module 7

## Section 1: Amazon Elastic Block Store (Amazon EBS)

### Storage

- provides persistent (retains data after power off ~ non-volatile) block storage volumes for use w Amazon EC2 instances.
- each volume automatically replicated within its availability zone to protect from component failure.
- designed for high availability and durability
- provide consistent & low-latency performance
- scale usage up or down in mins

### AWS storage options: Block vs object storage

- What if you want to change 1 character in 1-GB file?

Block storage

- change only block that contains e character

Object storage

- entire file updated
- critical difference btwn some storage types is whether they offer block-level or object-level
    - major effect on throughput, latency, and cost of storage
    - block typically faster & use less bandwidth but more $$

### Amazon EBS

- enables you to create individual storage volumes & attach to EC2 instances
- offers block-level storage
- volumes automatically replicated within its availability zone
- can be backed up automatically to S3 through snapshots (a backup of a volume)
- provides durable, detachable, block-level storage (similar to hard drive)
- low latency as directly attached to instances
- Uses:
    - Boot volumes and storage for Amazon EC2 instances
    - Data storage with a file system
    - Database hosts
    - Enterprise applications

### Volume Types

Maximum Volume Size
Maximum IOPS/Volume
Maximum Throughput/Volume

| Solid State Drive (SSD) | Hard Disk Drive (HDD) |
| --- | --- |

| General Purpose | Provisioned IOPS | Throughput-Optimized | Cold |
| --- | --- | --- | --- |
| 16 TiB | 16 TiB | 16 TiB | 16 TiB |
| 16,000 | 64,000 | 500 | 250 |
| 250 MiB/s | 1,000 MiB/s | 500 MiB/s | 250 MiB/s |
- Only SSDs can be used as boot volumes for EC2
- Lower cost options might be for additional storage or other use cases