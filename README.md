# Multilingual-RAG-SYSTEM
Develop a Simple Multilingual Retrieval-Augmented Generation (RAG) System

Setup Guide
Retrieval-Augmented Generation is a way to make LLM smarter by giving extra information at a time.

Rag based system build in four steps
Indexing,

Retrieval,

Augmentation,

Generation

<img width="491" height="281" alt="rag drawio" src="https://github.com/user-attachments/assets/5bc786d4-786b-4d7d-aa29-27d62dac912e" />




# Rag Pipeline


Indexing is the process of preparing the knowledge base .It has four sub steps

Document Ingestion:Load source knowledge into memory.

Text Chunking:Break large documents into small semantically meaningful chunks

Embedding Generation:Convert each chunk into dense vector.

Storage in a vector store:Store the vector along with the original chunk+metadata in a vector database.

Retrieval is the real time process of finding the most relevant piece of information from knowledge base.

Augmentation refers to the step where the retrieved documents (chunks of relevant context) are combined with the user’s query to form a new, enriched prompt for the LLM.

Generation is the final step where a Large Language Model (LLM) uses the user’s query and the retrieved & augmented context to generate a response.

<img width="376" height="586" alt="Rag 2 drawio" src="https://github.com/user-attachments/assets/59d4cd5b-a040-406b-a2aa-675e2a528092" />

<img width="701" height="541" alt="Rag 3 (2) drawio" src="https://github.com/user-attachments/assets/ec51149d-886c-4bab-86f4-93cbe46354ba" />

# Used Tools Libraries and Packages

A Retrieval Augmented Generation  system for Bangla and English Documents,powered by Google Gemini and Hugging Face Embeddings.

For this project purpose, I used LangChain an open source framework,which is used for developing applications powered by LLM.

LangChain gives  build in functionality for all kind of components which is necessary for my project.

Using LangChain ,you can built conversational chat-bots, AI knowledge assistant,AI agents.

LangChain models are the core interface by which you can interact with AI models.

Chains automatically build one stage output to second stage input. Chain is a concept by which helps you to build pipeline in LangChain.

<img width="441" height="361" alt="LangChain drawio" src="https://github.com/user-attachments/assets/c75bad82-acae-4492-bdd5-3be7031436ad" />

I used python’s built in functionality os module to work with operating system functionalities like environment variables

Google Gemini AI used for generating responses ,the brain of this project.

HuggingFaceEmbeddings model has been used to convert text into numerical vectors. To understand documents meaning.

PDF Document loader has been used to to read and extract text from PDF files.

FAISS vector-database has been used to store and quickly search through documents embedding

prompt template creator has been used to structure how we talk with AI models

RunnablePassThrough has been used as pipeline connector, to chain different processing steps together.

Torch library has been used for GPU acceleration

colab secret manger has been used to securely access google api key stored in colab.

# Methods and Challenges

I have used pypdf loader from LangChain for text extracting which is fastest for digital PDF and it also preserve basic formatting but it has some limitation ,it may mishandle Bangla conjuncts. 

Fall back if pypdf failed,i used alternative pdfminer which is better extracting raw text from complex layouts.Though it is slower than pypdfloader.

Broken encoding was fixed using custom function clean_bangla_text. Invisible characters were stripped during cleaning. Conjunct letters needed manual fixes. Mid-sentence line breaks were handled 

by the RecursiveCharacterTextSplitter with a 200-character overlap to maintain context.

For chunking strategy I used Hybrid chunking strategy.Primary split was paragraph based to acquire complete ideas.Secondary split was sentence based maintaining linguistic boundaries which 

respects the natural structure of languages.Then I used 1000 character chunks with 200 character overlapping. It keeps meaning intact,remember context and fixes and fits bangla style.

paraphrase-multilingual-mpnet-base-v2 from Sentence Transformers (Hugging Face) has been used for embedding.It is specially trained on 100+ languages including high quality Bangla data.It’s 

mpnet architecture is better than bert for sentence meaning. 768 dimensional vectors capture subtle context differences and it also runs on GPU.It’s key advantage is even if the query uses 

different wording the embeddings remains semantically close.

Query and all stored chunks are converted into high dimensional vectors using embedding models and the similarity between  query and stored chunks is computed using cosine similarity, which 

measures the angle between vectors.It works well for high dimensional embeddings. For vector storage I have used FAISS database because it uses highly optimized algorithm for searches rather 

than brute force search.

 My embeddng models generate dense vector representation in a share semantic space is optimized for multilingual retrieval.It focuses on cosine similarity(angle based).FAISS retrieval uses 
 
maximum mariginal relevance to make balance between diversity and relevancy.If the query is vague it may return irrelevant chunks.

In some cases LLM didn’t generate answer. Using better chunking may improve the result or may be using better models with more parameters will give more accuracy.







