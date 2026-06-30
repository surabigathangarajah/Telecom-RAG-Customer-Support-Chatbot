# Telecom RAG Customer Support Chatbot

## Overview

The Telecom RAG Customer Support Chatbot is an intelligent AI-powered assistant that answers telecom-related customer queries using Retrieval-Augmented Generation (RAG). Instead of relying solely on a language model, the chatbot retrieves relevant information from multiple knowledge sources before generating accurate, context-aware responses.

The project demonstrates a complete end-to-end RAG pipeline using LangChain, ChromaDB, Sentence Transformers, ChatGroq, and Streamlit.

---

## Features

* Retrieval-Augmented Generation (RAG) architecture
* Multi-source knowledge retrieval
* Conversational AI with context-aware responses
* Semantic search using vector embeddings
* Interactive Streamlit web interface
* Local vector database with ChromaDB
* Historical ticket retrieval for real-world issue resolution
* Conversation memory for improved user experience

---

## Data Sources

The chatbot retrieves information from three independent knowledge sources:

* **Technical PDF Guides**

  * Product documentation
  * Network troubleshooting guides
  * Service manuals

* **FAQ Dataset (CSV)**

  * Frequently asked customer questions
  * General policies and service information

* **Customer Support Tickets (SQLite)**

  * Historical customer issues
  * Problem descriptions
  * Resolved solutions and troubleshooting steps

---

## Project Architecture

```text
User Question
      │
      ▼
 Streamlit Interface
      │
      ▼
 LangChain RAG Pipeline
      │
      ├───────────────┐
      │               │
      ▼               ▼
 Chroma Retriever   Conversation Memory
      │
      ▼
Relevant Documents
(PDF + FAQ + Tickets)
      │
      ▼
Prompt Construction
      │
      ▼
ChatGroq (LLM)
      │
      ▼
Generated Response
```

---

## Technologies Used

* Python
* LangChain
* ChatGroq
* ChromaDB
* Sentence Transformers (all-MiniLM-L6-v2)
* SQLite
* Streamlit
* Pandas
* PyPDF

---

## Project Structure

```text
Telecom_chatbot/
│
├── app.py
├── ragchain.py
├── retriever.py
├── ingest_faq.py
├── ingest_guides.py
├── ingest_tickets.py
├── data/
│   ├── faq.csv
│   ├── telecom.db
│   └── guides/
├── chroma_store/
├── requirements.txt
├── .env
└── README.md
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/your-username/telecom-rag-chatbot.git
cd telecom-rag-chatbot
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate the environment:

Windows

```bash
.venv\Scripts\activate
```

Linux / macOS

```bash
source .venv/bin/activate
```

Install the required packages:

```bash
pip install -r requirements.txt
```

---

## Environment Variables

Create a `.env` file in the project root.

```env
GROQ_API_KEY=your_groq_api_key
```

---

## Data Ingestion

Generate vector embeddings for each data source.

FAQ

```bash
python ingest_faq.py
```

Support Tickets

```bash
python ingest_tickets.py
```

Technical Guides

```bash
python ingest_guides.py
```

This creates the local Chroma vector database used during retrieval.

---

## Running the Application

Start the Streamlit application:

```bash
streamlit run app.py
```

The application will open automatically in your web browser.

---

## How It Works

1. The user submits a telecom-related question.
2. The retriever searches across FAQ documents, technical guides, and historical support tickets.
3. The most relevant documents are retrieved from ChromaDB.
4. The retrieved context and user query are passed to the language model.
5. The language model generates a context-aware response grounded in the retrieved information.
6. Conversation history is maintained to support follow-up questions.

---

## Example Questions

* Why is my mobile data not working?
* How can I reset my network settings?
* My SIM card is not detected.
* Why is my internet speed slow?
* How do I activate international roaming?
* How can I troubleshoot poor signal strength?
* My calls keep dropping. What should I do?

---

## Future Improvements

* Voice-based customer support
* Image-based troubleshooting
* Hybrid keyword and semantic search
* Authentication and user profiles
* Live telecom API integration
* Deployment using Docker and cloud platforms
* Feedback collection for continuous improvement

---

## License

This project is intended for educational and learning purposes.
