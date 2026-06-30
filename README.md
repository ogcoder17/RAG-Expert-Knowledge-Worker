# Finovia — Expert Knowledge Worker (RAG) 🏦

> A Retrieval-Augmented Generation (RAG) chatbot that answers questions about **Finovia Bank** (entirely fictional) by retrieving relevant info from a knowledge base and feeding it to an LLM — so answers stay grounded in real documents instead of being made up.

Built with **Python · LangChain · OpenAI · ChromaDB · Gradio**.

---

## ✨ Overview

Finovia loads a folder of company documents, splits them into chunks, embeds each chunk into a vector database, and retrieves the most relevant pieces at query time to answer questions with context. It keeps chat history for natural follow-ups and runs in a simple Gradio chat UI.

---

## 🔧 How It Works

1. **Load** — reads markdown files from `knowledge-base-bank/`, tagging each with a `doc_type` (company, services, employees, contracts) as metadata.
2. **Chunk** — splits documents into 1000-character chunks with 200-character overlap to preserve context across boundaries.
3. **Embed & store** — converts chunks into vectors with OpenAI embeddings and stores them in **ChromaDB** (persisted to disk).
4. **Retrieve** — fetches the top **k = 4** most similar chunks to the user's question.
5. **Generate** — passes the retrieved context + chat history into a prompt and calls **gpt-4o-mini** for a grounded answer.
6. **Chat UI** — wraps the chain in a **Gradio** chat interface with conversational memory.

It also visualizes the embedding space in 2D/3D using **t-SNE** + Plotly, colored by document type — showing how related content clusters together.

---

## 🛠️ Tech Stack

**Python · LangChain (LCEL) · OpenAI (embeddings + gpt-4o-mini) · ChromaDB · Gradio · scikit-learn (t-SNE) · Plotly**



