# Car Manual Context-Aware Chatbot (RAG)

A Retrieval-Augmented Generation (RAG) system that answers car maintenance questions using an MG ZS SUV manual. Built with LangChain and OpenAI.

## RAG (Retrieval-Augmented Generation)

Combines:

- **Retrieval**: Fetch relevant info from documents
- **Generation**: Use LLMs to craft natural responses  
Enables factual, context-aware answers grounded in source material.

## LangChain

Framework for LLM applications. Used here for:

- Document loading (`UnstructuredHTMLLoader`)
- Text splitting (`HTMLTableRowSplitter`)
- Vector storage (`Chroma`)
- Pipeline orchestration (`RunnablePassthrough` chain)

## Project Goal

Create a voice-ready assistant that interprets car warning lights by:

1. Extracting manual content
2. Enabling natural language queries
3. Providing actionable repair guidance

## Project Approach

1. **Data Processing:** Custom HTML loader parses warning/procedure tables, and Row-based text splitting preserves context

2. **Vector Database:** `Chroma` storage with OpenAI embeddings and Similarity search for relevant warnings

3. **RAG Pipeline:**

```sh
input -> retriever -> prompt -> llm -> parser -> output
```

4. **Response Generation:** `gpt-4o-mini` model with temperature=0 with Strict context grounding with fallback

## Usage Example

```python
query = "Gasoline Particular Filter Full warning appeared?"
response = chain.invoke(query)
```

**Output:**  
"Consult an MG Authorised Repairer as soon as possible."

## Requirements

- Python 3.10
- OpenAI API key
- Packages:  
  `langchain-core`, `langchain-openai`, `chromadb`, `beautifulsoup4`

## Quick Start

1. Set OpenAI key in environment variables with name: `OPENAI_API_KEY`
2. Install dependencies: 
```sh
pip install -r requirements.txt
```
3. Place manual in `data/` directory
4. Run `notebook.ipynb`
