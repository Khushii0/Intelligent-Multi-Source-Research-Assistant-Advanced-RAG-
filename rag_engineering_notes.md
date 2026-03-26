\# Retrieval Augmented Generation Engineering Notes

\#\# What is RAG?

Retrieval Augmented Generation (RAG) is an architecture that combines  
information retrieval with large language models.

Instead of relying only on model parameters, RAG retrieves relevant  
documents from a knowledge base and uses them as context.

This improves factual accuracy and allows systems to answer questions  
based on external knowledge sources.

\#\# Hybrid Retrieval

Hybrid retrieval combines:

1\. Dense vector search using embeddings  
2\. Keyword-based search such as BM25

Dense retrieval captures semantic meaning while keyword search captures  
exact term matches.

Combining both improves retrieval accuracy.

\#\# Reranking

Initial retrieval may return irrelevant chunks.

A reranker model evaluates query-document pairs and sorts them by  
true relevance.

This step significantly improves RAG performance.

\#\# Vector Databases

Common vector databases include:

\- FAISS  
\- Chroma  
\- Pinecone  
\- Weaviate

Vector databases store embeddings and allow similarity search.

\#\# RAG Pipeline

Typical pipeline:

User Query → Embedding → Retrieval → Reranking → LLM Generation