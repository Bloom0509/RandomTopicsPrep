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
   ## database sharding
