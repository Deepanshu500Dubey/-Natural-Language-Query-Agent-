
# Project Title

Here I will build a Natural Language Query Agent over some sample data. The purpose of this project is to demonstrate my ability to work with data, research techniques commonly used to solve such tasks and implement a trimmed down version of the approach to answer simple natural language queries. 



## Approach 
To begin with, we will focus on the core requirement of the project: generating straightforward, conversational answers based on reference texts. Once this is achieved, we will proceed to implement the additional features:

Citing References: Include sections from lecture notes or source materials that were used to generate the final conversational answer.

Conversational Memory: Enable the system to support multiple questions, allowing for contextually aware follow-up questions.

Generating Summary of Conversation Sessions: After a series of questions and answers, compile the conversation into concise summaries, similar to flashcards or study tips.

## Basic Question-Answer Model with URLS only 

The provided code demonstrates a workflow to build a retrieval-based question-answering (QA) system using various tools and libraries such as Pinecone, LangChain, and Hugging Face. It begins by defining a list of URLs from which data is loaded using "UnstructuredURLLoader", and then the text content is split into smaller chunks with "RecursiveCharacterTextSplitter". These chunks are converted into embeddings using the Hugging Face model "sentence-transformers/all-MiniLM-l6-v2". Pinecone, a vector database service, is initialized and used to create an index named "take2" to store and search these embeddings. A query is then performed on this vector store to retrieve relevant documents. Additionally, the script logs into the Hugging Face Hub and loads the "meta-llama/Llama-2-7b-chat-hf" model, which is set up as a text generation pipeline. A system prompt template is defined for the QA task, and a "RetrievalQA" chain is created to handle queries using the "HuggingFacePipeline" model. Finally, the QA chain is queried with a question about milestone model architectures and papers, and the result along with the source document URLs are printed. This setup allows for efficient retrieval of relevant information from documents and generating context-aware answers using a powerful language model.







## Basic Question-Answer Model with URLS and LLM Table
 
The provided code demonstrates a workflow to build a retrieval-based question-answering (QA) system using various tools and libraries such as Pinecone, LangChain, and Hugging Face. It begins by defining a list of URLs from which data is loaded using UnstructuredURLLoader, and then the text content is split into smaller chunks with RecursiveCharacterTextSplitter. Additionally, the script retrieves tabular data from a specified URL, parses it with BeautifulSoup, and converts it into a pandas DataFrame. These chunks and tabular data are converted into embeddings using the Hugging Face model sentence-transformers/all-MiniLM-l6-v2. Pinecone, a vector database service, is initialized and used to create an index named "take2" to store and search these embeddings. A query is then performed on this vector store to retrieve relevant documents. Additionally, the script logs into the Hugging Face Hub and loads the meta-llama/Llama-2-7b-chat-hf model, which is set up as a text generation pipeline. A system prompt template is defined for the QA task, and a RetrievalQA chain is created to handle queries using the HuggingFacePipeline model. Finally, the QA chain is queried with a question about milestone model architectures and papers, and the result along with the source document URLs are printed. This setup allows for efficient retrieval of relevant information from documents and generating context-aware answers using a powerful language model.


## A Layer of Citation added 
The provided code demonstrates a workflow to build a retrieval-based question-answering (QA) system using various tools and libraries such as Pinecone, LangChain, and Hugging Face. Initially, it installs necessary packages and then defines a list of URLs from which data is loaded using UnstructuredURLLoader. The text content from these URLs is split into smaller chunks with RecursiveCharacterTextSplitter. These chunks are then embedded using the Hugging Face model sentence-transformers/all-MiniLM-l6-v2. Pinecone, a vector database service, is initialized with an API key and environment, and used to create an index named "take2" to store and search these embeddings. The script logs into the Hugging Face Hub and loads the meta-llama/Llama-2-7b-chat-hf model, setting it up as a text generation pipeline. A system prompt template is defined for the QA task, and a RetrievalQA chain is created to handle queries using the HuggingFacePipeline model. Finally, the QA chain is queried with a question about milestone model architectures and papers, and the result, along with the source document URLs, is printed. This setup allows for efficient retrieval of relevant information from documents and generating context-aware answers using a powerful language model.
## Adding Conversational Memory 
The provided script demonstrates how to build an advanced retrieval-based question-answering (QA) system using LangChain, Pinecone, and Hugging Face models. It begins by installing the necessary libraries and defining a list of URLs to load data from using UnstructuredURLLoader. The text content from these URLs is split into smaller chunks with RecursiveCharacterTextSplitter. These chunks are then embedded using the Hugging Face model lmsys/fastchat-t5-3b-v1.0. Pinecone is initialized to create a vector store to store and search these embeddings. The script also configures and loads the meta-llama/Llama-2-7b-chat-hf model with 4-bit quantization for efficient performance. The text generation pipeline is set up using this model. A system prompt template is defined for the QA task, and a RetrievalQA chain is created to handle queries using the HuggingFacePipeline model. The QA chain uses a conversation memory buffer to keep track of the interaction history. The script demonstrates running multiple queries, including "What is language modelling?" and checking the conversation history, showing how the QA system can handle and remember user interactions effectively. The final output includes the answers and the source URLs of the documents used.
## Adding Summarization to the model
This script demonstrates a comprehensive workflow for creating a Natural Language Query Agent using the LangChain library, Hugging Face's transformers, and Pinecone for vector storage. The process begins by installing necessary libraries and defining URLs to load data from. The UnstructuredURLLoader is utilized to load documents, which are then split into smaller chunks using RecursiveCharacterTextSplitter for efficient processing. Each chunk is embedded using the HuggingFaceEmbeddings model, specifically "lmsys/fastchat-t5-3b-v1.0", and stored in Pinecone's vector database.

Subsequently, the script initializes a Hugging Face pipeline for text generation using the "meta-llama/Llama-2-7b-chat-hf" model, which is configured with 4-bit quantization for efficient performance. This model, wrapped in the LangChain's HuggingFacePipeline, is used in a RetrievalQA chain setup, incorporating a custom prompt template and conversation buffer memory to maintain context across interactions.

Queries are executed through this QA chain, storing the questions and their corresponding answers in a list. Additionally, a summarization pipeline using "facebook/bart-large-cnn" generates a session summary from the captured QA pairs. Flashcards are created for each QA pair, presenting a concise Q&A format suitable for study or review.

This setup exemplifies the integration of advanced NLP techniques for effective information retrieval and question answering, augmented by context-aware interaction and summarization capabilities, making it a robust solution for building intelligent query agents.






