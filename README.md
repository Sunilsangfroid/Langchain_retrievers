# LangChain Retrievers 

This repository contains examples of various retrievers in LangChain for efficient document retrieval. Retrievers are components that fetch relevant documents from a data source based on a user's query.

## Overview

A retriever bridges the gap between your data source and your application, allowing you to fetch contextually relevant documents. All retrievers in LangChain are "runnables," meaning they can be easily incorporated into LangChain pipelines.

## Installation

To set up the environment:

```bash
pip install langchain chromadb faiss-cpu langchain_google_genai openai tiktoken langchain_openai langchain-community wikipedia
```

## Retriever Types

This repository demonstrates several types of retrievers available in LangChain:

### Vector Store Retrievers
- Use embeddings to find semantically similar documents
- Examples include Chroma, FAISS, and Pinecone retrievers

### Contextual Compression Retrievers
- Filter or rerank documents to improve relevance 
- Reduce token usage by focusing on the most relevant content

### Parent Document Retrievers
- Retrieve smaller chunks while maintaining context of the parent document
- Useful for handling large documents that need to be split

### Self-Query Retrievers
- Allow the LLM to generate structured queries from natural language
- Support filtering based on metadata

### Ensemble Retrievers
- Combine multiple retrievers for better performance
- Can use different strategies (reciprocal rank fusion, weighing, etc.)

## Usage Examples

Basic retriever usage:

```python
from langchain.retrievers import ChromaRetriever
from langchain.vectorstores import Chroma
from langchain_openai import OpenAIEmbeddings

# Create vector store
embeddings = OpenAIEmbeddings()
vectorstore = Chroma.from_documents(documents, embeddings)

# Create retriever
retriever = vectorstore.as_retriever()

# Retrieve relevant documents
docs = retriever.get_relevant_documents("What is LangChain?")
```

## Project Structure

```
.
├── examples/                # Example notebooks demonstrating retriever usage
│   ├── vector_store.ipynb
│   ├── contextual.ipynb
│   └── ...
├── data/                    # Sample datasets for testing retrievers
└── utils/                   # Utility functions for data loading and processing
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.