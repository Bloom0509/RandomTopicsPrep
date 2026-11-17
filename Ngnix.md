## Ngnix
 - open source web server software used for reverse proxy , load balancing and caching
 - It provides HTTPS server capabilities and is mainly designed for maximum performance and stabiity
## Ngnix in CI/CD
 - production architecture
 - React-> Ngnix-> Express API-> MongoDB
 - During deployment:
 - Jenkins -> Build React -> copy build files to Ngnix ->Ngnix serves frontend
 - Instead of npm start use nginx, because Ngnix is optimised for static content
## Reverse Proxy
- client doesn't know backend servers
- Why because of SSL termination , load balancing
## Forward Proxy
- Client -> Proxy -> Internet
- Used for monitoring, logging, blocking websites
## Why cache in Nginix
- without cache every request hit DB
- But we cannot cache everything because sometimes it can stale.
- Example: OTP, bank balance etc
- Cache only: Products , blogs , catalogs
## cache strategies
 ## cache aside
  - check cache -> Miss ->DB ->update cache (redis+ mongodb) most common cache
 ## cache through
  - write cache -> write DB (slower writes)
 ## write back
  - write cache ->return -> db later (fast but risky)
 ## read through
  - cache automatically
  - fetches DB
  - application only talks to cache
## firewall
 - allows traffic
 - allow/deny rules
 - allow only backend access
## Security Group(AWS) - AWS firewall
 - EC2 -> allow: 80,443,22
 - MongoDB allow: 27017 (only from backend security group)
  ## architecture
   - Internet ->ALB -> Frontend EC2 -> Backend EC2 -> MongoDB
  
   
