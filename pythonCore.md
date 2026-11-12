## Memory Management in Python
 - Reference Counting, Eg: a=[1,2] ,b=a
 - Reference count=2
 - when it becomes 0, a=None,b=None
 - Memory gets freed
 - Garbage Collector handles cyclic references
 - Garbage Collector removes unreachable code
## GIL(Global Interpreter Lock)
 - only one thread executes python bytecode at a time
 - CPU bound tasks, don't gain much from threading
 - Good for- I/O, File, API calls
## MultiProcessing
 - create separate processes
 - Each process has own memory
 - Own Python interpretes own GIL
 - Useful for: Image processing, ML, data processing
## Memory leak detection
 - Tools: tracemalloc(), objgraph, memory-profiler
 - Production: Monitors RSS memory, Heap Growth and object count
 - Spot the symptoms: check RAM usage
## Memcache with TTL 
  - In memory cache , allows you to store data temporarily , automatically expiring and deleting set numbers of seconds
   -      import time
          class cache:
             def __init__(self):
               self.store={}    // initialization
             def set( self,key,value,ttl):  //storing data with expiry
               expiry=time.time()+ttl
               self.store[key]=(value,expiry)
             def get(self,key): //retrieving data
               if key not in self.store:
                   return None
               value,expiry=self.store[key]
               if time.time()>expiry:  //lazy deletion
                  del self.store[key]   // deletes the item from the dictionary to free up memory
                  return None
               return value
         //usage
            cache=cache()
            cache.set("user","Arpita",5)
            print(cache.get("user")) # Arpita
            time.sleep(6)
            print(cache.get("user"))  # None
    
