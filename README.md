# HuggingFacePinecone_DocumentChat
 ```markdown
# Pinecone Document QA

This repository contains a Jupyter Notebook (`Chat with Pinecone.ipynb`) that demonstrates a document question-answering system using Pinecone, LangChain, and Hugging Face models.

## Project Description

The notebook loads PDF documents from a specified directory, chunks the text, generates embeddings using a Hugging Face model (`sentence-transformers/all-MiniLM-L6-v2`), stores these embeddings in a Pinecone vector database, and uses a language model (`bigscience/T0_3B`) to answer questions based on the document content.

## Technologies Used

* **Pinecone:** For efficient vector storage and similarity search.
* **LangChain:** For document loading, text splitting, and question answering pipelines.
* **Hugging Face Transformers:**
    * `sentence-transformers/all-MiniLM-L6-v2`: For generating text embeddings.
    * `bigscience/T0_3B`: For language model inference and question answering.
* **PyPDF:** For loading and processing PDF documents.
* **unstructured:** For document parsing.
* **python-dotenv:** For managing API keys securely.

## Setup and Installation

1.  **Clone this repository:**

    ```bash
    git clone [repository URL]
    cd [repository directory]
    ```

2.  **Install dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

3.  **Set up Pinecone:**

    * Create a Pinecone account and obtain your API key.
    * Create a Pinecone index named `pdf-qa-index`.
    * Store your Pinecone API key securely using environment variables or a `.env` file.
    * The code uses `google.colab.userdata.get('PINECONE_KEY')`, which is good for Colab. However, never hardcode API keys.

4.  **Place PDF documents:**

    * Place your PDF documents in a directory named `documents/`.

5.  **Run the Notebook:**

    * Open and run the `Chat with Pinecone.ipynb` notebook in Google Colab or Jupyter.

## Notebook Structure

* `Chat with Pinecone.ipynb`: The main notebook containing the code.
* `requirements.txt`: A list of required Python packages.
* `documents/`: Directory containing PDF documents.
* `README.md`: This file.

## Code Explanation

* **Document Loading and Chunking:**
    * `PyPDFDirectoryLoader` is used to load PDF documents from the `documents/` directory.
    * `RecursiveCharacterTextSplitter` is used to split the documents into smaller chunks for embedding.
* **Embeddings and Vector Storage:**
    * `HuggingFaceEmbeddings` with `sentence-transformers/all-MiniLM-L6-v2` is used to generate embeddings for the document chunks.
    * `PineconeVectorStore` is used to store the embeddings in the Pinecone index.
* **Question Answering:**
    * `retrieve_query` function is used to retrieve relevant document chunks from Pinecone based on a user's query.
    * `HuggingFacePipeline` with `bigscience/T0_3B` is used as the language model to generate answers.
    * `load_qa_chain` from LangChain is used to create a question-answering chain.

## Limitations

* **Model Performance:** The performance of the question-answering system depends on the quality of the documents and the capabilities of the chosen language model (`bigscience/T0_3B`).
* **Colab Dependence:** The code is primarily designed to run in a Google Colab environment.
* **API Key Security:** Proper API key management is crucial. Never hardcode API keys directly into your code.
* **Chunking Strategy:** The current chunking strategy might not be optimal for all document types.
* **LLM size:** The LLM that is used is relatively small.
* **Cost:** Using Pinecone and LLM APIs can incur costs.

## Potential Improvements

* Implement a user interface using Streamlit or Gradio.
* Add error handling for API calls and document loading.
* Experiment with different embedding models and language models.
* Implement more advanced retrieval strategies.
* Add metadata filtering to the vector database retrieval.
* Improve the chunking strategy.

## Contributing

Contributions are welcome! Please feel free to submit pull requests.

## License


```
