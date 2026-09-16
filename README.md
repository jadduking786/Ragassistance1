# 📚 PDF RAG Assistant

A Retrieval-Augmented Generation (RAG) application that allows users to upload a PDF document and ask questions about its content.

The application extracts text from the PDF, divides it into chunks, converts the chunks into vector embeddings using an open-source Sentence Transformer model, stores the embeddings in a FAISS vector database, retrieves the most relevant information, and uses Groq's `openai/gpt-oss-20b` model to generate answers.

The frontend is built with **Streamlit**, making the application simple and easy to use.

---

## 🚀 Features

* 📄 Upload PDF documents
* 🔍 Extract text from PDF files
* ✂️ Split documents into overlapping chunks
* 🧠 Generate embeddings using an open-source Sentence Transformer
* 🗄️ Store embeddings in FAISS vector database
* 🔎 Perform semantic similarity search
* 🤖 Generate answers using Groq
* 📚 Display retrieved document sources
* 📄 Show relevant page numbers
* 💬 Chat-style interface
* 🔐 Secure API key management using Streamlit Secrets
* ☁️ Deployable on Streamlit Community Cloud

---

## 🏗️ Application Architecture

```text
                ┌─────────────────┐
                │   User Uploads  │
                │      PDF        │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │   PDF Text      │
                │   Extraction    │
                │     PyPDF       │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │ Text Chunking   │
                │                 │
                │ Chunk + Overlap │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │   Embeddings    │
                │ Sentence        │
                │ Transformers    │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │  FAISS Vector   │
                │    Database     │
                └────────┬────────┘
                         │
                         │
             User Question
                         │
                         ▼
                ┌─────────────────┐
                │ Question        │
                │ Embedding       │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │ FAISS Similarity│
                │     Search      │
                └────────┬────────┘
                         │
                  Relevant Chunks
                         │
                         ▼
                ┌─────────────────┐
                │      Groq       │
                │  GPT-OSS-20B    │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │    Final Answer │
                └─────────────────┘
```

---

## 🧠 How RAG Works

RAG stands for **Retrieval-Augmented Generation**.

Instead of asking the language model to answer a question using only its general knowledge, the application first retrieves relevant information from the user's uploaded document.

The retrieved information is then provided to the language model as context.

### RAG Pipeline

```text
PDF
 ↓
Text Extraction
 ↓
Chunking
 ↓
Embedding
 ↓
FAISS
 ↓
Retrieval
 ↓
Context
 ↓
Groq LLM
 ↓
Answer
```

This helps the application answer questions based on the uploaded document.

---

## 🛠️ Technologies Used

| Technology | Purpose                   |
| ---------- | ------------------------- |
| Python     | Main programming language |
