# Documentation-Assitant

This project was initially built as a means for me to get the best help for learning Langchain. It is a Chatbot made specifically to use the langchain documentation as its context using RAG. With this, I am able to have a personalized Langchain professionally helping with each project. It's designed to help users navigate through the Langchain documentation and can help you with any errors you face wit Langchain. As well it provides direct sources for each of the information it returns to the user allowing you to confirm the information.

## Demo
<p>Here is a youtube link to the demo: https://youtu.be/Z2x0aGTf-IQ </p>
<img src="https://github.com/Papakobina/Documentation-Assitant/blob/main/demo_pic_helper.png"/>

## Technical Explanation

This project is a conversational interface to the Langchain documentation, leveraging advanced technologies such as OpenAI's language model and Pinecone's vector store for document retrieval.

### OpenAI's Language Model

We use OpenAI's language model because of its ability to understand and generate human-like text. This model is trained on a diverse range of internet text, which allows it to generate responses to user queries that are contextually relevant and accurate. The model is used in `core.py` to generate responses to user queries.

### Pinecone's Vector Store

Pinecone's vector store is used for document retrieval. It allows us to store and retrieve documents in a high-dimensional vector space, which is ideal for tasks like semantic search. We use Pinecone's vector store to store the Langchain documentation and retrieve relevant documents based on user queries. The ingestion of documents into the vector store is handled in `ingestion.py`.

### Streamlit

Streamlit is a fast, easy-to-use open-source framework for building data science web applications. We use Streamlit in `main.py` to create a user interface where users can input their queries and receive responses. Streamlit allows us to maintain a history of user prompts and generated responses, providing a conversational interface to the Langchain documentation.

### Operations Performed

The project performs several operations to provide a conversational interface to the Langchain documentation. First, it loads the Langchain documentation from ReadTheDocs and splits the text into manageable chunks. These chunks are then added to Pinecone's vector store. When a user enters a query, the project uses OpenAI's language model to generate a response. The response is based on both the user's query and the relevant documents retrieved from Pinecone's vector store.


## Description

The application consists of three main Python files:

1. `core.py`: This file contains the main logic for running the language model. It uses OpenAI's language model to generate responses to user queries. It also uses Pinecone's vector store for document retrieval.

2. `main.py`: This is the main entry point of the application. It uses Streamlit to create a user interface where users can input their queries and receive responses. It also maintains a history of user prompts and generated responses.

3. `ingestion.py`: This file is responsible for loading the Langchain documentation from ReadTheDocs, splitting the text into manageable chunks, and adding them to Pinecone's vector store.
## File Descriptions

### `core.py`

This file contains the main logic for running the language model. It uses OpenAI's language model to generate responses to user queries and Pinecone's vector store for document retrieval.

The `run_llm` function is the main function in this file. It takes a query and a chat history as input. It initializes the OpenAI embeddings and the Pinecone vector store. It then creates an instance of `ChatOpenAI` and `ConversationalRetrievalChain`. The function invokes the `ConversationalRetrievalChain` with the query and chat history and returns the response.

### `ingestion.py`

This file is responsible for loading the Langchain documentation from ReadTheDocs, splitting the text into manageable chunks, and adding them to Pinecone's vector store.

The `ingest_docs` function is the main function in this file. It loads the Langchain documentation, splits the text into chunks, and adds them to the Pinecone vector store. 

In this project after downloading and vectorizing the langchain documentation we ended up with 55k vectors store in pinecone.

### `main.py`

This file is the main entry point of the application. It uses Streamlit to create a user interface where users can input their queries and receive responses. It also maintains a history of user prompts and generated responses.

The `create_sources_string` function takes a set of source URLs and returns a formatted string with each source URL on a new line.

The `prompt` variable is used to capture the user's input. If the user enters a query, the `run_llm` function from `core.py` is called with the query and the chat history. The response from the `run_llm` function is then formatted and added to the chat history.

The `message` function from the `streamlit_chat` module is used to display the user's queries and the generated responses in the Streamlit interface.
