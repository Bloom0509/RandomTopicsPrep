## Designing large scale systems
  - ensuring system remains responsive
  - flow: concurrent request -> user ->load balancer -> API servers -> DB service -> databases  <->primary bottleneck

  ## 2 key techniques
   ## database replication
   - multiple db across servers
   - high availability
   - scales read capability
   - leader-follower replication , write(master) read(slave)
   - leader-leader replication , write(master) read(master)
   ## sync vs async
  | Async | sync |
  | ----------- | ----------- |
  | syncs in background | leader and follower are updated |
  | faster than sync | guarantes consistency |
  | risks for temporary data inconsistency | impacts write performance because it has to be updated |
   ## scaling writes in leader leader 
      conflict resolution mechanism
       1. time stamp based resolution: The update with the latest timestamp wins
       2. last write wins: The most recent write regardless of timestamps, override previous one
       3. custom conflict resolution logic: Application specific rules
   ## database sharding
   - shard keys: Range based(1-100)(101-200), hash based
   - you may have to range each shard so range based is more efficient.
  ## Difference between sharding and partitioning?
   - lies in scope of data distribution
   - Sharding distributes across multiple independent physical servers or databases
   - Partitioning breaks up a single dataset into smaller manageable pieces but to the same db server
  ## SQL vs NoSQL
  | SQL | NoSQL |
  | ----------- | ----------- |
  | don't offer sharding | have built in sharding support |
  ## database partitioning
   - splitting a large table into smaller physical pieces called partitions, while still appearing as a single table to the application
   - orders Table
     
     | partition 1 | 2024 orders |
     | ----------- | ----------- |
     | partition 2 | 2025 orders |
     | partition 3 | 2026 orders |
   - The application still queries - SELECT * FROM orders;
   - but the database internally access only the relevant partitions
  ## Types of Partition
   ## range partitioning 
  - Orders-2024,2025,2026
   ## list partitioning
   - Customers- India,USA,UK
   ## hash partitioning
   - custom ID- partition1,partition2
  
