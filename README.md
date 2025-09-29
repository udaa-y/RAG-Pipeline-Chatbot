# RAG-Pipeline-Chatbot
The RAG Pipeline Chatbot is an n8n workflow that builds a retrieval-augmented FAQ assistant. It watches Google Drive for new files, processes them into embeddings with Google Gemini, stores them in Pinecone, and powers a chatbot agent with memory for accurate, context-aware answers.

#  RAG Pipeline Chatbot (n8n Workflow)

This repository contains an **n8n workflow** that implements a **Retrieval-Augmented Generation (RAG) chatbot** using:
- **Google Drive** (document source)
- **Pinecone** (vector database)
- **Google Gemini API** (embeddings + chat model)
- **n8n LangChain nodes** (agent, memory, embeddings, text splitter)

---

##  Features
-  **Auto-ingestion**: Watches a Google Drive folder for new FAQ/policy documents.
-  **Document processing**: Downloads and splits text into chunks.
-  **Vector storage**: Creates embeddings with Google Gemini and stores them in Pinecone.
-  **Conversational AI Agent**: Uses Pinecone as a knowledge tool to answer user queries.
-  **Chat integration**: Chat trigger allows end-users to interact with the FAQ bot.
-  **Contextual memory**: Keeps track of prior exchanges for coherent multi-turn conversations.

---

##  Workflow Overview
1. **Google Drive Trigger** → Detects new file upload in a specified folder.
2. **Download File** → Fetches the document.
3. **Text Splitter** → Breaks content into chunks for embedding.
4. **Gemini Embeddings** → Creates vector embeddings.
5. **Pinecone Vector Store** → Saves vectors in a namespace (`FAQ`).
6. **Knowledge Base Tool** → Agent retrieves answers from Pinecone.
7. **Google Gemini Chat Model** → Generates natural language answers.
8. **Memory Module** → Maintains conversation history.
9. **AI Agent** → Combines everything into a Q&A chatbot.

---

##  Requirements
- **n8n** (v1.0+)
- **Google Drive API credentials**
- **Google Gemini (PaLM/Gemini) API key**
- **Pinecone API key**

---

## Usage
1. Import `RAG Pipeline Chatbot.json` into your **n8n instance**.
2. Set up credentials:
   - Google Drive OAuth2
   - Google Gemini (PaLM/Gemini) API
   - Pinecone API
3. Update workflow nodes with your:
   - Google Drive folder ID
   - Pinecone index + namespace
4. Activate workflow.
5. Upload a new FAQ/policy document to Google Drive → workflow auto-processes it.
6. Send a chat message to the bot → get instant FAQ answers.

---
