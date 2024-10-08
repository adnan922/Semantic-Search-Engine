README
Project Overview
This project utilizes Langchain and Qdrant to build a semantic search engine. It allows users to query a database of documents and retrieve relevant results based on semantic similarity.
Prerequisites

    Docker installed on your system
    Python 3.8 or higher

Setup

    Install Docker: Download and install Docker from 

.
Pull Qdrant Image: Run the following command to pull the Qdrant image:

docker pull qdrant/qdrant

3. **Run Qdrant Container**: Run the Qdrant container on port 6333:

docker run -p 6333:6333 qdrant/qdrant

4. **Clone this repository**: Clone this project using Git:

git clone 

5. **Install dependencies**: Navigate to the project directory and install dependencies:

pip install -r requirements.txt


**Usage**

1. **Prepare documents**: Place your PDF documents in the `data` directory.
2. **Index documents**: Run `ingrst.py` to index the documents:
   ```bash
python ingrst.py

This will create a Qdrant collection named "vector_db".

    Run the search engine: Run app.py using Streamlit:
    Bash

streamlit run app.py

   This will start a web interface where you can input queries.
4. **Query the database**: Enter a query in the text box and press Enter. The top 5 most similar documents will be displayed.

**Explanation**

This project consists of two main scripts:

1. **ingrst.py**: This script indexes the PDF documents using Langchain's `PyPDFLoader` and `RecursiveCharacterTextSplitter`. It then embeds the text chunks using Hugging Face's `BAAI/bge-large-en` model and stores them in a Qdrant collection.
2. **app.py**: This script uses Streamlit to create a web interface for querying the Qdrant collection. It takes user input, embeds the query using the same model, and performs a similarity search on the Qdrant collection.

**Dependencies**

This project relies on the following libraries:

* Langchain: For text processing and embedding
* Qdrant: For vector database management
* Hugging Face Transformers: For embedding models
* Streamlit: For web interface
* PyPDF2: For PDF document loading

**Troubleshooting**

* Ensure Docker is running and Qdrant container is started before running `ingrst.py` or `app.py`.
* Check the Qdrant collection name and URL in `ingrst.py` and `app.py` match the actual collection name and URL.
* Adjust the `chunk_size` and `chunk_overlap` parameters in `ingrst.py` to optimize indexing performance.

**Contributing**

Contributions are welcome! Please submit a pull request with your changes.
