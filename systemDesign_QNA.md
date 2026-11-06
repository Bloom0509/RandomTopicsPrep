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
