## Design a data validation framework
   ### Architecture
   - Data Source -> Schema validation -> Business Rules Validation -> Quality Checks -> Error logging ->Storage
   ### Validation types
   - Schema Validation {name:str, age:int}
   - NULL validation  if age is None:reject
   - Range validation 0<=age<=120
   - Duplicate validation email uniqueness
   ### Framework Design
      class Validator:
       1.def validator schema():pass
       2.def validator nulls():pass
       3.def validator rules():pass

## Api Rate limiting + Timeout design   
### Architecture
  - Producer-> Queue(Kafka/SQS)-> Worker Pool-> Retry Queue -> API -> Rate limiting
### Rate limiting
  - Token Bucket Algorithm, 100 tokens/min, only allow calls if token exists
### Timeout
  - requests.get(url,timeout -5), exponential backoff,retry 3 times
### Circuit Breaker
  - if api fails repeatedly, stop calling api for few minutes

## Pipeline for Schema Validation
 - Flow-> Source-> Schema Registry-> Validation Engine-> Accepted Records-> Rejected Records
 - Examples ->
   ### Using Pydantic
       class pydantic import BaseModel
         class User(BaseModel):
              name: str
              age:int
 - validations -> users(**payload)
 - Benefits-> Early failure detection, strong typing and data equity

## Skews in join
 - Suppose Orders Table and customerA has 1 milliom rows and customerB has 10 rows.
 - Join order customers one node gets 1 million rows and others get 10 rows.
 - Result is slow execution and unbalanced workload
   ### Solution
     - Salting -> Add random key to distribute data
     - BroadCast join -> Small tables copied to all nodes
     - Repartitioning -> Redistribute data evenly
 ## WaterMark
   - Store successful timestamp
   - benefits-> fast, less storage, lower cost
   - examples-> watermark: 2025-06-05 10:00
   - next run-> SELECT * FROM orders WHERE updated_at> '2025-06-05 10:00'
 ## Incremental Loading
   - full load-> Every run =10 millions rows bad
   - incremental load only load new rows
 ## Store 10gb file without memory issues
   - Chunk Processing
   - Cloud Storage
   - Streaming
 ## SCD type 2 (Slowly Changing Dimension)
   ### Trace history
       customer id=1 , city= delhi, later city= Mumbai
   ### Dimensional Table
   | id | city | start Date | End Date | Current |
   | ----------- | ----------- | ----------- | ----------- | ---------- |
   | 1 | Delhi | 2024 | 2025 | N
   | 2 | Mumbai | 2025 | NULL | Y
   ### Process
      when change arrives:-
       - Close old record -> end-date=now()
       - Insert new record -> current=Y
   Preserves historical changes by expiring the old rows and inserting a new version with effective dates and current flags    
 ## How to optimise slow queries
  1. Check query plan, EXPLAIN ANALYZE SELECT
  2. Add Indexes
  3. Avoid select *
  4. Optimise JOINS
  5. Pagination
  6. Use composite Index
  7. Remove N+1 queries
## Top K frequent element , Time complexity O(nlogK) Space complexity O(n)
    import heapq
    def freequnecyEle(arr,k):
          mp={},heap=[]
          for i in arr:
             mp[i]=mp.get(i,0)+1
          for num,val in mp.items():
             heapq.heappush(heap,(val,num))
             if len(heap)>k:
                heapq.heappop(heap)
          return [num for freq,num in heap]
  ## SQL query who ordered for consecutive 3 days
     WITH ctc AS (SELECT user_id, order_date
      ROW_NUMBER() OVER (PARTITION BY user_id
      ORDER BY order_date ) rn FROM orders),
      grp As (SELECT user_id, DATE_SUB( order_date,
      INTERVAL rn DAY) grp_id FROM ctc)
      SELECT user_id 
      FROM grp
      GROUP BY user_id,grp_id
      HAVING COUNT(*) >=3
   
     
