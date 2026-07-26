# 🤖 FAQ Bot – AI PDF Question Answering System (RAG)

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge\&logo=python\&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-App-FF4B4B?style=for-the-badge\&logo=streamlit\&logoColor=white)
![Google Gemini](https://img.shields.io/badge/Google-Gemini-4285F4?style=for-the-badge\&logo=google\&logoColor=white)
![ChromaDB](https://img.shields.io/badge/ChromaDB-VectorDB-00C853?style=for-the-badge)
![RAG](https://img.shields.io/badge/RAG-Retrieval--Augmented--Generation-orange?style=for-the-badge)

### 📄 Upload a PDF • 💬 Ask Questions • 🤖 Get Accurate AI Answers

A Retrieval-Augmented Generation (RAG) application built using **Streamlit**, **Google Gemini**, **ChromaDB**, and **PyPDF2**.

</div>

---

# 📖 Overview

FAQ Bot is an AI-powered Question Answering application that allows users to upload a PDF document and ask questions about its content.

Instead of relying solely on the language model's knowledge, the application uses **Retrieval-Augmented Generation (RAG)**. It retrieves the most relevant sections from the uploaded document and provides them as context to Google Gemini before generating a response.

This approach produces more relevant answers while reducing hallucinations.

---

# ✨ Features

* 📄 Upload PDF documents
* 📚 Automatic PDF text extraction
* ✂️ Smart text chunking with overlap
* 🔍 Semantic search using embeddings
* 🧠 Google Gemini Embedding API
* 💾 ChromaDB vector database
* 🤖 Google Gemini 3.1 Flash Lite for answer generation
* 💬 Conversational chat interface
* 📄 Displays document source chunks used
* 📊 Tracks input/output token usage
* 🔄 Reset token statistics
* ⚡ Fast document indexing
* 🎯 Retrieval-Augmented Generation (RAG)
* 🚫 Prevents hallucinations by answering only from the uploaded document

---

# 🛡️ Answer Policy

This application is **not a general-purpose chatbot**.

It answers questions **only using information available in the uploaded PDF**.

If the requested information is **not present** in the document, the assistant replies:

> **"I couldn't find that in the document."**

This ensures:

* ✅ Reduced AI hallucinations
* ✅ More reliable answers
* ✅ Document-grounded responses
* ✅ Better transparency for users

---

# 🏗️ Tech Stack

| Technology           | Purpose               |
| -------------------- | --------------------- |
| Python               | Programming Language  |
| Streamlit            | User Interface        |
| Google Gemini API    | LLM                   |
| Gemini Embedding API | Embeddings            |
| ChromaDB             | Vector Database       |
| PyPDF2               | PDF Text Extraction   |
| python-dotenv        | Environment Variables |

---

# 🧠 RAG Architecture

```text
                +----------------------+
                |     Upload PDF       |
                +----------+-----------+
                           |
                           v
                +----------------------+
                |  Extract PDF Text    |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Split into Chunks    |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Create Embeddings    |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Store in ChromaDB    |
                +----------+-----------+
                           |
                           |
                     User Question
                           |
                           v
                +----------------------+
                | Query Embedding      |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Similarity Search    |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Relevant Chunks      |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Google Gemini (RAG)  |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Final Answer         |
                +----------------------+
```

---

# 🚀 How It Works

### Step 1

Upload a PDF document.

⬇️

### Step 2

The application extracts all text using **PyPDF2**.

⬇️

### Step 3

The text is divided into overlapping chunks.

⬇️

### Step 4

Each chunk is converted into vector embeddings.

⬇️

### Step 5

The embeddings are stored inside **ChromaDB**.

⬇️

### Step 6

The user asks a question.

⬇️

### Step 7

The question is converted into an embedding.

⬇️

### Step 8

ChromaDB retrieves the **Top 3** most relevant chunks.

⬇️

### Step 9

Only those retrieved chunks are sent to Google Gemini.

⬇️

### Step 10

Gemini generates the answer based only on the retrieved document context.

⬇️

### Step 11

If the answer does not exist in the uploaded PDF, the bot replies:

> **"I couldn't find that in the document."**

---

# 📸 Screenshots

## 🏠 Home Screen

```
images/home.png
```

<img src="images/home.png" width="900">

---

## 📄 Upload PDF

```
images/upload.png
```

<img src="images/upload.png" width="900">

---

## 💬 Chat Interface

```
images/chat.png
```

<img src="images/chat.png" width="900">

---

## 📄 Source Chunks

```
images/source.png
```

<img src="images/source.png" width="900">

---

## 📊 Token Statistics

```
images/token_stats.png
```

<img src="images/token_stats.png" width="450">

---

# 📂 Project Structure

```text
FAQ-Bot/
│
├── app.py
├── requirements.txt
├── README.md
├── .env
│
├── images/
│   ├── home.png
│   ├── upload.png
│   ├── chat.png
│   ├── source.png
│   └── token_stats.png
│
└── .venv/
```

---

# ⚙️ Installation

## 1. Clone Repository

```bash
git clone https://github.com/your-username/FAQ-Bot.git

cd FAQ-Bot
```

---

## 2. Create Virtual Environment

```bash
python -m venv .venv
```

---

## 3. Activate Virtual Environment

### Windows

```bash
.venv\Scripts\activate
```

### Linux / macOS

```bash
source .venv/bin/activate
```

---

## 4. Install Dependencies

```bash
pip install -r requirements.txt
```

or

```bash
pip install streamlit google-genai chromadb PyPDF2 python-dotenv
```

---

# 🔑 Environment Variables

Create a `.env` file in the project root.

```env
GEMINI_API_KEY=YOUR_GEMINI_API_KEY
```

---

# ▶️ Run the Application

```bash
streamlit run app.py
```

The application will automatically open in your browser.

---

# 💡 Example Usage

### Uploaded Document

```
Python Programming Notes.pdf
```

---

### Question

```text
What is a variable?
```

### Answer

```text
A variable is a named memory location used to store data.
```

---

### Question

```text
Explain Machine Learning.
```

### Answer

```text
I couldn't find that in the document.
```

Because the uploaded PDF does not contain information about Machine Learning.

---

# 📊 Token Tracking

The application automatically tracks:

* Total Input Tokens
* Total Output Tokens
* Overall Token Usage

Users can reset the statistics at any time using the **Reset Stats** button.

---

# 🎯 Future Improvements

* Support multiple PDFs
* Persistent ChromaDB storage
* Streaming AI responses
* Voice input
* Chat history download
* Highlight answer inside PDF
* Page number citations
* Dark mode
* User authentication
* Conversation export
* PDF summarization
* Search across multiple documents

---

# 🤝 Contributing

Contributions are welcome!

1. Fork the repository
2. Create a new feature branch
3. Commit your changes
4. Push the branch
5. Open a Pull Request

---

# 👨‍💻 Author

**Sanket More**

---