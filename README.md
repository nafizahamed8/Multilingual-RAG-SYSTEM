# Multilingual-RAG-SYSTEM
Develop a Simple Multilingual Retrieval-Augmented Generation (RAG) System

Setup Guide
Retrieval-Augmented Generation is a way to make LLM smarter by giving extra information at a time.
Rag based system build in four steps:
Indexing,

Retrieval,

Augmentation,

Generation

<img width="491" height="281" alt="rag drawio" src="https://github.com/user-attachments/assets/5bc786d4-786b-4d7d-aa29-27d62dac912e" />




Rag Pipeline


Indexing is the process of preparing the knowledge base .It has four sub steps

Document Ingestion:Load source knowledge into memory.

Text Chunking:Break large documents into small semantically meaningful chunks

Embedding Generation:Convert each chunk into dense vector.

Storage in a vector store:Store the vector along with the original chunk+metadata in a vector database.

Retrieval is the real time process of finding the most relevant piece of information from knowledge base.

Augmentation refers to the step where the retrieved documents (chunks of relevant context) are combined with the user’s query to form a new, enriched prompt for the LLM.

Generation is the final step where a Large Language Model (LLM) uses the user’s query and the retrieved & augmented context to generate a response.

<img width="376" height="586" alt="Rag 2 drawio" src="https://github.com/user-attachments/assets/59d4cd5b-a040-406b-a2aa-675e2a528092" />



