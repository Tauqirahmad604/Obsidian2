### 1. Cluster

1. Logical grouping of instances within a single Availability zone.
2. Provide the lowest latency and the highest packet-per-second network performance for your placement group.
3. If the grouping fails, all instances fails.

### 2. Partition

1. Span across multiple availability zones in same region.
2. Instances in a partition do not share racks with the instances in other partitions.
3. Maximum of 7 partitions per Availability zone.

### 3. Spread

1. Span across each availability zones.(one copy of each ec2 is running in every AZ)
2. Reduced risk of mimilaneous failure.
3. Ecah EC2 placed on distinct hardware. 