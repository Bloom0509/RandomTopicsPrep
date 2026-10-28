## grpc 
 - open source framework that enables client and server applications to communicate across distributed systems
## Key technologies used
  ## Protocol Buffer 
  - grpc uses protocol as its interface definition language. you define your data structure and service endpoints in a proto file. grpc the  automatically generates strongly typed idiomatic client and server code(stubs)
  ## HTTP/2 Transport
  - unlike HTTP/1.1 used by REST. grpc uses HTTP/2. This allows for multiplexing (sending multiple requests over single connectors), headers compression and bi-directional streaming.
## why GRPC?
  ## contact first APIs
  - Both client and server are bound by the same proto contract
  ## Binary serilaization
  - protobuf compresses data into a binary format making payload smaller.
  ## streaming support
  - client side , server side streaming
  ## multi language
  - go,python,c++,node js
  ## best use cases
  - microsevices architecture and real time streaming application
