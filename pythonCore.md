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
