# RAG Pipeline Using Groq and ChromaDB

A PDF-based Retrieval-Augmented Generation (RAG) pipeline that retrieves relevant information from research documents and generates context-grounded answers using a Groq-hosted LLM.

## Project Overview

This project implements a complete Retrieval-Augmented Generation pipeline for question answering over PDF documents.

The pipeline includes:

- PDF document loading
- Text chunking
- Sentence Transformer embeddings
- ChromaDB vector storage
- Semantic similarity retrieval
- Similarity-score filtering
- Groq LLM-based answer generation
- Multi-query testing
- CSV-based result evaluation

## RAG Pipeline

```text
PDF Documents
      ↓
Document Loading
      ↓
Text Chunking
      ↓
Text Embedding
      ↓
ChromaDB Vector Store
      ↓
User Query
      ↓
Query Embedding
      ↓
Semantic Retrieval
      ↓
Similarity Score Filtering
      ↓
Retrieved Context
      ↓
Groq LLM
      ↓
Final Answer
```

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Programming language |
| Jupyter Notebook | Development and experimentation |
| LangChain | LLM integration |
| Sentence Transformers | Text embeddings |
| ChromaDB | Local vector storage |
| Groq | LLM inference |
| Pandas | Data processing and CSV generation |
| Google Colab | Development environment |

## Embedding Model

The project uses a Sentence Transformer embedding model that produces 384-dimensional embeddings.

```text
Text Chunk
    ↓
Embedding Model
    ↓
384-dimensional Vector
```

These embeddings are stored in ChromaDB for semantic similarity search.

## Vector Store

ChromaDB is used as the local persistent vector store.

The vector store contains:

- Document IDs
- Document chunks
- Embeddings
- Metadata
- Similarity-search information

The generated vector store is intentionally excluded from this repository because it can be recreated from the source documents.

## LLM

The generation stage uses a Groq-hosted LLM.

The API key is loaded from an environment variable and is not included in this repository.

Create a local `.env` file:

```env
GROQ_API_KEY=your_groq_api_key_here
```

Never commit the actual API key.

## Source Documents

The original PDF files are not included in this repository.

The research papers used for the project were obtained from their original/public sources. Source links should be provided separately in:

```text
sources/Sources.md
```

To reproduce the project, download the source documents and place them in the required PDF directory described in the notebook.

## Retrieval

For each user query, the system:

1. Converts the query into an embedding.
2. Performs semantic similarity search against ChromaDB.
3. Retrieves the top-k relevant document chunks.
4. Calculates similarity scores.
5. Applies the similarity threshold.
6. Builds the retrieved context.
7. Sends the context and query to the Groq LLM.
8. Generates the final response.

## Query Evaluation

The project was tested with multiple queries covering:

- RAG
- Encoder-Decoder
- NLP
- Python
- Open-domain question answering
- Knowledge Retriever
- DPR
- RAG researchers
- RAG paradigms
- True/False questions
- Questions outside the indexed knowledge

The results are stored in:

```text
RAG_Query_Results.csv
```

The CSV contains:

| Column | Description |
|---|---|
| Query No. | Query identifier |
| Query | User question |
| Count of Retrieval Documents | Number of retrieved chunks |
| Similarity Score | Highest retrieved similarity score |
| Output | Generated response |

## Project Structure

```text
RAG-Pipeline-Using-Groq-and-ChromaDB/
│
├── RAG_Pipeline_Groq_ChromaDB.ipynb
├── RAG_Query_Results.csv
├── requirements.txt
├── README.md
├── .gitignore
│
└── sources/
    └── Sources.md
```

## Installation

Install dependencies:

```bash
pip install -r requirements.txt
```

## Environment Variables

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key
```

The `.env` file is excluded using `.gitignore`.

## Running the Project

Open:

```text
RAG_Pipeline_Groq_ChromaDB.ipynb
```

Run the notebook cells sequentially.

The notebook performs document loading, chunking, embedding generation, vector-store creation, semantic retrieval, and LLM-based response generation.

## Limitations

- Retrieval quality depends on the embedding model.
- Poor chunking can reduce retrieval accuracy.
- Semantic similarity does not guarantee that a retrieved chunk directly answers the query.
- Text-only PDF processing may not retrieve information contained only inside images.
- Questions whose answers are absent from the indexed documents may not be answered correctly.
- Final answer quality depends on both retrieval and LLM generation.

## Future Improvements

- Hybrid search
- Re-ranking
- Improved chunking strategies
- Query expansion
- Metadata filtering
- Multi-query retrieval
- RAG evaluation metrics
- Multimodal/image retrieval
- Conversation memory
- Web-based RAG
- RAGAS-based evaluation

## Author

**Rounak Dey**
