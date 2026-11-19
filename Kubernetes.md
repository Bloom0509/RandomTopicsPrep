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

## worker Node Components
  ## kubelet 
   - agent running on each node, talks to API server from node. It creates monitor pods
  ## Container Runtime
  - runs containers example: docker
  ## kube proxy
  - handles networking, route traffic
  - Pod-> express
  ## pod
  - smallest deployable unit , supports multiple container
  - Pod->App Container.logging

## what happens when pod crashes?
- replica set recreates
## what happens when node crashes?
- scheduler moves pods to healthy pods
## how does service find pods?
- labels + selectors
## why deployment?
- scaling
- Rollback
- Rolling updates
## how kubernetes achieve zero downtime?
- rolling updates
- readiness probes
## Ingress  
- network traffic, management to the services in a kubernetes cluster
- acting as an API object that manages external access to service within the clusters

## Deployment Architecture
- React, Express, MongodB database
- Each component is containerized using docker
- React is served through Nginx
- Express exposes REST APIs and Socket.IO
- MongoDB stores activity data
- Jenkins acts as the CI/CD tool
- when code is pushed to Github, a webhook triggers jenkins to run tests,build docker images and push them to docker Hub.
- Kubernetes deploys containers using deployments and services
- frontend and backend run multiple replicas for high availability while service provide stable networking
- Ingress acts as a reverse proxy and SSL termination layer
- Kubernetes handles scaling, self healing and rolling updates, ensuring zero downtime deployments

## kubernetes and why not
- Docker compose: Single machine
- Kubernetes: cluster, multiple nodes, auto healing , auto scaling , rolling updates
## why not deploy containers directly?
- Containers are unmanaged
- Pods provide networking, storage, lifecycle , health checks
- Kubernetes manages pods
## Github Webhook
- webhook is an event driven HTTP callback where github automatically sends a POST request to jenkins whenever a repository event such as code push occurs triggering the CI/CD pipeline without pooling
## Deployment Architecture

```mermaid
flowchart TD
    A[User] --> B[Internet]
    B --> C[Ingress]
    C --> D[Nginx / Load Balancer]

    D --> E[Frontend Pod 1 - React]
    D --> F[Frontend Pod 2 - React]

    E --> G[Backend Service]
    F --> G

    G --> H[Backend Pod 1 - Express]
    G --> I[Backend Pod 2 - Express]

    H --> J[MongoDB Service]
    I --> J

    J --> K[MongoDB Pod]
```



