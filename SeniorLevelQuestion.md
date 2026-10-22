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
   
     
