## AI architecture in resume
 - User prompt -> React Frontend -> Django API -> open AI embedding Model -> VectorDB -> similar design retrived -> prompt+ context-> open AI LLM -> Generated Design Recommendations.
## what are embeddings?
 - Embeddings are dense numerical vectors that represent semantic meaning
 - Example: Red bridal saree and wedding silk saree here even though words differ embeddings are close
## why not store text directly?
 - Text cannot be mathematically compared efficiently. Embeddings transform text into vectors allowing similarity calculations
## How are embeddings generated?
 - Text-> embedding models-> 1536-> dimensional vector -> store in vectors
## why 1536?
 - Embedding model generates a high dimensional vector where each dimension captures latest semantic information
## langchain
 - Development framework that simplifies building application powered by language models enabling seamless intregration of multiple AI models and data sources.
## semantic search
 - User Query -> Embeddings -> vector search -> top k results
## similarity matric
 - cosine similarity, used for vector magnitude doesn't matter much direction represents meaning.
## vector databases
 - optimised for nearest-neighbour search across millions of embeddings
 - what does it store? ID,embeddings vector metadata
 - Example: Design-101 [0.21,0.45,...]
 - Example: Milvus,Why?
 - Fast ANN search,scalable,optimize
## what is RAG?
 - User query -> Retrieved context -> LLM -> Response
## why RAG?
 - Without RAG ? LLM only knows training data
 - With RAG ? LLM + current data
 - Benefits : less hallucination, more accurate, domain-specific answers
## LLM context Window
 - maximum number of tokens a model process in one request.
## what is Agentic AI?
 - Question-> Think-> Plan-> use Tools-> execute-> verify ->Answer
 - Planner Agent? it decides what should be done
 - executor Agent? it performs actual task
 - Tool calling? AI can use external systems
 - Memory? allows agent to remember previous interactions
## Vector search
 - converts text to vectors, search nearest vector
## hybrid search
 - keyword + vector
## Re-ranking
 - Top 20 docs then re ranker sorts again
## Embedding models
 - convert text to numbers
## Chunking strategies
  - before storing in db , we split
  ## fixed chunking 
   - Split every N character
   - example: doc 1000 words , chunk1-> 1-200, chunk2-> 201-400,  chunk3-> 401-600
  ## semantic chunking
   - split based on meaning
  ## recursive chunking
   - split hierarchy
   - paragraph->sentence->words
  ## parent child chunking
   - parent = full section
   - child = small chunk
 ## AI agents
   - It can reason, decide ,use tools, take actions, observe results, retry if needed.
   - User -> Agent -> Tool -> observation -> Agent -> Response
   - Goal -> Reason -> Take Actions -> Use Tools -> Observe Results -> Repeat until Goal Achieved
   - Key: LLM generates text, agent makes decisions and perform actions
 ## Tokenization
   - Process of breaking  raw text into smaller manageable units called tokens (such as words,subwords or characters) and assigning them numerical IDs
 ## Conversational Artificial Intelligence
   - A system that interacts with users through natural language
   - example: chatGPT, customer support bot
   - Flow: User -> LLM -> Responses
   ## characteristics
   - Maintains conversation context
   - Understands natural language
   - Generates responses
   - Usually does not perform actions
  ## Tool calling 
   - Tools are external capabilities available to the agent that perform actions beyond the LLM's training data
