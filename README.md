# Semantic Search Engine with Langchain and Qdrant

## Project Overview

This project leverages **Langchain** and **Qdrant** to create a powerful semantic search engine. The system enables users to query a vectorized database of documents and retrieve the most relevant results based on semantic similarity, providing more contextually accurate results compared to traditional keyword-based searches.

## Prerequisites

- **Docker** installed on your system
- **Python** (version 3.8 or higher)

## Setup Instructions

1. **Install Docker**:  
   [Download and install Docker](https://www.docker.com/get-started) on your system.

2. **Pull the Qdrant Image**:  
   Run the following command to pull the Qdrant Docker image:
   ```bash
   docker pull qdrant/qdrant
   ```

3. **Run the Qdrant Container**:  
   Start the Qdrant container by running:
   ```bash
   docker run -p 6333:6333 qdrant/storage qdrant/qdrant
   ```

4. **Clone the Repository**:  
   Clone this project’s repository:
   ```bash
   git clone <repository_url>
   ```

5. **Install Project Dependencies**:  
   Navigate to the project directory and install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. **Prepare Documents**:  
   Place your PDF documents in the `data` directory.

2. **Index Documents**:  
   Run the following command to index the documents:
   ```bash
   python ingest.py
   ```
   This will create a Qdrant collection named `vector_db`, which stores the document embeddings for semantic search.

3. **Run the Search Engine**:  
   Use **Streamlit** to launch the web interface for the search engine:
   ```bash
   streamlit run app.py
   ```

4. **Query the Database**:  
   Input a query in the web interface, and the system will retrieve the top 5 most semantically similar documents.

## Project Components

- **ingest.py**:  
  This script processes and indexes your PDF documents. It uses **PyPDFLoader** and **RecursiveCharacterTextSplitter** from Langchain to split the documents into manageable chunks. These text chunks are embedded using the Hugging Face model `BAAI/bge-large-en` and stored in the Qdrant collection.

- **app.py**:  
  This script provides a user interface for querying the database using **Streamlit**. It takes user input, embeds the query using the same model, and performs a similarity search on the stored embeddings in Qdrant.

## Key Libraries

- **Langchain**: For document processing and embedding text
- **Qdrant**: For vector database management
- **Hugging Face Transformers**: For pre-trained language models
- **Streamlit**: For building the web interface
- **PyPDFLoader**: For loading and processing PDF documents

## Troubleshooting

- Ensure Docker is running, and the Qdrant container is started before running `ingest.py` or `app.py`.
- Verify that the collection name (`vector_db`) and URL (http://localhost:6333) in both scripts match.
- Adjust the `chunk_size` and `chunk_overlap` in `ingest.py` for optimal indexing performance.

## Contributing

Contributions are welcome! If you have suggestions or improvements, feel free to submit a pull request.
```

You can copy this directly into your `README.md` file in GitHub's editor. Let me know if you need any further modifications!
