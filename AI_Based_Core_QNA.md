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
