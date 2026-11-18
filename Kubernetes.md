## kubernetes
 - contains orchestration platform that automates deployment , scaling , networking , self healing and life cycle management of containerized applications across a cluster of machines.
## Architecture

```mermaid
flowchart TD
 subgraph CP["CONTROL PLANE"]
        direction LR
        API["API Server"]
        SCH["Scheduler"]
        CM["Controller Manager"]
        ETCD[("etcd Database")]

        API <--> ETCD
    end

    subgraph WN["WORKER NODES"]
        direction LR

        subgraph N1["NODE 1"]
            direction TB
            P1(["Pod 1"])
        end

        subgraph N2["NODE 2"]
            direction TB
            P2(["Pod 2"])
        end

        subgraph N3["NODE 3"]
            direction TB
            P3(["Pod 3"])
        end
    end

    API --> N1
    API --> N2
    API --> N3

    SCH -.-> N1
    SCH -.-> N2
    SCH -.-> N3

    CM -.-> API
```



