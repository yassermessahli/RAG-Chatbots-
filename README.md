# Car Manual Context-Aware Chatbot (RAG)

A Standard project for Retrieval-Augmented Generation (RAG) system that answers car maintenance related questions, using an `MG ZS SUV` manual. Built with LangChain and OpenAI.

## RAG (Retrieval-Augmented Generation)

Recent technic that combines **Retrieval** to Fetch relevant info from documents, and **Generation** by leveraging LLMs to craft natural responses. It enables factual, context-aware answers grounded in source material.

## LangChain

A recent python framework to build context aware chat LLM applications. It is useful to build reasoning pipeline for better context relevant answers from the LLM step-by-step. including:
1. Document loading (ex. `UnstructuredHTMLLoader`)
2. Text splitting (ex. `HTMLTableRowSplitter`)
3. Vector storage (ex. `Chroma`)
4. Pipeline orchestration (ex. `RunnablePassthrough` chain)

## Project Goal

Create a chat assistant that interprets car warning lights by:
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

## Quick Start

1. Set OpenAI key in environment variables with name: `OPENAI_API_KEY`
2. Install dependencies: 
```sh
pip install -r requirements.txt
```
3. Place manual in `data/` directory
4. Run `notebook.ipynb`
