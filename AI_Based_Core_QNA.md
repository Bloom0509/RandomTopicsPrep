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
